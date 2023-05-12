0x19. Postmortem

Server Outage Incident Report
On May 1st, 2023, we experienced a server outage on our company’s server infrastructure which resulted in our client's inability to use our services and we sincerely apologize for the financial loss our clients have incurred during this period.

Issue Summary

On May 1st 2023 (13:05 pm GMT + 1), we experienced a server outage (downtime) on our company’s server infrastructure for 2 hours. As a result, our clients experienced an HTTP 500 error which affected their business as they could not access our services. The root cause was not correctly testing out all implemented upgrades before pushing them to production servers.

Timeline (all time in GMT + 1)
Time (GMT + 1)	Actions
13:00 PM		Upgrades implementation begins
13:05 PM		Server Outage begins
13:10 PM		Pagers alerted the on-call team
13:15 PM		On-call team acknowledgment
13:40 PM		Rollback initiation begins
14:00 PM		Successful rollback
14:30 PM		Server restart initiated
15:00 PM		100% of traffic back online

Root cause

Server upgrades were initiated across all of our production servers at 13:00pm (GMT + 1) without previously deploying on our test environments and doing all essential unit testing. Part of the upgrade supplied to the production server required authentication from a third-party software; however, this new implementation is not supported on the current version on our servers, resulting in downtime. We were able to swiftly remedy this by first rolling back the server's prior state and then upgrading the current version on our servers.

Preventive measures

Pushing all intended changes first to our test environments before shipping to the live server.
Increase the performance metrics threshold to alert on-call engineers in the event of a possible server crash

Addressing the issue

Develop and implement additional testing procedures for website updates and integrations. 
Update monitoring and alerting systems to detect and respond to similar issues more quickly. 
Develop and document incident response procedures to ensure issues are resolved as efficiently as possible.

