# DaVinci Resolve Cloud Collaboration – Beginner’s Fast Guide

## What Is DaVinci Resolve Cloud Collaboration?
In short, it lets multiple users access the same **Project Library** simultaneously.  
The project data (timelines, metadata, markers) is stored in a database, while media files are kept locally or on the cloud for each user.

There are three main modes:
- **Local Database** – for solo use only  
- **Network Project Server** – collaboration on the same LAN  
- **Blackmagic Cloud Project Library** – full online collaboration across regions  

---

## 1. Preparation
1. Install **DaVinci Resolve 18 or later**  
2. Sign up for and log in to **Blackmagic Cloud**: [https://cloud.blackmagicdesign.com](https://cloud.blackmagicdesign.com)  
3. Choose your storage option:  
   - Cloud drives: Google Drive / Dropbox / OneDrive  
   - NAS storage: Synology / QNAP  
   - Portable drive for offline use  

---

## 2. Single-User Workflow: Syncing Projects Across Devices
### Goal
Work seamlessly between your desktop and laptop while keeping your projects in sync.  

### Method 1: Use Blackmagic Cloud
1. In Resolve, go to **Project Manager → Create New Library → Cloud**.  
2. Log in to Blackmagic Cloud and create a new Project Library (about $5/month).  
3. Create and save your project on Computer A.  
4. On Computer B, log in to the same account → open the same Cloud Library → project syncs automatically.  

**Pros:** True cloud sync; no manual transfers needed.  
**Cons:** Only project data is synced, not media files.  

**Media sync tips:**
- Store your media on Google Drive or a NAS and keep the same folder path on both devices.  
- Use **“Relink Media”** in Resolve to reconnect media quickly.  

### Method 2: Use a Cloud Drive (Offline Alternative)
1. On Computer A, go to  
   `C:\Users\<Username>\AppData\Roaming\Blackmagic Design\DaVinci Resolve\Support\Resolve Disk Database\Resolve Projects`  
   Copy the entire project folder to your cloud drive (e.g. Dropbox).  
2. On Computer B, paste it into the same path.  
3. Launch Resolve; the project appears automatically.  

**Note:** Ensure the cloud drive has finished syncing before closing Resolve.

---

## 3. Team Collaboration: Multiple Editors on One Project
### Goal
Allow multiple editors to cut, grade, and add effects on the same project from different locations.  

### Method 1: Blackmagic Cloud Project Library (Recommended)
1. Admin logs into [Blackmagic Cloud](https://cloud.blackmagicdesign.com).  
2. Click “Create Library,” name it, and enable paid access.  
3. Add collaborators by their email (they must have a Blackmagic ID).  
4. Collaborators log in with the same ID → open the shared Library in Project Manager.  
5. Right-click the project and select “Collaborate.”  
6. Inside the project, you’ll see:  
   - “Locked” icons to prevent simultaneous editing of the same section  
   - Real-time chat  
   - Shared markers and comments  

**Logic:**  
- Project data updates live through the cloud.  
- Each user keeps local or shared access to the same media folder.  

### Method 2: Use Project Server (LAN or NAS)
1. Install **DaVinci Resolve Project Server** (free).  
2. Create a shared database and enable “Share” permission.  
3. Open ports on your LAN or NAS for connections.  
4. Each user in Resolve: **Project Manager → Connect → Enter Server IP**.  
5. Everyone can now work simultaneously.  

**Best for:**  
Teams in the same office, studio, or campus network. Not suitable for remote use.  

---

## 4. Hybrid Mode: NAS + Cloud Project
### Scenario
You want to keep large media files off the cloud but still sync project data.  

### Recommended Setup
- **Project Library:** Blackmagic Cloud (lightweight)  
- **Media:** NAS storage (large capacity)  
- **Cache/Proxies:** Local drive (fast access)  

**Steps:**
1. Create the project on the Cloud Library.  
2. Create a shared NAS folder, e.g., `\\NAS\MediaPool`.  
3. On each computer, go to **Preferences → Media Storage**, add the same path mapping.  
4. Enable “Use Relative Paths” in Project Settings.  
5. Everyone connects to the NAS to access shared media.  

---

## 5. Solo Version Management
### Auto Backups
- Resolve saves project history automatically.  
- Enable it in **Project Settings → Project Backups**.  
- Right-click any project → “Project Backups” to view or restore previous versions.  

### Manual Version Naming
Use clear version tags:
- `Film_Cut_v1`, `Film_Cut_v2`, `Film_Color_v1`  
- Export `.drp` backup files to your cloud drive regularly.  

---

## 6. Working on Different Devices & Offline Editing
### Example: Editing While Traveling
1. On your main PC, export `.drp` (without media) or `.drb` (with library structure).  
2. Copy media to a portable drive.  
3. On your laptop, open `.drp` and relink media.  
4. After editing, export the new `.drp` and import it back on your main PC.  

### Pro Tip: Use Proxy Files
1. Generate low-res proxies on your main system.  
2. Upload proxies to a cloud drive.  
3. Download only the proxies on your laptop.  
4. After editing, export XML or DRP and relink with original media on your main machine.  

---

## 7. Common FAQ
**Q: Why can’t I open the project?**  
A: Check that all collaborators use the same Resolve version (preferably the latest).  

**Q: Media shows as offline?**  
A: Go to Project Settings → Relink Media → Choose correct folder.  

**Q: What if two people edit the same timeline?**  
A: Resolve automatically locks Bins and Timelines; rig

