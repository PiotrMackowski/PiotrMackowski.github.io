---
title: OSINT your future employer
tags:
  - OSINT
  - LinkedIn
  - Google
---
Some employers do a very thorough background check on their prospective employees, so why shouldn't you return the favour? Whatever you have chosen to be interviewed for, I believe basic research is expected of every candidate. Think in terms of how the company makes money and what influences its position in the market. 

In security, deeper research is desired and an easy way to show you know your stuff. Also, unlike in other occupations, you should be able to pull off a bit of targeted open source intelligence on your interviewer without hiding it. Don't refrain from explicitly mentioning your preparation. As long as you manage to smoothly incorporate your findings into the conversation, you will leave a long-lasting impression on the other person. 

Your shopping list might include, but is not limited to:
- the homepage,
- disclosed security breaches, 
- reviews on Glassdoor,
- other job descriptions,
- Shodan,
- Google dorks,
- bug bounty platforms,
- the team you aspire to become part of and their activity:
	- LinkedIn & Github profiles,
	- conferences and meetups,
	- blogs and podcasts.

Your objective is to learn more about the company, the team and to find out whether you want to invest time in the recruitment process at all. Assuming you have the luxury to say no, this research helps you to avoid certain red flags. Also, your time is precious. The reality is that you will need to go through this quite a few times depending on your interview to offer ratio. Grab yourself something to write on, pick a target and follow along. 

Starting with the homepage and general news sites, get an idea what the business is about, what makes it profitable. Is it B2B, B2C or both? Does the industry mandate any compliance requirements? Look for (financial) reports. You don't need to be an expert in accounting to understand whether there's growth year on year or stagnation. If publicly traded, [check how the stock price](https://www.google.com/finance/) is holding up over the years. If private, verify who has the majority. An about us section might offer some information about the board and executives. Do they have someone responsible for security? If there's just a CIO, then security is most likely in scope of this person. Think about [the difference in company reporting structures](https://www.isc2.org/Insights/2024/07/CISO-Reporting-Lines-Why) and how this affects who calls the shots and how the budget flows down. 

Moving on to investments, take note of any (past) mergers and acquisitions. 
Let's face it, M&A's are tough for everyone involved, wherever you're in the food chain. Especially if IT is a supporting function rather than the core business, you can count on the business to accept the risk and to force IT to just make it happen. If entity A has a better security posture than entity B, most likely A won't like to establish trust with B. We shall first raise the security posture of B, and only then incorporate them or migrate their services and shut them down. Both strategies take time. IT ends up with a fragmented environment, which is harder to manage. The budget stays the same though, the investment shall pay off after all. 

In the interview, this knowledge allows you to ask strategic questions: "I noticed the recent acquisition of Company B. How is the team handling the migration of their legacy services? Are we isolating their environment or integrating it immediately?" This shows you understand the business risk, not just the technology.

To finish off the general information scraping, search for any disclosed security breaches. There are public repositories such as [breaches.cloud](https://www.breaches.cloud/), but your favorite search engine should do the trick just fine. Did the breach affect the bottom line anyhow? Additionally, reviews on sites like Glassdoor and GoWork (Poland specific) can give you a general idea of average employee satisfaction, but be mindful of the negativity bias. Often you will find insightful information you wouldn't get to know otherwise before starting the actual job, unless you have access to an insider. [Antisyphon training](https://www.youtube.com/watch?v=bUvVaXZRnTA) offers a practical approach to gaining such access if you're up for it. 

Prepare questions based on the information you have found. *While researching the position, I came across XYZ, how does that impact your responsibilities?* This shows you have done your homework and you get more information about what the team actually struggles with, which you can come back to later on in the conversation. Regardless of the type of financial trend identified earlier, you can mention you have checked the books and enquire how it affects the team. Perhaps there was a headcount reduction, or they had received more funding for trainings.  

Now it's time to move on to the tech stack. Your job description is the starting point. Then, go on a high level through other job descriptions (like DevOps, SRE's, IAM, network, compliance, system engineering, developers and data) to get an idea of the ecosystem. Once you have exhausted those, tools like Shodan, Censys or ZoomEye can be helpful to have a look from a slightly different angle. Do they have HTTPS, HSTS and a CSP everywhere? Say you're interviewing for a position at Tripadvisor, and the topic of system design comes up. Well, obviously a reliable service needs to have some kind of bot protection and CAPTCHA's, so this is where DataDome comes in. The Envoy proxy handles the API gateway and load balancing at the edge. Fastly is the CDN of choice. Instead of starting the discussion from scratch, disclose what your understanding of their system is, and consider asking the interviewer to fill in the missing parts. 

![Tripadvisor - Shodan results](/assets/images/Tripadvisor.jpg)
Recall the fragmented environment as a result of mergers and acquisitions discussed earlier. The below table might reflect those legacy systems the company failed to kill or actual honeypots. 

| Top Products               | Count |
| -------------------------- | ----- |
| nginx                      | 37    |
| SQL Server Browser Service | 19    |
| Lotus Domino httpd         | 1     |
| Apache httpd               | 1     |

DNS records often provide an interesting angle at SaaS integrations. A personal favorite of mine to check those is [web-check.xyz](https://web-check.xyz/), as it queries a holistic overview with stuff like security.txt in one click. Depending on the maturity of the company you can expect some of those records to be forgotten and left for the eternity or actually planted to deceive you. Most of these records serve a purpose that we can use to our advantage. Imagine yourself on the interview discussing a hypothetical security awareness campaign. It would make sense to craft one somewhat aligned to what users actually tend to interact with on a daily basis, wouldn't it? So instead of the usual M365 login page, you say you have checked their DNS records, and therefore, you propose two scenarios like _Dropbox - someone has shared a file_ and _Docusign - HR documents about to expire_ campaign.     

![DNS records](/assets/images/dnsrecords.jpg)    

Multi tenant SaaS solutions often follow a standard convention for their subdomains. Enumeration of those is straightforward and true positives are highly accurate:
- company.pagerduty.com
- company.webex.com
- company.zendesk.com
- company.slack.com
- company.service-now.com
- company.service-now.com/login.do (SSO bypass)
- company.my.salesforce.com
- company.docusign.net

Google dorks could go either way in my experience. I wouldn't spend a lot of time here, but you can just get lucky. After all, “luck is what happens when preparation meets opportunity.”
Try the following to discover subdomains and specific URL's:
- `site:target[.]com -www`
- `site:target[.]com (inurl:config OR inurl:dev OR inurl:test OR inurl:backup OR inurl:admin OR inurl:integration OR inurl:staging OR inurl:internal)`

If there's a public bug bounty program, take note of the scope. The larger the scope, the more challenging it is to sustain the program. You can enquire whether there are plans to expand the scope. The hardened, core environment, which is subject to certain audits, is most likely in scope, whereas less critical parts are not. 

Once you have a general idea of what is going on, it's time to dive deeper into individuals, who make it all happen. By going through LinkedIn profiles you should be able to establish a mind map who works with who and which people specialize in what. Often the experience section can offer some insight into what projects or initiatives have been conducted. If someone is active on the platform, pay attention to the latest mentions, comments, (company) events and posts. GitHub is also worth a shot. 

Finally, the most time consuming part: conferences, meetups, books, blogs and podcasts. This can be a lot to go through, so just focus on what or who interests you. If you have attended conferences in the past, there's a good chance you still have access to the recordings. If you did not, perhaps you can pay to receive access, or buy a ticket for the next edition, which comes with the access to the recordings of the past edition(s). Check YouTube for openly available content. If the team is active in the community, just being aware of what is happening is already an advantage. On a side note, if you have been a speaker at an event and it was recorded, you can count on people to grab a meeting room to watch it together. 

I hope I have equipped you with a few ideas you wouldn't have considered otherwise. In general - outcomes may vary, so try and see what works for you. Do the recon, find the gaps, and bring them to the table.