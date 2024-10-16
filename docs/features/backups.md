# Backups

Ivee automatically backs up your instances to ensure data safety and business continuity. 
Our backup system is designed to provide:

* **Automated Backups:** We take care of your backups, so you don't have to.  No manual intervention is required.
* **Incremental Backups:**  Ivee utilizes incremental backups, capturing only the changes made since the last backup.
* This minimizes storage space and backup time, which lowers your cloud bill even further in [Bring Your Own Account mode](/deploy/mode-byoa.md).
* **Data Consistency:**  Our backup process guarantees data consistency, ensuring you can reliably restore to any point in time.
* **Low RPO:** Incremental backups contribute to a low Recovery Point Objective (RPO), meaning minimal data loss in case of a failure.

**Backup Configuration and Schedule:**

The frequency and retention period of your backups depend on the tier you choose. For example, in a free tier 
we take backups every 6 hours and store them for 3 days. Whereas for production workloads, we backups are stored every 
5 minutes and kept for 30 days.

This means that in the unlikely event of data loss, you can quickly restore your database to a recent state, 
minimizing downtime and impact on your applications.
