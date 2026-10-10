# Deployment Guide: Wedding Guest App

Follow these steps to deploy your custom wedding guest logistics app using Google Apps Script.

## Step 1: Set up Google Drive & Sheets
1. **Create a Drive Folder:** Go to Google Drive and create a new folder named `Wedding Guest Passports`.
2. **Get the Folder ID:** Open the folder. Look at the URL in your browser: `https://drive.google.com/drive/folders/YOUR_FOLDER_ID`. Copy `YOUR_FOLDER_ID`.
3. **Create a Google Sheet:** In your Google Drive, create a new Google Sheet. Name it `Wedding Logistics`.
4. **Rename the Tab:** At the bottom, rename `Sheet1` to `Guest Data`.
5. **Set up Columns:** The columns for `Guest Data` have been streamlined to 21 columns (A through U).
   All vehicle management, driver assignments, and email notifications now live in the dedicated **Car Logistics** and **Car Fleet** tabs.
   
   **Row 1 (Columns A through U, total 21 columns):**
   
   1. Timestamp (A)
   2. Group ID (B)
   3. First Name (C)
   4. Last Name (D)
   5. Email (E)
   6. WhatsApp (F)
   7. Arr Mode (G)
   8. Arr Flight/Train No (H)
   9. Arr Date (I)
   10. Arr Time (J)
   11. Arr Airport/Station (K)
   12. Arr Terminal (L)
   13. Dep Mode (M)
   14. Dep Flight/Train No (N)
   15. Dep Date (O)
   16. Dep Time (P)
   17. Dep Airport/Station (Q)
   18. Dep Terminal (R)
   19. ID Link (S)
   20. Flight Status (Arrival) (T)
   21. Flight Status (Departure) (U)

*(Tip: In Google Sheets, you can automatically initialize or migrate these columns anytime by clicking **Wedding Logistics > 🔄 Reorganize Guest Data Tab (Move Flight Status to T & U)** from the custom menu.)*

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
