# Active Directory Home Lab

### *Complete Setup Guide*

This lab sets up a Windows Active Directory environment consisting of three virtual machines:

- 1 x Domain Controller (DC) — Windows Server 2022
- 2 x Workstations — Windows 11 Enterprise

### ISO Download: 
https://www.microsoft.com/en-gb/evalcenter/

---

## Contents

- [Part 1: Domain Controller Setup](#part-1-domain-controller-setup)
- [Part 2: Windows 11 Enterprise Workstations](#part-2-windows-11-enterprise-workstations)
- [Part 3: AD Users, Groups & Policies](#part-3-ad-users-groups--policies)
- [Part 4: File Share & Service Account SPN](#part-4-file-share--service-account-spn)
- [Part 5: Joining Workstations to the Domain](#part-5-joining-workstations-to-the-domain)
- [Part 6: Set Up Local Administrators on Workstations](#part-6-set-up-local-administrators-on-workstations)
- [Part 7: Map Network Drive on Spiderman Machine](#part-7-map-network-drive-on-spiderman-machine)

---

## Credentials Reference

| Machine / Account | Username | Password |
|---|---|---|
| DC — Administrator | `Administrator` | `l@$$w0rd!` |
| DC — Domain Admin | `MARVEL\Administrator` | `P@$$w0rd!` |
| DC — Tony Stark (Admin) | `tstark` | `Password12345` |
| DC — SQLService (SVC) | `SQLService` | `MyPassword123#` |
| DC — Frank Castle (User) | `fcastle` | `Password1` |
| SPIDERMAN — Peter Parker | `peterparker` | `Password1` |
| THEPUNISHER — Frank Castle | `frankcastle` | `Password1` |
| (Local) Administrator | `Administrator` | `P@$$w0rd1!` |

**Domain:** `marvel.local` | **DC:** `HYDRA-DC`

---

## Part 1: Domain Controller Setup

**Machine:** `HYDRA-DC` | **OS:** Windows Server 2022 Desktop Experience

### Step 1 — Initial Installation

- **Download:** Windows Server 2022 ISO
- **Edition:** Windows Server 2022 Desktop Experience
- **Administrator Password:** `l@$$w0rd!` *(weak password that meets minimum requirements)*

### Step 2 — Basic Configuration

1. Allow network to be discoverable: select **Yes**
2. Rename PC to `HYDRA-DC`
3. Restart

### Step 3 — Install Active Directory Domain Services (AD DS)

> ⚠️ This promotes the server to a Domain Controller.

1. Open **Server Manager** > **Manage** > **Roles & Features**
2. Next > **Role-based or Feature-based installation** > Next
3. Select destination server: `HYDRA-DC` > Next
4. Add Features > Next > Next > Next
5. Check **Restart the destination server automatically if required** > Install
6. After install: click **Promote this server to a domain controller**
7. Select **Add a new forest** > Root domain name: `marvel.local` > Next
8. DSRM Password: `P@$$w0rd!` > Next
9. Next (No DNS delegation) > Wait for NetBIOS name to populate as `MARVEL`
10. Next > Next > Next > Install > Close *(server will restart)*

### Step 4 — Set Up Certificate Authority (LDAPS)

> ⚠️ Log in as `MARVEL\Administrator` / `P@$$w0rd!` for this step.

1. Manage > Roles & Features > Next > Next > Next
2. Select **Active Directory Certificate Services** > Add Feature > Next > Next > Next > Next
3. Check **Restart the destination server automatically if required** > Yes > Install
4. Click **Configure Active Directory Certificate Services**
5. Next > **Certificate Authority** > Next > Next > Next
6. Create new private key > `SHA256`
7. Validity period: `90` years > Next
8. (Cert logs) > Next > **Configure** > Close > Restart

---

## Part 2: Windows 11 Enterprise Workstations

Install 2 x Windows 11 Enterprise (60GB each) with the following settings:

| | THEPUNISHER | SPIDERMAN |
|---|---|---|
| **Local User** | `frankcastle` | `peterparker` |
| **Password** | `Password1` | `Password1` |
| **Security Q** | Bob | bob |
| **Telemetry** | Skip | Skip |
| **Rename PC** | `THEPUNISHER` | `SPIDERMAN` |

---

## Part 3: AD Users, Groups & Policies

> ⚠️ Perform all steps below logged in to the DC as `MARVEL\Administrator`.

### Step 1 — Organise AD Structure

1. Tools > **Active Directory Users and Computers** > `marvel.local`
2. Under `Users`: right-click > **New > Organisational Unit** > name it `Groups`
3. Move all **Security Group** type objects from the `Users` folder to the `Groups` folder

### Step 2 — Create Admin Account (Tony Stark)

1. In Users tab > right-click **Administrator** account > **Copy**
2. First Name: `Tony` | Last: `Stark`
3. User logon name: `tstark` > Next
4. Password: `Password12345` > check **Password never expires** > Next > Finish

### Step 3 — Create Service Account (SQLService)

1. Copy Administrator account again > First Name: `SQL` | Last: `Service`
2. User logon name: `SQLService` > Next
3. Password: `MyPassword123#` > Next > Finish
4. Double-click the `SQLService` account > type the password in the **Description** field > Apply > OK

### Step 4 — Create Low-Level User (Frank Castle)

1. Right-click whitespace > **New > User**
2. First Name: `Frank` | Last: `Castle` | Logon: `fcastle`
3. Password: `Password1` > Next > Finish

---

## Part 4: File Share & Service Account SPN

### Step 1 — Create a File Share

1. Server Manager (right side) > **File & Storage Services** > **Shares** > Tasks > **New Share**
2. SMB Share Quick > Next > Share Name: `hackme` > Next > Next > Next > **Create** > Close

### Step 2 — Complete Service Account SPN Setup

1. Start > CMD > **Run as Administrator**
2. Run the following command:
    ```
    setspn -a HYDRA-DC/SQLService.MARVEL.local:60111 MARVEL\SQLService
    ```
3. Query SPN to verify:
    ```
    setspn -T MARVEL.local -Q */*
    ```

### Step 3 — Disable Windows Defender via Group Policy

#### Create the GPO

1. Start > **Group Policy Management** > Forest: `marvel.local` > Domains > `marvel.local`
2. Right-click > **Create a GPO in this domain** > Name: `Disable Windows Defender` > OK
3. Right-click the new GPO > **Edit** > Computer Configuration

#### Configure the Policy

1. Policies > Administrative Templates > Windows Components > **Microsoft Defender Antivirus**
2. Open **Turn off Microsoft Defender Antivirus** > Edit > **Enable** > Apply > Close Editor

#### Enforce the GPO

1. In Group Policy Management > right-click `Disable Windows Defender` > **Enforce**

---

## Part 5: Joining Workstations to the Domain

### Step 1 — Set Static IP & DNS on Each Workstation

1. Power on all 3 machines and log in to THEPUNISHER and SPIDERMAN
2. On the **DC**: Start > Network Status > Change Adapter Options > right-click Ethernet > Properties > IPv4 > Properties — note the current IP address
3. On **THEPUNISHER & SPIDERMAN**: Start > Network Status > Change Adapter Options > right-click Ethernet > Properties > IPv4 > Properties
4. Set DNS to the Domain Controller's IP address (e.g. `192.168.122.44`)

### Step 2 — Join Domain (on both THEPUNISHER and SPIDERMAN)

1. Start > **Access Work or School** > Connect > **Join device with local Active Directory**
2. Domain: `MARVEL.local`
3. Credentials: `administrator` / `P@$$w0rd!`
4. Account type: **Administrator** > Next > Restart

### Step 3 — Verify Connections on DC

1. Tools > **Active Directory Users and Computers** > `marvel.local` > **Computers**
2. Confirm both `THEPUNISHER` and `SPIDERMAN` appear as connected

---

## Part 6: Set Up Local Administrators on Workstations

> ⚠️ Perform on both SPIDERMAN and THEPUNISHER. Log in as `MARVEL\Administrator` / `P@$$w0rd!`

### Enable & Set Password for Local Administrator

1. Start > **Edit local users and groups** > Users
2. Right-click **Administrator** > **Set Password** > `Password1!` > OK
3. Right-click **Administrator** > Properties > **Enable Account**

### Add fcastle to Administrators Group

1. Start > Edit local users and groups > **Groups** > **Administrators** > Add
2. Add `fcastle` > Apply > Check

### Turn On File & Network Discovery

1. File Explorer > Network > turn **Network Discovery On**
2. You should see `HYDRA-DC` appear in Network

### SPIDERMAN — Add Additional User to Administrators

1. Start > Edit local users and groups > Users > right-click **Peter Parker** > Member of > Add
2. Add to **Administrators** group > Apply

### Verify Share Drive

- Access share via: `\\HYDRA-DC\hackme`

---

## Part 7: Map Network Drive on Spiderman Machine

### Sign In & Map Drive

1. Sign in to the SPIDERMAN machine as `SPIDERMAN\peterparker` / `Password1`
2. File Explorer > This PC > Computer > **Map Network Drive**
3. Drive letter: `Z:` | Path: `\\HYDRA-DC\hackme`
4. Check **Reconnect at sign-in** and **Connect using different credentials**
5. Credentials: `administrator` / `P@$$w0rd!`

---

## Full Credentials Summary

| Machine / Account | Username | Password |
|---|---|---|
| DC — Administrator | `Administrator` | `l@$$w0rd!` |
| DC — Domain Admin | `MARVEL\Administrator` | `P@$$w0rd!` |
| DC — Tony Stark (Admin) | `tstark` | `Password12345` |
| DC — SQLService (SVC) | `SQLService` | `MyPassword123#` |
| DC — Frank Castle (User) | `fcastle` | `Password1` |
| SPIDERMAN — Peter Parker | `peterparker` | `Password1` |
| THEPUNISHER — Frank Castle | `frankcastle` | `Password1` |
| (Local) Administrator | `Administrator` | `P@$$w0rd1!` |
