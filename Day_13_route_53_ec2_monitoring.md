Route 53 - EC2 Monitoring:
-------------------------

1. Launch and EC2 instance allowing HTTP and SSH.

2. Copy the public IP of your EC2 instance.

3. Go to route 53 and crrate a health check.

4. Paste the copied public IP in route 53.

5. Choose fast 10-fault detection, and view latency.

6. Opt for alamrs and add email for notifications.

7. monitor health status.

8. Test it by removing HTTP rule.
