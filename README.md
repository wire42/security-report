Windows Security Report PowerShell Script



This PowerShell script collects and reports on key Windows security events from multiple servers. It gathers failed and successful logins, account management events, privileged activity, policy changes, object access, system events, and PowerShell execution logs. The script also enriches external IP addresses with geolocation data and emails a comprehensive HTML report.



Features
Multi-Server Support: Query any number of Windows servers remotely.

Event Coverage: Collects failed/successful logons, account lockouts, account changes, admin activity, policy changes, file/folder/registry access, system events, and PowerShell execution.

IP Geolocation: Enriches public source IPs with city, region, country, and ISP using the ip-api.com API.

Time Analysis: Calculates time between failed login attempts per user.

Detailed Reporting: Generates a well-structured HTML report and sends it via email.

Customizable: Easily adjust event categories, servers, and output.



Prerequisites
PowerShell 5.1 or later

Permissions to read Security and PowerShell logs on all target servers

Outbound internet access for IP geolocation lookups (to ip-api.com)

SMTP server details for email delivery


Configuration
Edit Server List:
Replace

powershell
$servers = @("Server1", "Server2")
with your server names or IP addresses.

SMTP Settings:
Update the Send-MailMessage parameters at the end of the script:

-From : Sender email address

-To : Recipient email address

-SmtpServer : Your SMTP server address

Event Categories:
The script covers a wide range of security events by default. You can add or remove event IDs in the $eventCategories hashtable.

Usage
Save the script as Get-WindowsSecurityReport.ps1.

Run in PowerShell (as an account with sufficient privileges):

powershell
.\Get-WindowsSecurityReport.ps1
Check your email for the HTML-formatted report.

Notes
API Rate Limits: The free ip-api.com service allows 45 requests per minute. The script includes a delay to avoid exceeding this limit.

Internal IPs: Private/internal IPs are not geolocated and are labeled as "Internal".

Security: Do not share the report externally, as it may contain sensitive information.

Customization:

To add more event types, expand the $eventCategories hashtable.

To export as CSV instead of HTML, use Export-Csv instead of ConvertTo-Html.

To summarize or filter results, add additional PowerShell logic before formatting the report.

Troubleshooting
Remote Log Access Errors: Ensure the running account has permissions to read event logs on all target servers.

Email Delivery Issues: Verify SMTP settings and firewall rules.

Geolocation Failures: Ensure the machine running the script has internet access.

License
This script is provided as-is, without warranty. Use at your own risk.

Questions or suggestions?
Contact your IT security team or the script author.
