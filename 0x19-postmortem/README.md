Postmortem: Web Stack Outage Incident

By Umar Kabiru (adermkabeer@gmail.com) 

Issue Summary
  - Duration: April 10, 2023, 14:30 - April 10, 2023, 17:45 (WAT)
  - Impact: The user authentication service experienced a widespread outage, resulting in slow login times and complete unavailability for approximately 25% of users.
  - Root Cause: An underlying database query inefficiency caused a cascading effect on the authentication service, leading to high CPU and memory usage.

Timeline:
  - Detected: April 10, 2023, 14:30 (WAT)
    - Method: An automated monitoring alert indicated increased response times for user login requests.
  - Actions Taken:
    - Initial investigation focused on load balancer configuration, followed by scaling the service horizontally.
    - Assumed root cause was increased user traffic due to a marketing campaign.
  - Misleading Investigation/debugging Paths:
    - Incorrectly suspected a DDoS attack and expended resources on network analysis and firewall configuration
    - Additionally, reviewed application logs for unusual activity unrelated to the issue.
  - Escalation: Incident was escalated to the DevOps team and database administrators for further analysis.
   -Resolution: The issue was resolved by optimizing the underlying database queries, implementing caching mechanisms for authentication tokens, and redeploying the authentication service.

Root Cause and Resolution:
  - Root Cause: The primary cause of the issue was identified as inefficient database queries that retrieved user credentials. These queries resulted in high CPU and memory usage, impacting the overall performance of the authentication service.
  - Resolution: The team optimized the database queries by adding appropriate indexes and rewriting the queries to reduce their complexity. Additionally, a caching layer was introduced to store and retrieve authentication tokens, reducing the need for frequent database calls. The updated code was thoroughly tested and deployed, leading to a significant reduction in CPU and memory consumption.

Corrective and Preventative Measures:
  Improvements/Fixes:
  - Enhance monitoring capabilities to detect performance degradation and anomalies in real-time.
  - Implement automated scaling mechanisms to handle sudden spikes in user traffic.
  - Establish a clear communication protocol for incident escalation and cross-team collaboration.
  - Develop a comprehensive incident response plan that includes specific troubleshooting steps.

Tasks to Address the Issue:
  - Optimize database queries for other critical services to prevent similar performance bottlenecks.
  - Regularly review and update monitoring thresholds based on evolving traffic patterns.
  - Conduct a thorough review of all service dependencies to identify potential single points of failure.
  - Schedule routine code reviews and performance audits to proactively identify and address performance-related issues.

Lessons Learned:
This incident highlighted the importance of a systematic approach to debugging and troubleshooting. Our initial focus on external factors such as network attacks diverted valuable time and resources from addressing the actual root cause. By improving our monitoring, escalation procedures, and communication channels, we can better respond to incidents and collaborate efficiently across teams. Additionally, we recognize the necessity of continuous performance optimization to ensure a seamless user experience.
 
Conclusion:
The web stack outage on April 10, 2023, served as a valuable learning experience for our team. Through a combination of enhanced monitoring, efficient incident response, and proactive performance optimization, we have implemented measures to prevent similar incidents in the future. We remain committed to delivering reliable and high-performance services to our users while continually improving our systems to meet evolving demands.

