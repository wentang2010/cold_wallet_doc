# Cold Wallet - En

> A secure, offline cryptocurrency cold wallet application built with Rust and the Iced GUI framework, focused on the Solana ecosystem.

***

## Why Cold Wallet? — The Current State of Asset Security

### Frequent and Severe Wallet Theft Incidents

Cryptocurrency asset theft has surged in recent years, exposing ordinary users to serious security threats:

| Year | Amount Stolen     | Incidents | Notable Events                                             |
| ---- | ----------------- | --------- | ---------------------------------------------------------- |
| 2024 | **$2.2 Billion**  | 303       | Private key compromise accounted for 43.8% of stolen funds |
| 2025 | **$3.4+ Billion** | —         | Bybit exchange $1.5B single theft (largest in history)     |

* **Hot wallet risk**: Hot wallets connected to the internet have an asset loss rate of **4.3%**
* **Individual wallets**: **158,000** individual wallet theft incidents in 2025
* **Private key compromise**: Nearly half of stolen funds in 2024 stemmed from private key leaks or custodial breaches
* **Forgotten mnemonics**: Mnemonics written on paper or in files are usually in plain text, prone to accidental leaks, and paper is more easily damaged.

Keeping assets on exchanges or in hot wallets is essentially exposing private keys to the internet. **This cold wallet is designed to address the asset security pain points of ordinary users**—securely encrypting and storing private keys in an offline environment, eliminating the hassle of memorizing mnemonics, while avoiding the complexity of hardware cold wallet operations.

***

## Advantages and Comparison of This Cold Wallet

### Comparison with Mainstream Solutions

| Dimension             | This Cold Wallet                                              | Hardware Wallets (Ledger/Trezor)              | Exchanges / Hot Wallets                             |
| --------------------- | ------------------------------------------------------------- | --------------------------------------------- | --------------------------------------------------- |
| **💰 Cost**           | Free                                                          | $49–$400 device purchase required             | Free                                                |
| **🔒 Security**       | Dual private key encryption, offline, military-grade security | Offline private keys, secure chip             | Private keys hosted in cloud, vulnerable to hackers |
| **📱 Convenience**    | Desktop GUI, no extra device, simple operation                | Requires carrying hardware, complex operation | Convenient                                          |
| **🔌 Offline**        | Fully supports offline use                                    | Supported                                     | Must be online                                      |
| **⚡ Getting Started** | Download and use, zero barrier                                | Requires purchase, configuration, learning    | Sign up and use                                     |
| **⚠️ DApp Attacks**   | Cannot be attacked                                            | May be attacked                               | Will be attacked                                    |

### Core Advantages

1. **🔐 Security First**
   * Private keys **never touch the network**; fully encrypted locally
   * Military-grade encryption, resistant to brute-force attacks
   * Single instance operation, preventing security risks from multiple instances
2. **📦 Easy to Use**
   * **Free basic version**, no hardware purchase required
   * Modern graphical interface, no command line needed
   * Supports Windows, macOS, Linux—cross-platform
3. **💰 Zero-Cost Entry**
   * Software cold wallet, no $49–$400 hardware investment
   * Suitable for beginners and experienced users who demand assets not be stolen
   * Requires extremely high wallet security, with third-party apps unable to steal assets
4. **🔑 No Mnemonic to Memorize + Military-Grade Security**
   * Users only need to remember one password—**no need to memorize long 12/24-word mnemonics**
   * **Military-grade encryption**—as long as the password is not exposed, offline encrypted data cannot be cracked
   * Even if the encrypted file is accidentally leaked, it is difficult to crack without the password—brute-force resistant algorithms make cracking prohibitively expensive

### Use Cases

* Users who want secure asset storage and **are unwilling to bear hardware wallet costs**
* Users who need **offline storage** for Solana and SPL tokens
* Users who pursue **simple and easy use** and don't want to deal with complex hardware

***

## Project Overview

**Cold Wallet** is a desktop cold wallet application for the Solana blockchain. It uses military-grade encryption to protect your private keys and mnemonics, ensuring assets are stored securely in an offline environment. The app supports private key import, multi-wallet management, token balance queries, transaction signing, and other core features.

### Core Design Principles

* **Security First**: Private keys and mnemonics never touch the network; fully encrypted and stored locally
* **Offline Capable**: Fully supports offline use, suitable for cold storage scenarios
* **User Friendly**: Modern graphical interface with intuitive, simple operations

***

## Features

| Feature                                             | Description                                                                                                |
| --------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| 🔑 **Military-Grade Key Derivation and Encryption** | Brute-force resistant key generation algorithm, industry-standard authenticated encryption for stored data |
| 💾 **Encrypted Offline Storage**                    | Private key pairs encrypted and stored offline, no network connection                                      |
| 🎨 **Modern Interface**                             | Cross-platform desktop app based on Iced GUI                                                               |
| ⚡ **Hardware Acceleration**                         | AES-NI instruction set support for excellent encryption performance                                        |
| 🔒 **Single Instance**                              | Prevents security risks from multiple instances                                                            |

### Supported Blockchains

* **Solana**: Native SOL, SPL tokens (USDT, USDC, etc.)

### Main Modules

* **Wallet Management**: Create, import, backup wallets
* **Mnemonic**: BIP39 standard
* **Token Display**: SOL and SPL token balance queries
* **Transaction Signing**: Offline signing of transaction data
* **Data Persistence**: SQLite local database for encrypted wallet information

***

## User Guide

### I. First-Time Setup

#### 1. Create Master Password

On first launch, you need to create a strong password to protect your encrypted wallet. The password must: be at least 8 characters, include uppercase and lowercase letters and numbers, and you must agree to the terms of service.

![Create Master Password](../assets/create_password-9018e9d7-28e6-4268-a15f-628719b72a7e.png)

#### 2. Wallet Setup

Choose "Generate New Wallet" or "Import Wallet File" to complete initialization.

* **Generate New Wallet**: Proceed to the key generation flow
* **Import Wallet File**: Select existing `xxx_secure_meta.data` file to import

#### 3. Generate Key Files (for new wallets)

Complete key generation and saving in three steps:

1. **Generate**: Click "Step 1: Generate New Key Files" to locally generate two encrypted files
2. **Save**: Save the files to a secure location (USB flash drive recommended); **store the two files separately** (`xxx_secure_private_key` and `xxx_secure_meta.data`)
3. **Continue**: After saving, proceed to the main interface

![Generate Key Files](../assets/generate_key_files-31076c48-ea1c-4cfe-ba85-46eaeb77975b.png)

> ⚠️ **Important**: Currently only Solana network is supported. Losing either key file will result in unrecoverable assets.

***

### II. Daily Usage

#### 1. Login

Existing wallet users can log in by entering the master password.

![Login](../assets/login-40cb4979-8953-4bf7-b527-f43e5a534f30.png)

#### 2. Home

The home screen displays the current wallet address, asset list, and Receive / Send entries.

* **No Key**: Indicates the private key is not loaded; you can view the address and balance but **cannot send**
* **Key Loaded**: Private key is loaded; you can perform send operations

![Home](../assets/home-22d9a247-8de3-4eed-acd9-11ea2eb34e88.png)

#### 3. Keys Management

* **Not Loaded**: Click "Load Key" and select the `xxx_secure_private_key` file to load
* **Loaded**: Shows green "Key Loaded"; click "Unload Key" to unload (clears sensitive information)

![Key Loaded](../assets/key_loaded-577a4bb6-dafa-4149-a46d-84cf8e044c65.png)

> You must load the key before sending assets. If you click Send on the home screen without loading, you will be redirected to the Keys management page.

#### 4. Wallet Management

Create new wallets, import wallet files, and view the list of loaded wallets and their balances.

![Wallet Management](../assets/wallet_management-97e34b8a-1890-4b7d-b88c-9791974d0328.png)

#### 5. Receive

Displays the wallet address as a QR code and text; you can copy the address. **No key loading required** to receive.

![Receive](../assets/receive-f4f349c7-59f6-498e-ab68-e2fe430482b6.png)

> Only Solana (SOL) and SPL tokens can be sent to this address.

#### 6. Send

Select a token, enter the recipient address and amount, then click Send. Note:

* **Key must be loaded** to send; please load it in the Keys management page
* The wallet reserves approximately 0.01 SOL for transaction fees
* Use the Max button to fill in the maximum sendable amount

![Send](../assets/send-5be203ea-1cd6-4a2f-b1c5-6df3fca4ae23.png)

#### 7. Profile

View/edit wallet name, version info, and log out.

![Profile](../assets/profile-b4a8bf54-c170-42a7-9de7-e68f9fd8b65e.png)

***

### III. Forgot Password

The password is stored encrypted locally and **cannot be recovered**. If you forget your password, you can only clear all data via "Delete Password and Clear All Data", then re-import using your backed-up private key files.

![Forgot Password](../assets/reset_password-cd03bbce-379b-4b48-bf1f-ff6e7ddd1370.png)

> ⚠️ **Confirm before proceeding**: You must have safely backed up both private key files (`xxx_secure_meta.data` and `xxx_secure_private_key`), otherwise you will permanently lose access to your assets.

***

### Software Installation

window version will come soon.
[macOS 下载](https://github.com/wentang2010/cold_wallet_doc/releases/download/v0.3.0/Cold_Wallet-0.3.0.dmg)

***

### Security Features

* ✅ **Confidentiality**: Military-grade encryption
* ✅ **Integrity**: GCM mode prevents data tampering
* ✅ **Authenticated Encryption**: Verifies both ciphertext and associated data
* ✅ **Brute-force Resistance**: Brute-force resistant algorithms increase cracking cost
* ✅ **Memory Safety**: Uses zeroize to clear sensitive data—even if the machine is compromised with malware, sensitive data cannot be extracted from memory

***

## Security Recommendations

### ✅ Recommended Practices

1. **Use a strong password**: At least 8 characters with uppercase, lowercase, numbers, and symbols
2. **Back up regularly**: Store encrypted files on multiple offline media
3. **Verify backups**: Periodically test that backups can be decrypted successfully

### ❌ Practices to Avoid

1. ❌ Do not transmit private keys on networked devices
2. ❌ Do not store private keys in internet cloud storage
3. ❌ Do not use weak or common passwords
4. ❌ Do not store dual encryption files in the same location; back up dual private keys separately

***

## Frequently Asked Questions (FAQ)

### 1. Why doesn't the balance show?

Please ensure you can access the Solana network. If you cannot access it, please use a VPN.

### 2. If one of the two private key pairs is accidentally exposed, are the assets safe?

If only one of the private keys is exposed, the assets are not at security risk. However, it is recommended to create a new wallet and transfer assets to ensure no private key is exposed.

### 3. Will there be fees in the future? Does it affect me?

More value-added services will be introduced in the future, but the free version features will be permanently available. No need to worry.

### 4. How to reset if I forget the password?

The official service does not store any sensitive user data. If you forget your password, you can reset it by following these steps:

1. Click "Forget Password" on the login page to clear wallet data, which will automatically take you to the create master password screen.
2. Set a new password.
3. Select "Import Wallet" and choose your previously backed-up meta file (e.g., `xxx_secure_meta.data`). You will then be taken to the Home page, and you can log in with this password from now on.

### 5. What happens if I lose the private key files?

The two private key files are `xxx_secure_meta.data` and `xxx_secure_private_key`.

1. If you lose `xxx_secure_private_key`, you will lose control of your wallet assets and cannot perform transfers or other signing operations.
2. If you lose `xxx_secure_meta.data` and you have deleted the wallet data (unable to log in to the wallet Home page), you will also lose control of your assets. If you can log in to the wallet normally and see the wallet balance, even if you have lost `xxx_secure_meta.data`, you can still transfer assets to a new wallet address using `xxx_secure_private_key`.

***

## Disclaimer

Users assume all risks when using this software to store cryptocurrency assets. The author is not responsible for any loss of assets. Be sure to back up your data and keep your password safe!

> **🔐 Remember: Your private key is everything. Protect your password and backups!**
