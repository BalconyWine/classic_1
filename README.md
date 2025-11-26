{
  "version": "1.0",
  "type": "clickpath",
  "configuration": {
    "device": {
      "deviceName": "Desktop",
      "orientation": "landscape"
    }
  },
  "events": [
    {
      "type": "navigate",
      "description": "Open IBM COS Endpoint",
      "url": "https://s3.direct.eu-fr2.cloud-object-storage.appdomain.cloud/"
    },
    {
      "type": "javaScript",
      "description": "Calculate Bucket Sizes",
      "code": "// CONFIGURATION\nvar API_TOKEN = 'YOUR_IBM_TOKEN_HERE';\nvar ENDPOINT = 'https://s3.direct.eu-fr2.cloud-object-storage.appdomain.cloud';\n\n// 1. Setup Request\nvar xhr = new XMLHttpRequest();\nxhr.open('GET', ENDPOINT, false); // Synchronous for simplicity in synthetic\nxhr.setRequestHeader('Authorization', 'Bearer ' + API_TOKEN);\nxhr.setRequestHeader('Accept', 'application/json');\nxhr.send(null);\n\nif (xhr.status === 200) {\n    api.info('Connected to IBM COS successfully');\n    var responseBody = xhr.responseText;\n    \n    // 2. Parse Buckets (Regex)\n    var bucketMatches = responseBody.match(/<Name>(.*?)<\\/Name>/g);\n    \n    if (bucketMatches) {\n        api.info('Found ' + bucketMatches.length + ' buckets');\n        \n        // Check first 3 buckets to avoid timeout\n        var limit = Math.min(bucketMatches.length, 3);\n        for (var i = 0; i < limit; i++) {\n            var bucketName = bucketMatches[i].replace(/<\\/?Name>/g, '');\n            \n            // Fetch Bucket Objects\n            var bucketXhr = new XMLHttpRequest();\n            bucketXhr.open('GET', ENDPOINT + '/' + bucketName + '?max-keys=1000', false);\n            bucketXhr.setRequestHeader('Authorization', 'Bearer ' + API_TOKEN);\n            bucketXhr.send(null);\n            \n            if (bucketXhr.status === 200) {\n                var sizeMatches = bucketXhr.responseText.match(/<Size>(\\d+)<\\/Size>/g);\n                var totalSize = 0;\n                if (sizeMatches) {\n                    for (var j=0; j<sizeMatches.length; j++) {\n                        totalSize += parseInt(sizeMatches[j].replace(/<\\/?Size>/g, ''));\n                    }\n                }\n                var sizeMB = (totalSize / (1024 * 1024)).toFixed(2);\n                api.info('Bucket: ' + bucketName + ' | Size: ' + sizeMB + ' MB');\n            }\n        }\n    }\n} else {\n    api.fail('Failed to connect to IBM COS. Status: ' + xhr.status);\n}"
    }
  ]
}
