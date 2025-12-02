# Windows 11NE (Neo Edition)

A practical Windows 11 cleanup, stability, and performance guide  
for **gamers, VTubers, streamers, and creators**.

## ⚠️🚨⚠️  BEFORE WE START  ⚠️🚨⚠️

If you’re wondering why Linux or other Windows variants aren’t covered here,  
I’ve written a short FAQ explaining the scope and reasoning behind this guide.

➡️ Please read the [FAQ](faq.md) before opening issues or discussions.

## Start Here – Choose Your Path

I’ll keep this as simple and straightforward as possible.

The **cleanest and safest** way to end up with a stable Windows 11 system is:
1. Back up your data  
2. Perform a clean reinstall  
3. Set the system up correctly from the start  

That said not everyone wants to wipe their system.

Instead of forcing one approach, this guide is broken into **clear pathways**.

👉 Click the option that matches your situation.

---

### 🔹 Path 1 – Windows 11 (No Reinstall)
**You are already running Windows 11 and want to clean things up without reinstalling.**

➡️ [Path 1 – Windows 11 (No Reinstall)](paths/path-1-win11-no-reinstall/README.md)

---

### 🔹 Path 2 – Windows 11 (Clean Install)
**You are already on Windows 11 and are okay starting fresh.**

➡️ [Path 2 – Windows 11 (Clean Install)](paths/path-2-win11-clean-install/README.md)

---

### 🔹 Path 3 – Windows 10 → Windows 11
**You are currently running Windows 10 and planning to upgrade.**

➡️ [Path 3 – Windows 10 → Windows 11](paths/path-3-win10-to-win11/README.md)

---

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

---

## Disclaimer

This project is provided **as-is**.

You are responsible for:
- Your data
- Your hardware
- Understanding what you run

If you don’t understand a step:
- Stop
- Read
- Ask questions before proceeding

---

**Windows 11NE**  
Built for creators who need their systems to work not argue with them. 💙
