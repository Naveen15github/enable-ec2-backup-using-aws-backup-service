# enable-ec2-backup-using-aws-backup-service
![Alt text]()

In this task, I enabled automated EC2 backup using the AWS Backup service.
I created a backup vault, backup plan, assigned my EC2 instance to that plan, and verified that the backup job ran successfully.
This helps to automatically protect EC2 instances without taking manual AMIs every time.

## 🪜 Steps I Did
🔹 1. Opened AWS Backup Service

I went to the AWS Management Console, searched for “Backup”, and opened the AWS Backup dashboard in the same region where my EC2 instance was running.

🔹 2. Created a Backup Vault

I clicked on Backup vaults → Create Backup vault.

Gave a name like MyBackupVault.

Used the default AWS KMS encryption key for security.

Then clicked Create Backup vault.

✅ My backup vault was successfully created to store all EC2 backups.

🔹 3. Created a Backup Plan

I clicked on Backup plans → Create Backup plan.

Selected Build a new plan option.

Named it Daily-EC2-Backup-Plan.

Under Backup rule, I set:

Frequency: Daily

Backup window: Default

Retention period: 7 days

Backup vault: MyBackupVault

Then clicked Create plan.

✅ My backup plan was created successfully to automatically take backups every day.

🔹 4. Assigned My EC2 Instance to the Backup Plan

I opened my backup plan and clicked Assign resources.

Gave a name like EC2-Backup-Assignment.

Selected Resource type = EC2.

Selected my existing EC2 instance ID.

Used the IAM role suggested by AWS Backup.

Then clicked Assign resources.

✅ My EC2 instance was successfully assigned to the backup plan.

🔹 5. Verified Backup Job

I went to Backup jobs and saw the backup job running automatically.

Once the status changed to Completed, I confirmed that the backup was stored safely in my vault.
![Alt text](image_url)

✅ Backup completed successfully and stored inside MyBackupVault.

🔹 6. Restored the Backup (Testing)

To check if the backup works,

I went to Protected resources → EC2.

Selected the completed backup → clicked Restore.

Used the same settings and launched a new EC2 instance from the backup.

The instance launched perfectly and had the same data/configuration.

✅ Restore was successful — backup worked perfectly.

💡 What I Learned

How to automate EC2 backups using AWS Backup instead of doing it manually.

How to create backup vaults and plans for daily/weekly backups.

How to restore an instance directly from a backup job.

How lifecycle and retention work for managing backup storage.

⚙️ Services Used

AWS Backup

Amazon EC2

AWS Identity and Access Management (IAM)

AWS Key Management Service (KMS)

🏁 Final Result

I successfully enabled automatic EC2 backup using AWS Backup Service.
Now my EC2 instance gets backed up daily into my backup vault, and I can restore it anytime in case of data loss or failure.
This setup makes my AWS environment more reliable and recovery-ready. ✅
