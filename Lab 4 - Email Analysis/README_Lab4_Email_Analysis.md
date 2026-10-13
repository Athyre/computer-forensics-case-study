# Lab 4: E-mail Analysis of a Suspect Mailbox

## Overview

This lab is part of a computer forensics portfolio that analyzes a single suspect disk image, `Vader_Home_Computer.001`. It focuses on locating and parsing the suspect's **Mozilla Thunderbird mailbox** to find evidence of illegal activity and to reconstruct what happened from the e-mails.

**Tools used:** FTK Imager (image mounting), MiTeC Mail View

**Skills demonstrated:** mounting forensic images, e-mail artifact analysis, header and timestamp review, timeline reconstruction, evidence-based reporting

## The Challenge

The suspect's computer contained a Thunderbird mailbox (Inbox, Sent, and Trash). The investigation had to answer:

- Who owns the mailbox and what is the e-mail address?
- When were the first e-mails sent and received?
- Is there any indication of criminal activity, who is involved, and what series of events took place?

## The Solution

1. **Mounted the image** `Vader_Home_Computer.001` with FTK Imager.
2. **Opened the mail files** in MiTeC Mail View from `...\Application Data\Thunderbird\Profiles\cnllzbsb.default\Mail\pop.mail.yahoo.com`, loading the Inbox, Sent, and Trash files (not the `.msf` index files).
3. **Reviewed the messages** by sorting on headers, collecting all e-mail addresses, and filtering for key terms.
4. **Built a timeline** of the relevant e-mails, recording the evidence reference (folder and message number), sender, recipients, subject, and timestamp for each.

## Key Findings

**Mailbox owner:** Darth Vader (`dvader454@yahoo.com`)

**First e-mails:**

| Direction | Date / Time | Details |
|---|---|---|
| Received | 5 April 2014, 01:00:30 | Yahoo account activation message |
| Sent | 5 April 2014, 01:33:36 | Reply to an Olive Garden welcome e-mail |

**People involved in the suspected crime:**

| Name | E-mail | Role |
|---|---|---|
| Darth Vader | dvader454@yahoo.com | Seller claiming to own 20 lightsabers |
| Sith Lord | sith_lord8989@hotmail.com | Broker connecting the seller and the buyer |
| Jabba | jabba.the.hut1212@gmail.com | Buyer |

**Series of events (8-10 April 2014):**

1. Sith Lord tells Darth he has a buyer for "Black Market Light Sabers". Darth accepts, claims to own 20 lightsabers, agrees to 16,500 space bucks each, and offers Sith Lord a 10% commission for his silence.
2. Sith Lord warns that the buyer, Jabba, may become violent if the deal fails. Darth asks to be introduced and says he will handle the risk.
3. Sith Lord introduces Darth and Jabba. Jabba asks for proof of authenticity, and Darth sends photos.
4. Jabba agrees to pay in two stages. Darth sends a zip file of certificates whose contents are labelled "Fake Authenticity Papers" and asks for payment.
5. Jabba sends a link to an executable file (`Jabbas_Money.exe`) as the payment link. Darth reports it as dead, Jabba resends it, and on 10 April Darth still reports an error. This is the last e-mail found.

## Conclusion

The e-mails indicate a suspected illegal lightsaber deal between three people, including forged authenticity documents and a commission offered for silence. The mailbox ends before the outcome, so it cannot be confirmed whether the payment was made or the items were delivered. The lab shows how e-mail evidence can reveal the people involved, the timeline, and intent, while also showing why further investigation is needed to confirm the final outcome.

## Evidence and Documentation

Screenshots of every e-mail referenced above and the full lab report: `[LINK]`

## Repository Structure

```
Lab4-Email-Analysis/
├── README.md
├── report/        # lab report (DOCX/PDF)
└── screenshots/   # mounted image, mailboxes, key e-mails
```
