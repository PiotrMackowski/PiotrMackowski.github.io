---
title: How to 10x your Secure Score
tags:
  - Defender XDR
  - Microsoft
  - XSPM
---
How can you leverage the [Microsoft Secure Score](https://learn.microsoft.com/en-us/defender-xdr/microsoft-secure-score) to your advantage? The beauty of this tool lies in its ability to portray your security posture in a single number that is both understandable for a non-technical audience and relatable to the posture of other similarly sized companies. Securing leadership buy-in was never so easy before. 

*Your secure score is 52%, whereas organizations like yours score just 45%.*

Whether it's your job to set goals or to achieve them, the recommendations offer out of the box specific, measurable and relevant objectives. Upon closing them it's a piece of cake to communicate the value and the impact you have had on the security of your tenant. 

The exact set of recommendations depends on your tenant, i.e. what products you have licensed. A full-blown Enterprise Mobility + Security E3/E5 setup should result in a somewhat similar distribution of recommendations across Microsoft's products like below. 

| Product                           | Weight |
| --------------------------------- | ------ |
| Defender for Endpoint             | 60%    |
| Defender for Identity             | 12%    |
| Defender for Office               | 11%    |
| Exchange Online                   | 2%     |
| Intune                            | 3%     |
| Microsoft Entra ID                | 7%     |
| Other Apps                        | 5%     |

You'll immediately notice that MDE significantly impacts the overall score, so it makes sense to put the focus on hardening your endpoints. However, it's essential to first consider the needs and perspectives of your stakeholders. Unless you are a one-man-army type of operation, the products listed above are likely managed by various teams, each with a different appetite for security and reliability standards, as well as varying levels of interest in hardening their respective products. Therefore, your best bet might be to knock on everyone's door to gauge who is ready to collaborate promptly and who may place your request toward the end of their backlog. Act accordingly.

Nevertheless, Attack Surface Reduction rules will eventually end up on your plate. Some of them you won't be able to enforce at all, some require auditing and analysis. Some rules can be implemented in block mode without risking sleepless nights. [Nathan McNulty](https://blog.nathanmcnulty.com/defender-for-endpoint-implementing-asr-rules/) and [Jeffrey Appel](https://jeffreyappel.nl/microsoft-defender-for-endpoint-series-attack-surface-reduction-and-additional-protection-part4b/) have each published excellent hands-on material that should get you started. 

If you choose to not action a recommendation, it's beneficial to formally accept the risk in the portal, so that your peers have a clear picture of what is in progress, completed or accepted as is. Some recommendations are specific to highly regulated environments, and it is wise to just accept the risk in less regulated environments. For instance, while at first it may seem a good idea to not allow anonymous participants to join meetings in Teams, you will be unpleasantly surprised when you realise you have delayed several hiring processes because the candidates could not attend their virtual interview. 

### Why a 100% Score doesn't mean 100% Secure

The downside of partially building your leadership buy-in on the Secure Score is that certain aspects are outside of your control or not at all reflected in that number. The system can suddenly turn against you if the % drops, to name just a few examples; 
- Microsoft adds new recommendations that you are not compliant with,
- your company procures new products, which results in additional recommendations and a shift in the weights,
- your department onboards a bunch of endpoints, but the same hardening you have driven so diligently so far is not a part of the MVP. 

On the other hand, Microsoft Teams allows by default communication with external domains, yet there is no guidance (recommendation) on managing or restricting this setting. This feature permits users to connect with individuals outside the organization, who can reach them simply by knowing their email addresses. While this promotes cross-organizational collaboration, it also exposes your users to social engineering attacks. 
External users could exploit this functionality to verify active email addresses, initiate conversations on Teams, impersonate trusted contacts, or send malicious links and attachments with the intent to compromise devices or accounts. Additionally, this configuration enables external monitoring of user availability status and retrieval of Out of Office messages if configured. To mitigate these risks, you must restrict Teams communication to specific, trusted external domains - if external communication through Teams is required at all.