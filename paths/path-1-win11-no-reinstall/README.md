# Path 1 – Windows 11 (No Reinstall)

## ⚠️⚠️⚠️ Before You Continue ⚠️⚠️⚠️

Every step in this path assumes your data is protected.

Before touching drivers, cleanup steps, or system configuration:
- You **must** create a system restore point
- You **must** back up important files externally

If you skip backups, that risk is on you.

➡️ **Complete the backup steps here before continuing:**  
[How to Backup](backup.md)

---

## Step 1 – Update Windows

### What to Do

1. Open **Settings** → **Windows Update**.
2. Click **Check for updates**.
3. Install everything under:
   - **Important / Security / Cumulative updates**
4. If you see **“Restart required”**, restart the PC.
5. After reboot, go back to **Windows Update** and click **Check for updates** again.
6. Repeat this cycle until Windows reports:
   - “You’re up to date.”
7. (Optional) Click **Advanced options → Optional updates**:
   - You may install **.NET updates** and **firmware**.
   - **Do not** install random driver updates here if you plan to use vendor drivers in Step 3.

### Why We Do This

- Many weird issues vanish once the OS is fully patched.
- Servicing stack, Windows Update client, and .NET all get patched.
- You don’t want to troubleshoot a problem that Microsoft already fixed.

This gives us a **known, supported baseline** before we touch anything else.

---

## Step 2 – OS Integrity Verification (DISM + SFC)

We’re checking that Windows itself isn’t corrupted from past upgrades or crashes.

> Run these commands in an **elevated** (Admin) terminal.

### 2.1 Open an Elevated Terminal

1. Right-click the **Start** button or you can press **WINDOWS KEY** and **X**.
2. Choose **Windows Terminal (Admin)** or **Command Prompt (Admin)**.
3. Accept the UAC prompt.

### 2.2 Run DISM

In the terminal window, type:

```cmd
DISM /Online /Cleanup-Image /RestoreHealth
```

Press Enter and wait. This can take a while (5–20 minutes).
When it finishes, you should see something like “The restore operation completed successfully.”

⚠️ Restart your PC after DISM completes.

2.3 Run SFC

After reboot, open an admin terminal again and run:

```cmd
sfc /scannow
```
Let it reach **100%**.

- If it says it **found and repaired files** → ✅ good  
- If it says it **couldn’t fix some files** → ⚠️ note it, but continue with the guide  
  (You may re-run after completing all steps)

---

## Why We Do This

- **DISM** repairs the underlying Windows image  
- **SFC** repairs system files on top of that image  

Together, they fix many cases of “Windows feels cursed,” including:
- Random crashes  
- Broken menus  
- Features not opening  

We want to confirm the OS itself is stable **before blaming drivers or applications**.

---

## Step 3 – Driver Validation & Correction

Creators rely heavily on **GPU, audio, and capture hardware**.  
Wrong or generic drivers commonly cause stutters, frame drops, and strange OBS behavior.

We **do not** use driver packs or “driver booster” tools.  
We install drivers directly from trusted sources.

---

### 3.1 GPU Drivers

#### Identify Your GPU

1. Right-click **Start** → **Device Manager** or use **WINDOWS KEY** and **X**
2. Expand **Display adapters**
3. Note the GPU name:
   - NVIDIA
   - AMD
   - Intel

#### Get the Correct Driver

**Laptop or prebuilt desktop**
- Go to the manufacturer’s support page (Dell, ASUS, Lenovo, etc.)
- Search your **exact model**
- Download the latest **Windows 11 graphics driver**

**Custom-built desktop**
- NVIDIA → Official NVIDIA driver download page
- AMD → Radeon driver download page
- Intel → Arc / iGPU driver download page

Install the driver you downloaded and **reboot**.

⚠️ If installing NVIDIA make sure to use the custom install and make sure to select the clean install option. 

---

### 3.2 Chipset / Motherboard Drivers

**For desktops**
1. Go to your motherboard vendor’s support page (ASUS, MSI, Gigabyte, etc.)
2. Download and install:
   - Chipset drivers
   - ME / AM4 / AM5 / Intel Platform drivers (if offered)

**For laptops**
- Use the OEM support page
- Install chipset / platform drivers listed for your model

---

### 3.3 Audio & Capture Card Drivers

Install or update drivers from:
- Your **audio interface** or **sound card** vendor
- Your **USB microphone** vendor (if it uses a driver)
- Your **capture card** vendor (Elgato, AverMedia, etc.)

Reboot after installing drivers.

---

## Why We Do This (Drivers)

- Windows Update often installs **generic drivers** that technically work but perform poorly

Known-good vendor drivers eliminate many:
- Stutter issues
- Random crashes
- “OBS hates me today” problems

Drivers must be correct **before** we start tweaking or disabling anything.

---

## Step 4 – Startup Cleanup (Task Manager)

We’re trimming background noise that slows boot and wastes resources,  
**without touching core system services**.

---

### What to Do

1. Right-click the **taskbar** → **Task Manager**
2. Open the **Startup apps** tab  
   (You may need to click **More details**)
3. Go through and you can disable almost everything on this list unless you know for certain you dont want to

For each item:

**Disable things like:**
- Updaters (Adobe Updater, game launchers you rarely use)
- OEM tray apps or RGB software you don’t care about
- “Helper” apps not required for your workflow

**Leave enabled:**
- GPU utilities (NVIDIA / AMD / Intel)
- Audio software (Wave Link, Voicemeeter, interface control panels)
- Capture card software
- Input device drivers (Logitech, Razer, etc., if used)
- Anti-cheat launchers / required game platform services

Right-click → **Disable** anything you don’t need at boot.

You can always re-enable items later.

---

## Why We Do This (Startup)

- Many apps auto-start without asking
- Startup clutter:
  - Slows boot time
  - Consumes RAM and CPU
  - Increases the chance of conflicts

We remove obvious junk **without touching system services yet**.

---

## Step 5 – Service Isolation (`msconfig`)  
### Optional / Advanced

We are performing a **controlled clean boot**, **not** a “disable everything” nuke.

---

### 5.1 Open msconfig

1. Press **Win + R**
2. Type `msconfig`
3. Press **Enter**
4. Under the **General** tab
5. Select Selective Startup (Leave both boxes checked under)
6. Go to the **Services** tab
7. Check **Hide all Microsoft services** (required)

Only third-party services will now appear.

The next part after this you can choose to do one of two ways. You can uncheck everything and go down and select the items in 5.2 one by one and enable them. Or go down and just disable what you know you want to disable but I find the first option better. 

---

### 5.2 What Must Stay Enabled

Even if they’re non-Microsoft, **do NOT disable** services related to:

**Anti-cheat & Games**
- Riot Vanguard
- BattlEye
- Easy Anti-Cheat
- Game launcher helpers (Battle.net, Riot, EA, Steam)

**GPU**
- NVIDIA / AMD / Intel graphics services

**Audio**
- Elgato Wave services
- Voicemeeter
- Sound card / audio interface services

**Capture & Camera**
- Elgato / AverMedia services
- Camera bridge / face-tracking helpers

**Security**
- Third-party antivirus or endpoint protection

If you do not recognize a service, **leave it enabled**.

---

### 5.3 What You May Disable

You may disable services you clearly recognize as:
- Update checkers that don’t need to run constantly
- Telemetry or “experience improvement” services
- Known vendor bloat you never use (OEM helpers, support assistants)

Uncheck only those services, then:

1. Click **Apply**
2. Click **OK**
3. Restart

---

## Why We Do This (msconfig)

Some instability comes from misbehaving third-party services, such as:
- Overlay tools
- OEM junk
- Bad updaters

This step is about **isolating causes**, not optimizing performance.

Because it’s easy to misuse, this step is:
- Optional
- Reversible (re-enable services if something breaks)

---

## Step 6 – Targeted Software Cleanup

With the OS stable and drivers correct, we remove software you genuinely don’t use.

---

### Option A – Built-in Uninstall

1. **Settings → Apps → Installed apps**
2. Sort by:
   - **Name**, or
   - **Install date**
3. Uninstall software you:
   - Don’t recognize (after confirming it’s bloat)
   - No longer use
   - OEM preinstalled junk

---

### Option B – Revo Uninstaller (More Thorough)

If you use Revo:

1. Open **Revo Uninstaller**
2. Select the program
3. Choose **Uninstall**
4. Use a **Advanced** leftover scan
5. Select all items in the registry and all files and  you can delete both sets

---

### What NOT to Remove

Avoid uninstalling:
- .NET runtimes
- Visual C++ Redistributables
- GPU drivers
- Audio drivers
- Game anti-cheat components
- OBS, tracking tools, capture tools  
  (unless you plan to reinstall immediately)

---

## Why We Do This (Cleanup)

Less installed junk means:
- Fewer background tasks
- Fewer conflicts

Removing the wrong items can break games or streaming tools,  
so we only remove **known, unnecessary software**.

---

## Step 7 – Controlled System Tweaks (Fixed Config)

At this point the system is:
- Updated
- Verified
- Using correct drivers
- Cleaned up

Only now do we apply system tweaks.

---

# Windows 11NE – WinUtil Tweaks Profile

This section describes **exactly** how to run Chris Titus Tech’s WinUtil 

Do **not** enable extra options beyond what’s listed here unless you know what you’re doing.

---

## 1. Launch WinUtil

1. Open **PowerShell** or **Terminal** as Administrator  
   - Right-click **Start** → **Windows Terminal (Admin)**

2. Run this command:

   ```powershell
   irm "https://christitus.com/win" | iex
   ```

3. Click on the **Tweeks** tab and select standard and then make your's look how the image below does.

![WinUtil Standard Creator Profile](tweeks.png)

4. Click **Run Tweeks**
5. Click **Run OO Shutup 10**
6. Click **File** and **Import Profile**
7. [Download ooshutup10.cfg](https://raw.githubusercontent.com/HaittaNeo/Windows-11NE/refs/heads/main/paths/path-1-win11-no-reinstall/ooshutup10.cfg)

<a id="raw-url" href="https://raw.githubusercontent.com/HaittaNeo/Windows-11NE/refs/heads/main/paths/path-1-win11-no-reinstall/ooshutup10.cfg">Download FILE</a>

8. Import the downlooaded config file
9. Restart computer after everything has been applied and done

---

## ✅ You’re Done

At this point, your system should be back online, stable, and running cleaner than before.

If you’d like an extra layer of confidence, you may return to the top of this path and run **DISM** and **SFC** one more time to confirm system integrity. This is optional, but it’s a good final check after significant changes.

If everything feels good you’re all set.

If you notice issues:
- Use your **system restore point** to roll back the changes, or  
- Proceed to **Path 2** and follow the clean-install process for a fresh Windows 11 setup.

## Navigation

⬅️ [Back to Main README](../../README.md)
