Have you ever wanted to gift someone sats in physical form? With a LNbits wallet you can easily create a NFC gift card. This works by writing a LNURLw link to the NFC card, from which the recipient can withdraw their sats with a LNURL-enabled wallet. 

### What do I need?
- LNbits wallet
- Android phone
- NFC card with at least NTAG2* capabilities, for example NTAG216. See nostr:naddr1qqxnzd3e8qcr2wfn8qcrgwf4qyg8wumn8ghj7mn0wd68ytnhd9hx2q3qtx0k0a7lw62vvqax6p3ku90tccgdka7ul4radews2wrdsg0m865sxpqqqp65whwqrr5 for where to purchase cards. 

💡 NTAG2* cards allow you to write **one** link onto them. They can for example act as a business card containing the URL to the company's website. NTAG424 cards not only have bigger memory but also something called a SUN parameter which allows web server authentication, which adds more security to your payments. The latter type of cards can also be made into [BoltCards]. 

### 1. Activate extension
Open your LNbits wallet. Activate the Withdraw Links extension from the toolbar and go to the extension. 

### 2. Create withdraw link
On the LNURLw extension page, choose `Advanced Withdraw Link(s).`

Choose the wallet from which the sats will be withdrawn. You probably want to separate this from your main LNbits wallet. To do this you can first create a new LNbits wallet from going to the toolbar and choosing `+ Add a new wallet`, then depositing some sats in the newly created wallet. 

Give the withdraw link a title. 

Set the minimum and maximum redeemable amounts. 

Set the number of times the link can be used and time between withdrawal attempts. 

You can optionally add a custom picture by checking the box for `Use a custom voucher design` and entering a URL to a .png image. 

Do not click the `assmilking` box. 

When you are happy with the configuration, proceed to `Create withdraw link`.

### 3. Write link to NFC card
On your newly created withdraw link, click on `view LNURL`. Click on the `Write to NFC` button and hold your NFC card up to your phone to be written. 

✔️ **DONE**

💡 Tell the recipient of the card about the sats balance of the card so that they don't waste their time trying to get every last satoshi. 

💡 Once the recipient has withdrawn their sats from the gift card, they can rewrite it to their own wallet and reuse it. Two birds, one stone! If the card you gave them is NTAG424, they can turn it into a Lightning "debit card" like we described in the nostr:naddr1qqxnzd3e8qcr2wfn8qcrgwf4qyg8wumn8ghj7mn0wd68ytnhd9hx2q3qtx0k0a7lw62vvqax6p3ku90tccgdka7ul4radews2wrdsg0m865sxpqqqp65whwqrr5. If the card is only NTAG2*, then they can only convert it into another gift card. 
