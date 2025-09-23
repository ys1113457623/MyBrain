---
tags:
  - SystemDesign
created:
  - 2025-01-12
review: 2025-01-12
---
## 📅 Date:  
**Sunday, January 12th 2025**  

## 🎯 Learning Objective:  
**What’s the goal for learning this concept?**  
- [x] Whats is the internal working on AIRTAGS
- [x] What is BLE(Bluetooth Low Energy) https://en.wikipedia.org/wiki/Bluetooth_Low_Energy
- [x] What is [elliptic curve cryptography](https://blog.cloudflare.com/a-relatively-easy-to-understand-primer-on-elliptic-curve-cryptography/)
- [x] What is **[Ultra Wideband](https://en.wikipedia.org/wiki/Ultra-wideband)**

---

## 🔑 Key Points (Dynamic):  

### 1. Setting up AirTag
```
- Airtag doesn't use GPS, Wifi or cellular network
- It uses BLE ( Bluetooth low energy )
- They generate public private key using elliptic curve crytography this key value pair is shared between user account and airtag
```

### 2. Broadcasting AirTag’s Location

**1. AirTag Behavior When Not Near Your iPhone**

• Continuously broadcasts its **Bluetooth Low Energy (BLE)** signal.
• The signal includes a unique, encrypted identifier.

**2. Role of the “Find My” Network**

**What is the “Find My” Network?**

• A **crowd-sourced system** consisting of millions of Apple devices (e.g., iPhones, iPads, Macs).
• Enables tracking even when the AirTag is far from your iPhone.

**How It Works**

1. **Broadcasting Signal**:

• The AirTag emits a **Bluetooth beacon** with its encrypted identifier.

2. **Relaying Location**:

• Nearby Apple devices detect the signal and send the AirTag’s location to Apple’s servers.
• This process is:
• **Anonymous**: The relaying device owner is unaware of the detection.
• **Encrypted**: Only the AirTag owner can see the location.

3. **Updating the Location**:

• The updated location is shown in the **Find My app** on your iPhone.

**3. Lost Mode**

**What Happens When Lost Mode is Enabled?**

• The AirTag broadcasts an additional **NFC (Near Field Communication)** signal.
• If someone taps the AirTag with a smartphone:
• A notification appears with your contact information (if set in Lost Mode).
• Location updates continue through the **Find My network**.

**4. Privacy and Security**

  **Key Features**

• **Anonymous Data Exchange**:

• The relaying device doesn’t know which AirTag it detected.
• Location data is encrypted so only the owner can view it.

• **Rotating Identifiers**:

• The AirTag changes its Bluetooth identifier frequently to prevent long-term tracking.

**5. If No Apple Devices Are Nearby**

• The AirTag’s location won’t update until another Apple device comes within range.
• You’ll only see the **last known location** in the **Find My app**.

**6. Interaction with Non-iPhone Users**
• Non-iPhone users can tap the AirTag with an **NFC-enabled phone**.
• This opens a webpage showing:
• A message or phone number you set in **Lost Mode**.

  **7. Anti-Stalking Features**
• If an AirTag not registered to the person is traveling with them:
• Apple devices will notify them after a prolonged period.
• The AirTag will emit a sound if it stays with them too long.

  **8. Summary Workflow**
1. AirTag sends out a **Bluetooth signal** with a unique identifier.
2. Nearby Apple devices detect the signal and send the AirTag’s location to Apple’s servers.
3. The location is updated in the **Find My app** for the AirTag owner.
4. In Lost Mode, the AirTag also broadcasts an **NFC signal** for anyone who finds it.

### 3. What Is BLE(Bluetooth Low Energy)
**Bluetooth Low Energy (BLE)** is a wireless communication technology designed for **low-power, short-range communication**. It’s a subset of Bluetooth, specifically optimized for devices that require minimal energy consumption while still providing efficient data transfer over short distances.

**Key Features of BLE**
1. **Low Power Consumption**
2. **Short Range** ( 10 - 30m )
3. **Efficient Data Transfer**
4. **Connection Modes**
	1. Connected Mode: Establishes a direct link between 2 devices
	2. Broadcast Mode: Sends signals to any nearby devices that can receive them
5. **Interference Handling** ( BLE uses a technology called **frequency hopping** to switch between channels, reducing interference from other wireless devices. )
 
![[Screenshot 2025-01-12 at 8.01.27 PM.png]]


### 4. What Is **Ultra-Wideband (UWB)**?
Ultra-Wideband (UWB) is a wireless communication technology that uses **radio waves** over a wide frequency range to enable **highly accurate distance and directional tracking**. Unlike Bluetooth or Wi-Fi, which use narrow frequency bands, UWB spreads its signal over a very broad spectrum, making it ideal for precise location tracking and low-latency communication.