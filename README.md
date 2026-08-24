# CTF_writeup2
Challenge - Northstar Records 
CTF Name: [EHAX RecCTF 2026]
Category: Web Exploitation
Author : Sleepvendra

Challenge description: Northstar keeps the working copy of every case, decision, and late-night fix. Staff verify their accounts at the records desk — if a record looks restricted, verify the account's access level before escalating. Hint that was later in the discord server was "i dont really like anything sweet to eat ,however towards teh endpoint of my meal ,i do like some sweet cookies". solve it by crook or hook ".

website - https://ctf.ehax.in/challenges#Northstar%20Records-5
<img width="702" height="836" alt="image" src="https://github.com/user-attachments/assets/de163cea-80d7-4aa8-a11d-163aa83f6528" />

INITIAL RECONNAISSANCE :
The hint directly points to cookies, specifically looking at an endpoint related to sweet/dessert or meal paths, and modifying session cookies to elevate access.

The exact step-by-step methodology I used to solve this :
Inspect the Cookies-
  i.Open Chrome DevTools (F12 or Ctrl+Shift+I) on the challenge page.
  ii.Go to the Application tab > Storage > Cookies .
  iii.Look for cookie named session,auth,role,user or token.

  Picture of List of cookies 
  <img width="591" height="595" alt="image" src="https://github.com/user-attachments/assets/92af12a3-e725-4ab6-9899-1f9aabfac198" />

  Decoded the archive_... cookie:

  The value started with L2NoYWxs... which after already practicing some challlenges earlier I was clear that this is standard Base64 encoded.

  Copied the entire value of archive_... and decoded it using  CyberChef.

    <img width="976" height="641" alt="image" src="https://github.com/user-attachments/assets/b38efc8c-bab8-45d7-9ad6-a06f101f37ef" />

  Appended this path to the browser address bar and it opened up the following page
  <img width="981" height="718" alt="image" src="https://github.com/user-attachments/assets/74f9b867-daba-4675-b510-bbcb93100c93" />

  At this point of time , I was much intuitive about this being an sql injection since having practiced many sqli in portswigger labs.

  Tried standard SQL injection and credentials bypass payloads first

  Username: admin' OR 1=1--

  Password: random

  Flag Captured !!
