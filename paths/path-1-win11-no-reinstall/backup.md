## Universal Rule – Backup First (No Exceptions)

Every path in this guide begins with **backup steps**.

Before making *any* changes:
- Create a **System Restore Point**
- Back up important files to an **external device**

If you skip backups, that risk is on you.

---

## Backup Layer 1 – System Restore Point

A restore point allows you to roll back:
- Registry changes
- Driver installs
- System configuration changes  

It does **not** back up personal files.

### How to Create a Restore Point

1. Open **Start**
2. Search for **Create a restore point**
3. Open it
4. Ensure protection is **On** for the system drive
5. Click **Create**
6. Name it something clear (example): Before Windows 11NE Changes

If Protection is **Off**:
1. Select the system drive (`C:`)
2. Click **Configure**
3. Select **Turn on system protection**
4. Set **Max Usage** to at least **5–10%**
5. Click **Apply**
6. Click **OK**

System Protection is now enabled.

---

## Backup Layer 2 – External File Backup

The most important data lives here:

`C:\Users\<your-username>\`


You can back up just your user folder or the entire `Users` directory.

This will include:
- Desktop
- Documents
- Downloads
- Pictures / Videos / Music
- Most application data
- Many game save locations

Some applications **do** store data inside `Program Files`, but that data:
- Must be **identified per application**
- Cannot simply be copied back or “merged” into a new OS

Most modern software stores important user data inside **AppData**, which is already contained within your user folder.
