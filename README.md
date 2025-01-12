<p align="center">
  <img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>File Share Permissions and Access Testing</h1>
I will show you how to share folder permissions with groups in your organization or with specific profiles, so they can edit, have no access, or only read. <br />

<h2>Step 1: Create File Shares with Various Permissions</h2>

1. **Log into DC-1 as Domain Admin:**
   - On DC-1, log in as `mydomain.com\Mateo_admin` (domain admin account).

2. **Log into Client-1 as a Normal User:**
   - On Client-1, log in as `mydomain\<someuser>` (normal user account).

3. **Create Folders on DC-1:**
   - On DC-1, navigate to the `C:\` drive.
   - Create the following 4 folders:
     - `read-access`
     - `write-access`
     - `no-access`
     - `accounting` (for later use)

4. **Set Permissions and Share the Folders:**
   - Right-click each folder, select **Properties**, and go to the **Sharing** tab.
   - Click **Advanced Sharing** and enable sharing for the folders.
   
   Now, set the following permissions for each folder:
   - **Folder: "Midi- Mateo"**
     - Group: `Domain Users`
     - Permissions: **Read**
     - (Share this folder)
  <img src="https://i.imgur.com/QQaz16M.png" alt="Traffic Examination"/>   
   - **Folder: "Mateo-songs"**
     - Group: `Domain Users`
     - Permissions: **Read/Write**
     - (Share this folder)
   
   - **Folder: "no-access"**
     - Group: `Domain Admins`
     - Permissions: **Read/Write**
     - (Share this folder)

5. **Skip setting permissions for the "accounting" folder for now.**

---

<h2>Step 2: Attempt to Access File Shares as a Normal User</h2>

1. **On Client-1 (Normal User) Access:**
   - On Client-1, open **Run** (Press `Windows + R`).
   - In the **Run** box, type: `\\dc-1` and press **Enter**.
   - You should see the list of shared folders on DC-1.

2. **Check Access to Each Folder:**
   - Try accessing each folder:
     - **Read-access folder:** Can you open it? Can you only view files?
     - **Write-access folder:** Can you create, modify, and delete files in this folder?
     - **No-access folder:** Can you access it? (You should not be able to access it as a normal user.)
