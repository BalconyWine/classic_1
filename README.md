import { execution } from '@dynatrace/synthetic';

// --- CONFIGURATION ---
// Replace this with your actual Bearer Token from your original script
// (The long string starting with "eyJh...")
const API_TOKEN = "YOUR_IBM_CLOUD_IAM_TOKEN"; 

// Your endpoint from the screenshot
const ENDPOINT = "https://s3.direct.eu-fr2.cloud-object-storage.appdomain.cloud";

export default async function () {
    console.log("Starting IBM COS Audit...");

    // 1. Setup the Headers (Using the Bearer Token method you used originally)
    const headers = {
        "Authorization": `Bearer ${API_TOKEN}`,
        "Accept": "application/json"
    };

    // 2. List Buckets (Equivalent to your get_cos_buckets)
    // Note: Standard S3 API usually requires HMAC, but your script used a REST API.
    // We will try the standard S3 XML listing which works with most tokens, 
    // OR the specific URL you used if you are inside the BNP network.
    
    // ATTEMPT 1: Standard S3 Listing
    const response = await api.http.get(`${ENDPOINT}/`, { headers: headers });

    if (response.statusCode !== 200) {
        console.error(`Failed to connect. Status: ${response.statusCode}`);
        if (response.statusCode === 403) {
            console.error("Access Denied. Your Token might be expired or invalid.");
        }
        return;
    }

    // Parse XML Response to find buckets (Dynatrace handles XML parsing automatically often, or we do regex)
    const body = response.body;
    console.log("Connected to IBM COS!");
    
    // Simple Regex to count buckets (faster than full XML parsing)
    // Matches <Name>bucketname</Name>
    const bucketMatches = body.match(/<Name>(.*?)<\/Name>/g);
    
    if (!bucketMatches) {
        console.log("No buckets found or empty account.");
        return;
    }

    console.log(`Found ${bucketMatches.length} buckets.`);

    // 3. Check the First 3 Buckets (To avoid Dynatrace 60s Timeout)
    // We cannot check ALL buckets in one run because it will take too long.
    const limit = Math.min(bucketMatches.length, 3);
    
    for (let i = 0; i < limit; i++) {
        // Extract name from tags <Name>my-bucket</Name>
        const bucketName = bucketMatches[i].replace(/<\/?Name>/g, '');
        console.log(`Analyzing bucket: ${bucketName}...`);

        // Get Objects for this bucket
        const bucketResponse = await api.http.get(`${ENDPOINT}/${bucketName}?max-keys=1000`, { headers: headers });
        
        if (bucketResponse.statusCode === 200) {
            const bucketBody = bucketResponse.body;
            
            // Extract Sizes using Regex <Size>1234</Size>
            const sizeMatches = bucketBody.match(/<Size>(\d+)<\/Size>/g);
            let totalSize = 0;
            let objectCount = 0;

            if (sizeMatches) {
                objectCount = sizeMatches.length;
                sizeMatches.forEach(tag => {
                    const sizeBytes = parseInt(tag.replace(/<\/?Size>/g, ''));
                    totalSize += sizeBytes;
                });
            }

            // Convert to Megabytes
            const sizeMB = (totalSize / (1024 * 1024)).toFixed(2);
            console.log(` -> Size: ${sizeMB} MB`);
            console.log(` -> Objects: ${objectCount}`);
        } else {
            console.log(` -> Could not read bucket (Status ${bucketResponse.statusCode})`);
        }
    }
    
    console.log("*** Audit Complete ***");
}

