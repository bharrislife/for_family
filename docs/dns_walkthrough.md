
# Plain-English DNS Walkthrough

## 1. How DNS Works: The Internet's Phonebook
When someone types a custom web address (like bettyharris.flyrank.ai) into their browser, the computer needs an IP address (a numerical internet coordinate) to know where that site physically lives. 

Here is what happens behind the scenes:
1. The Request (Browser): Your browser asks a DNS Resolver: "Where is this domain located?"
2. The Search (Nameserver): The Resolver queries the Authoritative Nameserver holding records for the domain.
3. The Answer (DNS Record): The Nameserver checks its records and replies: "That name points to our web server over at Netlify!"
4. The Page Loads: Your browser connects to that server and loads the website over HTTPS.

---

## 2. What is a CNAME Record?
* CNAME (Canonical Name Record): A digital alias or forwarding rule that links one domain name to another domain name, rather than a fixed IP address.
* Value for my FlyRank subdomain: 
  * Name: bettyharris (or bettyharris.flyrank.ai)
  * CNAME Value / Target: betty-harris.netlify.app

When Ops provisions bettyharris.flyrank.ai with a CNAME pointing to my host URL, anyone visiting my FlyRank address will seamlessly land on my hosted site without moving any code or files.
