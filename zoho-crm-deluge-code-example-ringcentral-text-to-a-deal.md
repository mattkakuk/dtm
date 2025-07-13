---
id: 8367
title: 'Zoho CRM Deluge Code Example: RingCentral Text to a Deal'
date: '2024-09-21T21:25:51+00:00'
author: 'Matt Kakuk'
layout: page
guid: 'https://digitaltransformationmanagement.ai/?page_id=8367'
social_share_style:
    - global
---

## Code Example: Text a deal via RingCentral.

### Step-by-Step Instructions for Publishing the Zoho Deluge Script on Your Site

#### **Step 1: Create a Custom Function in Zoho CRM**

1. **Log in to Zoho CRM**: Start by logging in to your Zoho CRM account.
2. **Navigate to Settings**: Click on the gear icon (⚙️) in the top-right corner of the page to go to CRM settings.
3. **Go to Workflow Rules**: In the "Automation" section, click on **Workflow Rules**.
4. **Create a New Workflow**:
    
    
    - Choose the module as **Deals** since the function will run when a deal record is created or updated.
    - Define the conditions when the workflow should be triggered (e.g., when a deal is created, edited, or specific fields are updated).
    - Set the **Trigger** to specify when the SMS should be sent (e.g., when the contact is added to the deal).
5. **Add Custom Action**: After defining the workflow rules, go to the “Instant Actions” section and click on **Custom Function**.
6. **Create New Custom Function**:
    
    
    - Click **New Custom Function**.
    - Give it a name, such as "Send\_SMS\_to\_Deal\_Contact".
    - Set the module as **Deals**.
    - In the function editor, paste the updated Deluge script.

```
void automation.send_RC_SMS_to_contact_of_deal(string dealID)<br></br>{<br></br>// Fetch the deal record by its ID<br></br>dealRecord = zoho.crm.getRecordById("Deals", dealID);<br></br><br></br>// Check if the Contact lookup field is available in the deal record<br></br>if(dealRecord.get("Contact_Name") != null)<br></br>{<br></br>// Get the Contact ID from the Deal<br></br>contactId = dealRecord.get("Contact_Name").get("id");<br></br>contactRecord = zoho.crm.getRecordById("Contacts", contactId); // Fetch the Contact record<br></br><br></br>// Check if the contact exists and has an ID<br></br>if(contactRecord.get("id") != null)<br></br>{<br></br>// Check if SMS_Opt_Out is false (unchecked)<br></br>if(contactRecord.get("SMS_Opt_Out") == false)<br></br>{<br></br>contactFirstName = ifnull(contactRecord.get("First_Name"), "");<br></br>contactMobile = contactRecord.get("Mobile");<br></br><br></br>if(contactMobile != null)<br></br>{<br></br>// Get the Deal Owner (optional based on your needs)<br></br>dealOwner = dealRecord.get("Owner");<br></br>ownerRecord = zoho.crm.getRecordById("users", dealOwner.get("id"));<br></br><br></br>// Retrieve the RC Account ID from the user (Owner) record<br></br>AccountId = "";<br></br>if (ownerRecord.get("users") != null)<br></br>{<br></br>AccountId = ownerRecord.get("users").get(0).get("RC_Account_ID");<br></br>}<br></br><br></br>// Define the extension ID, from number, and the message content<br></br>ExtensionId = ""; // Optional Extension ID<br></br>FromNumber = ""; // Optional From Number (use if different from account number)<br></br>MsgText = "Hi " + contactFirstName + ", just checking in to make sure you received my proposal. Let me know if you have any questions. - Matt Kakuk";<br></br><br></br>// Send the SMS using the correct API call<br></br>resp = multiuserringcentralmessagingextension.sendRcSms(AccountId, ExtensionId, FromNumber, contactMobile, MsgText);<br></br>info resp; // Log the response for debugging<br></br>}<br></br>else<br></br>{<br></br>info "Contact does not have a mobile number.";<br></br>}<br></br>}<br></br>else<br></br>{<br></br>info "Contact has opted out of SMS communication.";<br></br>}<br></br>}<br></br>else<br></br>{<br></br>info "Contact record not found.";<br></br>}<br></br>}<br></br>else<br></br>{<br></br>info "No contact associated with this deal.";<br></br>}<br></br>}
```

## Get Started Now

 Sign up for a discovery call for this extension ## Simple steps

 [ Step 1: Download the Extension ](https://booknow.digitaltransformationmanagement.ai/#/customer/3989982000000065008) [ Step 2: Book Implementation Meeting ](https://booknow.digitaltransformationmanagement.ai/#/customer/3989982000000065008)Don’t have Zoho CRM yet? [Sign up here for a FREE trial.](https://store.zoho.com/ResellerCustomerSignUp.do?id=665fcaaac748dba6eb18d8d5e0c630c0)

Don’t have RingCentral yet? [Fill out the form](https://digitaltransformationmanagement.ai/contact-us/) and we set you up with that also.

 <svg aria-hidden="true" viewbox="0 0 448 512" xmlns="http://www.w3.org/2000/svg"><path d="M313.6 304c-28.7 0-42.5 16-89.6 16-47.1 0-60.8-16-89.6-16C60.2 304 0 364.2 0 438.4V464c0 26.5 21.5 48 48 48h352c26.5 0 48-21.5 48-48v-25.6c0-74.2-60.2-134.4-134.4-134.4zM400 464H48v-25.6c0-47.6 38.8-86.4 86.4-86.4 14.6 0 38.3 16 89.6 16 51.7 0 74.9-16 89.6-16 47.6 0 86.4 38.8 86.4 86.4V464zM224 288c79.5 0 144-64.5 144-144S303.5 0 224 0 80 64.5 80 144s64.5 144 144 144zm0-240c52.9 0 96 43.1 96 96s-43.1 96-96 96-96-43.1-96-96 43.1-96 96-96z"></path></svg>### Step 1 :

Download the Extension [ ](https://marketplace.zoho.com/app/crm/multi-user-ringcentral-texting-for-zoho-crm) [ ](https://marketplace.zoho.com/app/crm/multi-user-ringcentral-texting-for-zoho-crm) <svg aria-hidden="true" viewbox="0 0 448 512" xmlns="http://www.w3.org/2000/svg"><path d="M313.6 304c-28.7 0-42.5 16-89.6 16-47.1 0-60.8-16-89.6-16C60.2 304 0 364.2 0 438.4V464c0 26.5 21.5 48 48 48h352c26.5 0 48-21.5 48-48v-25.6c0-74.2-60.2-134.4-134.4-134.4zM400 464H48v-25.6c0-47.6 38.8-86.4 86.4-86.4 14.6 0 38.3 16 89.6 16 51.7 0 74.9-16 89.6-16 47.6 0 86.4 38.8 86.4 86.4V464zM224 288c79.5 0 144-64.5 144-144S303.5 0 224 0 80 64.5 80 144s64.5 144 144 144zm0-240c52.9 0 96 43.1 96 96s-43.1 96-96 96-96-43.1-96-96 43.1-96 96-96z"></path></svg>### Step 2 :

Book Your Implementation Meeting [ ](https://booknow.digitaltransformationmanagement.ai/#/3989982000000065008) [ ](https://booknow.digitaltransformationmanagement.ai/#/3989982000000065008)Don’t have Zoho CRM yet? [Sign up here for a FREE trial.](https://store.zoho.com/ResellerCustomerSignUp.do?id=665fcaaac748dba6eb18d8d5e0c630c0)

Don’t have RingCentral yet? [Fill out the form](https://digitaltransformationmanagement.ai/contact-us/) and we set you up with that also.

 <svg aria-hidden="true" viewbox="0 0 384 512" xmlns="http://www.w3.org/2000/svg"><path d="M288 248v28c0 6.6-5.4 12-12 12H108c-6.6 0-12-5.4-12-12v-28c0-6.6 5.4-12 12-12h168c6.6 0 12 5.4 12 12zm-12 72H108c-6.6 0-12 5.4-12 12v28c0 6.6 5.4 12 12 12h168c6.6 0 12-5.4 12-12v-28c0-6.6-5.4-12-12-12zm108-188.1V464c0 26.5-21.5 48-48 48H48c-26.5 0-48-21.5-48-48V48C0 21.5 21.5 0 48 0h204.1C264.8 0 277 5.1 286 14.1L369.9 98c9 8.9 14.1 21.2 14.1 33.9zm-128-80V128h76.1L256 51.9zM336 464V176H232c-13.3 0-24-10.7-24-24V48H48v416h288z"></path></svg>### New RingCentral MultiUser Zoho CRM Extension BETA

Get install and support documents here [ ](https://support.digitaltransformationmanagement.ai/portal/en/kb/new-ringcentral-multiuser-zoho-crm-extension-beta) ![](https://digitaltransformationmanagement.ai/wp-content/uploads/2022/07/img-04.webp) ![](https://digitaltransformationmanagement.ai/wp-content/uploads/2022/07/img-03.webp) ![](https://digitaltransformationmanagement.ai/wp-content/uploads/2022/07/shape-3.svg) ![](https://digitaltransformationmanagement.ai/wp-content/uploads/2024/02/circle-quarter-blue.png)## Call Today to find out more or to get started

 We're here to assist you and provide the information you need. [ (561) 331 5360 (561) 331 5360 ](tel:+15613315360) ![](https://digitaltransformationmanagement.ai/wp-content/uploads/2024/03/zoho_premium_partner.png) ![](https://digitaltransformationmanagement.ai/wp-content/uploads/2024/03/ringcentral-partner-logo-2048x202-1-1024x101.png)