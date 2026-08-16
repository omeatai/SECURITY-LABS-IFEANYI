# Client-Server Basics — Lab sample

> **Room:** [Client-Server Basics](https://tryhackme.com/room/clientserverbasics)

## Introduction

**HTTP GET** is how a browser (the client) asks a web server for a resource. This lab starts the room machine, opens Firefox, and uses **Developer Tools → Network** to inspect scheme, host, filename, address, and status on a local demo site.

## Technologies and tools used

| Piece                         | Role                                              |
| ----------------------------- | ------------------------------------------------- |
| **Lab machine**               | Split-view desktop with Firefox and the demo site |
| **Firefox Developer Tools**   | Inspect request/response fields                   |
| **HTTP GET**                  | Retrieve a resource; lab focus method             |
| **`http://httpdemo.local:8080`** | Local demo host used in the room               |

<details>
  <summary>Lab</summary>

## Lab

This is a **browser Network-inspector** walkthrough on the TryHackMe lab machine. Pause until the machine is on and the split view is visible.

### **Overview**

- [ ] Inspect a real **GET** request and its response on the demo site.
- [ ] You will:
  - [ ] Start the lab machine and open Firefox.
  - [ ] Open Developer Tools → **Network** and reload the page.
  - [ ] Read scheme, host, filename, address, and status on the first GET.
  - [ ] Open the **Response** tab to see the HTML body.
- [ ] Success: you can name the host and scheme in `https://www.iamlearning.thm/contact` and you have seen a **200 OK** GET.

### **Task 1: Start the lab machine**

- [ ] Click **Start Lab Machine** (or **Start Split-screen** if the pane is hidden).
- [ ] Wait until the machine status is **On**.
- [ ] Confirm the desktop is visible in the split view.

### **Task 2: Open the demo site in Firefox**

- [ ] Click the **Firefox** icon on the lab desktop.
- [ ] Confirm the address bar shows `http://httpdemo.local:8080`.
- [ ] If it does not, type that URL and press Enter.

### **Task 3: Open Developer Tools on the Network tab**

- [ ] Press **F12**, or right-click the page and choose **Inspect**.
- [ ] Click the **Network** tab.
- [ ] Reload the page (circular reload control next to the address bar).
- [ ] Confirm multiple **GET** rows appear in the Network list.

### **Task 4: Inspect the first GET**

- [ ] Click the **first GET** entry.
- [ ] In the right-hand panel, note:
  - [ ] **Scheme** — HTTP or HTTPS
  - [ ] **Host** — name of the host you requested
  - [ ] **Filename** — file requested; `"/"` maps to `index.html`
  - [ ] **Address** — IP of the host (lab example: `127.0.0.1` when hosted locally)
  - [ ] **Status** — success indicator (example: **200 OK**)

### **Task 5: Read the response body**

- [ ] With the same GET selected, open the **Response** tab.
- [ ] Confirm the body is the **HTML** of the index page.
- [ ] Remember: the response has a **header** (metadata) and a **body** (content).

Successfully inspected a client GET and a server response in Firefox Developer Tools.

</details>
