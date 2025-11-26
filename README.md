{
  "frequencyMin": 5,
  "requests": [
    {
      "description": "Check IBM COS Availability",
      "url": "https://s3.direct.eu-fr2.cloud-object-storage.appdomain.cloud/",
      "method": "GET",
      "headers": [
        {
          "name": "Authorization",
          "value": "Bearer PASTE_YOUR_LONG_TOKEN_HERE"
        }
      ],
      "validation": {
        "rules": [
          {
            "value": "200",
            "passIfFound": true,
            "type": "httpStatusCode"
          }
        ]
      },
      "configuration": {
        "acceptAnyCertificate": true,
        "followRedirects": true
      }
    }
  ]
}

