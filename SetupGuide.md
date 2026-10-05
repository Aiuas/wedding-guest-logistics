# Deployment Guide: Wedding Guest App

Follow these steps to deploy your custom wedding guest logistics app using Google Apps Script.

## Step 1: Set up Google Drive & Sheets
1. **Create a Drive Folder:** Go to Google Drive and create a new folder named `Wedding Guest Passports`.
2. **Get the Folder ID:** Open the folder. Look at the URL in your browser: `https://drive.google.com/drive/folders/YOUR_FOLDER_ID`. Copy `YOUR_FOLDER_ID`.
3. **Create a Google Sheet:** In your Google Drive, create a new Google Sheet. Name it `Wedding Logistics`.
4. **Rename the Tab:** At the bottom, rename `Sheet1` to `Guest Data`.
5. **Set up Columns:** The columns have been updated to support the new Group ID and Transport Mode features. 
   **Copy the text below, single-click cell A1 in your sheet, and paste it. Then click Data > Split text to columns:**
   
   ```text
5. ### 3. Setup the Columns
Create the following columns in **Row 1** (A through AC, total 29 columns). **It is critical these are in this exact order.**

1. Timestamp
2. Group ID
3. First Name
4. Last Name
5. Email
6. WhatsApp
7. Arr Transport Mode
8. Arr Transport No
9. Arr Date
10. Arr Time
11. Arr Location
12. Arr Terminal
13. Dep Transport Mode
14. Dep Transport No
15. Dep Date
16. Dep Time
17. Dep Location
18. Dep Terminal
19. ID Link
20. Assigned Driver (Arrival)
21. Driver Phone (Arrival)
22. Car Details (Arrival)
23. Send Arrival Email [Checkbox]
24. Arrival Email Status
25. Assigned Driver (Departure)
26. Driver Phone (Departure)
27. Car Details (Departure)
28. Send Departure Email [Checkbox]
29. Departure Email Status

*(Tip: In your sheet, select Column W (23) and Column AB (28) starting from row 2 downwards, and click **Insert > Checkbox** so each row has an easy 1-click send button! When clicked, it automatically sends the email and unchecks itself.)*

### 4. Create the Web App Backend
1. In your Google Sheet, click on **Extensions > Apps Script**.
2. Delete the default `Code.gs` file.
3. You need to create 7 separate files in the Apps Script editor to match the structure of our new modular app. 
   - Click the `+` icon next to "Files" to create them. 
   - **For Script files (`.gs`), create:** `Main`, `API`, `Database`, `Triggers`
   - **For HTML files (`.html`), create:** `Index`, `Styles`, `Scripts`
4. Copy the code from the corresponding files in your local folder into these newly created Apps Script files.
5. In `Main.gs`, update the `SHEET_ID` with the ID of your Google Sheet.
6. In `Main.gs`, update the `FOLDER_ID` with the ID of your Google Drive folder.

### 5. Setup the Automated Emails
1. In the Apps Script editor, click the **Triggers** icon (it looks like a clock) on the left sidebar.
2. Click **+ Add Trigger** (bottom right).
3. Set it up as exactly as follows:
   - Choose which function to run: `onEditTrigger`
   - Choose which deployment should run: `Head`
   - Select event source: `From spreadsheet`
   - Select event type: `On edit`
4. Click Save (you may need to authorize permissions). here. Click your account, then "Advanced", and "Go to Wedding Logistics App (unsafe)". Click Allow.*

## Step 4: Deploy as a Web App
1. In the top right corner of the Apps Script editor, click **Deploy > New deployment**.
2. Click the gear icon ⚙️ next to "Select type" and choose **Web app**.
3. Fill in the details:
   - Description: "Version 1"
   - Execute as: **Me** (This is critical so guests don't need to log in to upload files).
   - Who has access: **Anyone**
4. Click **Deploy**.
5. **Copy the Web App URL!** 

## Step 5: Add to Canva
1. Go to your Canva website design.
2. Add a beautifully styled Button that says "RSVP & Submit Flight Details".
3. Link that button to the **Web App URL** you copied in Step 4.
4. Alternatively, use Canva's **Embed** app and paste the Web App URL to embed it directly (test this on mobile to ensure it feels smooth).

You're done! Test it by submitting a fake entry and then assigning a fake driver in your Google Sheet (remember, you only need to assign the driver to the primary guest's row, as they are the only ones with the email on file).
