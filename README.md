# TM-FileStorageSecurity-Wasabi
A how-to guide for using Trend Micro's File Storage Security to secure your Wasabi storage buckets.

Wasabi is a competitively priced cloud storage provider that's similar in feel to AWS S3. Currently, they claim to charge 80% less than S3 ($6.99 p/TB) and don't charge data egress or API fees. Wasabi has fewer availability zones than S3, but to their credit, I've never had any performance issues with their services. (https://wasabi.com/)

File Storage Security by Trend Micro is one of the best solutions available for scanning files/objects in cloud storage. It's also highly customizeable, many of the cloud services it leverages can be modified to suit a given use-case. (https://www.trendmicro.com/en_us/business/products/hybrid-cloud/cloud-one-file-storage-security.html)

Architecture of File Storage Security in AWS: https://cloudone.trendmicro.com/docs/file-storage-security/arch-overview-aws/. Out of the box, FSS can be deployed to AWS, Azure or GCP. We're going to be adding additional lambda functions to the Fss flow so that we can pull newly added objects from our wasabi buckets, scan them within aws, and then send the results back to our Wasabi account so we can then organize the files into a promotion or quarantine bucket (if the file is malicious). A separate landing bucket in wasabi will be receiving the objects we upload. 


