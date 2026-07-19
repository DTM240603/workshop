---
title: "Event 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---

# Summary Report: "First Cloud AI Journey Community Day"

**Date & Time:** 09:00, 06/13/2026 &emsp; | &emsp; **Location:** 26th Floor, Bitexco Financial Tower – AWS Office, Ho Chi Minh City

### Event Objectives

- Create a space for networking and knowledge-sharing among bootcamp trainees, alumni, AWS Community Builders, and industry engineers.
- Inspire attendees about the cloud career path through a real-world story from someone further along the journey.
- Share real-world experience designing a large-scale system on AWS.
- Provide perspective on workplace culture and career opportunities at multinational corporations.

### Speakers

- **Danh Hoang Hieu Nghi** – AI Engineer, AWS Community Builder, AWS Student Builder Group Leader
- **Dinh Trung Kien** and **Nguyen Minh Tho** – FCJ trainees, authors of the URL Shortening Service project
- **Mr. Dat Pham** – Data Analytics Engineer
- **Mr. Cuong Nguyen** – Manufacturing Excellence Engineer

### Key Highlights

#### Presentation 1: "From First Cloud AI Journey to AWS Partner"

Speaker **Danh Hoang Hieu Nghi** shared his personal journey from a student curious about technology to becoming an AWS Partner through the First Cloud AI Journey program, following an **8-step** roadmap:

1. **Student Curiosity** – Starting with curiosity
2. **First Cloud Journey** – Finding the right learning environment
3. **Workshop & Community** – Learning from others
4. **Hands-on Labs** – Learning by doing
5. **School Projects** – Applying knowledge to real problems
6. **Portfolio** – Demonstrating capability
7. **AWS Partner** – Solving real-world problems
8. **Share Back** – Helping the next generation

The roadmap showed that the path from student to AWS Partner is not a sudden leap but a clear trajectory. The "Share Back" step especially emphasized the importance of community contribution.

![From First Cloud AI Journey to AWS Partner](/images/4-EventParticipated/4.2-Event2/1-from-fcj-to-aws-partner.jpg)

#### Presentation 2: "A Scalable URL Shortening Service on AWS"

Speakers **Dinh Trung Kien** and **Nguyen Minh Tho** presented their capstone project: building a highly scalable URL shortening service handling millions of redirect requests per day with low latency. The architecture consists of API Gateway + Lambda (creating short URLs), CloudFront + Lambda@Edge (redirects), DynamoDB (storing mappings), and ElastiCache Redis (caching). Four core design principles were summarized:

- **Separation of Concerns**: The read path and write path are fully decoupled, each optimized for its own traffic pattern rather than sharing a single bottleneck.
- **Defense at the Edge**: Security and caching are pushed to CloudFront/WAF, stopping threats at the edge before they reach the core system.
- **Pre-computation over On-demand**: Short codes are generated ahead of time and queued, ensuring instant, collision-free URL creation even under high load.
- **Cache-aside Pattern**: Redirects check the Redis cache first, only querying DynamoDB on a cache miss, keeping the database under minimal stress.

![A Scalable URL Shortening Service on AWS](/images/4-EventParticipated/4.2-Event2/2-url-shortening-service.jpg)

#### Presentation 3: "Real Stories on Culture at a Multinational Corporation"

**Mr. Dat Pham** (Data Analytics Engineer) shared his journey to becoming a data analyst: how he learned, and how he approaches and analyzes data in a real enterprise environment. **Mr. Cuong Nguyen** (Manufacturing Excellence Engineer) shared insights on workplace culture at a multinational corporation: professional English skills, distributed teamwork mindset, adapting to different working styles, and advice on building a portfolio and joining technical communities as early as possible while still a student.

![Real Stories on Culture at a Multinational Corporation](/images/4-EventParticipated/4.2-Event2/3-cau-chuyen-van-hoa.jpg)

### Key Takeaways

- The cloud career path has a clear trajectory (8 steps), and community contribution is an essential part of it, not a side activity.
- The four distributed-system design principles (Separation of Concerns, Defense at the Edge, Pre-computation over On-demand, Cache-aside Pattern) can be broadly applied to many different problems.
- Technical skill is necessary but not sufficient; communication, professional culture, and business thinking are what distinguish a good engineer from one who delivers real value to an organization.
- The Data Analytics Engineer role involves more than writing SQL and building dashboards — it also means designing data pipelines and being a bridge between engineering and the business.

### Applying to Work

- Applying the four design principles from the URL Shortener project (especially the Cache-aside Pattern and Separation of Concerns) to designing the API serving layer of the CloudBrief final project.
- Building a personal portfolio during the internship: the CloudBrief project, blog posts, and AWS certifications.
- Practicing presentation and communication skills for non-technical audiences, not just focusing on programming/deployment skills.
- Keeping the "Share Back" principle in mind — proactively sharing what I've learned with the community after completing the internship program.

### Event Experience

Attending the **First Cloud AI Journey Community Day** delivered value beyond the three presentations: the chance to network directly with the AWS Vietnam community, meet fellow FCJ trainees, and stay current on industry trends. I had the opportunity to discuss the CloudBrief final project idea and received useful feedback from experienced people. Seeing the journey of someone who came before — from FCJ student to AWS Partner — gave me strong motivation to complete my final project well.
