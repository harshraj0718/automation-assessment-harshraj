# Bonus: Kimai Demo Uptime Monitor

The optional n8n workflow checks `https://demo-stable.kimai.org/` every five minutes, retries failed requests, and emails an alert when the site returns a non-200 response or the request fails. Healthy checks are recorded without sending an email.

`Bonus_UptimeMonitor_HarshRaj.json` includes the Gmail credential reference and recipient. `Bonus_UptimeMonitor_Canvas_HarshRaj.png` shows the configured canvas. Gmail API access is enabled for the connected credential. The monitor remains inactive and was not included in the Task 2 test execution.
