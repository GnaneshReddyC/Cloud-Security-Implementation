company: CODTECH IT SOLUTION

NAME:GNANESH REDDY C

INTER ID:CTIS5317

DOMAIN: CLOUD COMPUTING

DURATION: 4 WEEKS

MENTOR: NEELA SANTOSH

task 4:Cloud Security Implementation

This task focuses on implementing Identity and Access Management (IAM) policies, secure storage mechanisms, and data encryption controls on Amazon Web Services to establish a secure and well-governed cloud environment. The primary objective was to enforce Role-Based Access Control (RBAC), apply the Principle of Least Privilege, secure object storage, and ensure encryption of data both at rest and in transit. To achieve this, core AWS services including AWS Identity and Access Management (IAM), Amazon S3, and AWS Key Management Service (KMS) were configured systematically.

The implementation began with IAM configuration. Three IAM groups were created to organize permissions according to job roles: AdminGroup, DeveloperGroup, and ReadOnlyGroup. The AdminGroup was attached with the AdministratorAccess managed policy to provide full access to AWS resources. The DeveloperGroup was assigned the PowerUserAccess policy, allowing broad service access without administrative control over IAM. The ReadOnlyGroup was granted the ReadOnlyAccess policy to restrict users to view-only permissions. IAM users were then created and assigned to these groups rather than being granted permissions individually. This group-based approach ensures scalability, centralized access management, and adherence to RBAC principles. A strong password policy was enforced requiring a minimum length of twelve characters including uppercase letters, lowercase letters, numbers, and special symbols. Additionally, Multi-Factor Authentication (MFA) was enabled for all IAM users to add an extra layer of authentication beyond passwords, significantly reducing the risk of credential compromise.

To enforce the Principle of Least Privilege, a custom IAM policy was created to limit developer access specifically to a designated S3 bucket named secure-project-bucket. The policy allowed only s3:GetObject and s3:PutObject actions on objects within that bucket. The implemented policy is shown below:

{
"Version": "2012-10-17",
"Statement": [
{
"Effect": "Allow",
"Action": ["s3:GetObject", "s3:PutObject"],
"Resource": "arn:aws:s3:::secure-project-bucket/*"
}
]
}

This custom policy was attached to the DeveloperGroup to ensure that developers could interact only with necessary resources and not gain excessive privileges.

Secure storage was configured using Amazon S3. A bucket named secure-project-bucket was created with all public access blocked at both bucket and account levels to prevent unintended exposure of data. Versioning was enabled to protect against accidental deletion and to maintain object history. To enforce encryption in transit, a bucket policy was applied to deny any requests that do not use secure HTTPS connections. The following bucket policy was implemented:

{
"Version": "2012-10-17",
"Statement": [
{
"Sid": "DenyInsecureTransport",
"Effect": "Deny",
"Principal": "",
"Action": "s3:",
"Resource": [
"arn:aws:s3:::secure-project-bucket",
"arn:aws:s3:::secure-project-bucket/*"
],
"Condition": {
"Bool": {
"aws:SecureTransport": "false"
}
}
}
]
}

This configuration ensures that any HTTP-based requests are denied, allowing only secure TLS-encrypted connections.

For encryption at rest, AWS Key Management Service (KMS) was used to create a customer-managed symmetric key named secure-project-key. Automatic key rotation was enabled to comply with security best practices and reduce long-term cryptographic risk. The S3 bucket was then configured to use Server-Side Encryption with KMS (SSE-KMS) as the default encryption method. This guarantees that all objects uploaded to the bucket are automatically encrypted using the managed key without requiring manual intervention. By combining KMS-based encryption with strict access control policies, the data remains protected against unauthorized access and data breaches.

Overall, this implementation successfully establishes a secure cloud environment by integrating IAM-based access control, encrypted storage, secure communication protocols, and key management best practices. The configuration aligns with AWS security standards and demonstrates a practical understanding of identity governance, storage security, and cryptographic protection mechanisms in a cloud infrastructure environment.

<img width="1612" height="315" alt="Image" src="https://github.com/user-attachments/assets/45ab59f7-476e-4d1f-a6a7-a4db7de86846" />

<img width="1598" height="402" alt="Image" src="https://github.com/user-attachments/assets/c1c03fb8-f109-49f0-906e-37134597e66a" />

<img width="1581" height="573" alt="Image" src="https://github.com/user-attachments/assets/1092fb20-d847-4dfe-98c3-ca3bb3b688a8" />

<img width="1918" height="492" alt="Image" src="https://github.com/user-attachments/assets/3204f864-60fc-48b8-ac3a-1072e6abb8bb" />

<img width="1907" height="457" alt="Image" src="https://github.com/user-attachments/assets/c1e904d2-00c6-49e6-bad6-4da98ce926a0" />



