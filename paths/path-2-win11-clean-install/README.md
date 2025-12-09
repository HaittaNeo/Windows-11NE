# Path 2 – Windows 11 (Clean Install)

This path is for users who are **already on Windows 11** and are comfortable starting fresh.

A clean install provides the **cleanest, most predictable baseline**, but it requires preparation and attention. Read each step carefully.

---

## ⚠️⚠️⚠️ Before You Begin ⚠️⚠️⚠️

This process **will erase the selected system drive**.

Before continuing, make sure you have:
- Completed all backup steps  
- Verified your backups are accessible from another device  
- Read through this path once start to finish  

➡️ **Backup instructions:**  
[How to Backup](../backup.md)

---

## Important Note – Network Drivers

This Windows 11NE install is **stripped down**.  
On some systems, **Wi-Fi drivers may not be available during setup**.

Before you start:

✅ **Strongly recommended**
- Download your **Wi-Fi or Ethernet network drivers**
- Save them to a **separate USB drive**

✅ **Alternative**
- Use a **wired Ethernet connection** during first boot
- You can install drivers immediately after setup

This avoids being stranded offline after installation.

---

## Step 1 – Prepare Installation Media

### What You’ll Need
- A USB flash drive (8GB minimum, 16GB recommended)
- A working Windows system

---

### 1. Download the Windows 11NE ISO

Download **Windows 11NE (25H2)** — a debloated Windows 11 base designed for this guide.

➡️ *(Link to ISO will live here once final)*

---

### 2. Download Rufus

Download Rufus from the official site:

➡️ https://rufus.ie/en/

---

### 3. Create the Bootable USB

1. Launch **Rufus**
2. Select:
   - **Device:** Your USB drive  
   - **Boot selection:** Windows 11NE ISO  
3. Configure Rufus **exactly as shown below**

📸 *(Rufus settings image goes here)*

4. Click **Start**

When prompted with **Windows User Experience options**:
- **Uncheck every box**
- Click **OK**

⛔ Do not enable bypasses or automation options.

Wait for Rufus to complete.

---

## Step 2 – Boot Into the Installer

Once the USB is ready, choose **one** of the following methods:

### Option A – Boot Key (Recommended)
Restart your system and press your boot menu key:

Common keys:
- **F12** – Dell / Lenovo
- **F11** – MSI
- **F8** – ASUS
- **Esc** – HP
- **F9** – Some OEM systems

Select the USB device.

---

### Option B – Advanced Startup (From Windows)

1. Open **Settings**
2. Go to **System → Recovery**
3. Click **Restart now** under Advanced startup
4. Choose:
   - **Use a device**
   - Select your USB installer

---

## Step 3 – Windows 11 Setup

Follow the installer prompts as shown in the images below.

📸 *(Windows installer screenshots go here)*

### Setup Options
- Select **Install Windows 11**
- Check ✅ **I agree that everything will be deleted (files, apps, and settings)**

### Product Key
- When prompted, click:
  **I don’t have a product key**

Windows should activate automatically later.

---

## Step 4 – Disk Selection (READ CAREFULLY)

This is the **most important step**.

Your screen may show:
- Multiple disks  
- Multiple partitions  
- The USB installer  

### What You Need to Do

1. Identify the disk containing your **old Windows installation**
2. Look under the **Type** column for:
   - Recovery
   - System
   - MSR

These partitions will all belong to the same disk  
(e.g., **Disk 0**, **Disk 1**)

3. Select **each partition** on that disk and click **Delete**
4. Continue until the disk shows:
   - **Unallocated Space**

✅ When only unallocated space remains on the target disk:
- Select it
- Click **Next**

⚠️ **Do NOT delete partitions on other disks unless you intend to wipe them.**

---

## Step 5 – Installation & First Boot

Windows will now:
- Copy files
- Reboot multiple times
- Complete setup automatically

Once finished, you’ll enter **OOBE (Out-of-Box Experience)**.

With this stripped-down build:
- You may be prompted for a **username and password**, or  
- A default account may be created  

Either is fine — we’ll adjust later if needed.

---

## Step 6 – First Login & Network Setup

Once on the desktop:
- Connect to the internet (Ethernet or Wi-Fi driver USB)
- Install your network driver if necessary
- Allow initial Windows updates to complete

---

## Step 7 – Proceed With Post-Install Setup

At this point, your system is ready to be configured properly.

➡️ Continue with:
- **Windows Update**
- **Driver installation**
- **System verification**

Follow the same instructions used in **Path 1** for:
- Updates
- DISM / SFC
- Driver order
- WinUtil & O&O configuration

➡️ [Continue with Path-1 Post-Install Steps](../path-1-win11-no-reinstall/README.md)

---

## ✅ After Path 2

You now have:
- A clean Windows 11NE install
- No legacy upgrade issues
- Full control over drivers and configuration

From here, Windows behaves predictably — which is the entire goal of this project.

⬅️ [Back to Main README](../../README.md)
