 **Here's the complete README file, incorporating all information and addressing potential redundancies:**

# Offline Payment Transaction iOS App

**Overview**

This iOS Xcode project demonstrates a secure method for conducting offline payment transactions between users. It utilizes encryption and Apple's Secure Enclave to protect sensitive data, enabling transactions even without a constant internet connection.

**Key Features**

* Offline transaction processing
* Secure storage of balance and index data using the Secure Enclave
* Encryption with elliptic curve keys
* Digital signature verification
* Offline balance download and verification
* Offline balance transfer

**Getting Started**

1. **Clone the project:**

   ```bash
   git clone https://github.com/AVSaiKumar/OfflineXcode.git
   ```

2. **Open the project in Xcode:**

   - Open the `OfflineService.xcodeproj` file.

3. **Run the project:**

   - Click the "Run" button to launch the simulator.

<img src="ss1-intro.png" alt="Alt Text" width="400"/>

**4. Understanding the UI Screen**

The user interface displays key information about your wallet and transactions:

- Public Key: This is your wallet's unique identifier, used for secure transactions.
- Balance: This reflects your current available funds, updating as you send and receive payments.
- OnIndex (Online Index): This number increases each time you successfully add a token from the central server. It helps prevent replay attacks, ensuring transactions aren't duplicated.
- OffIndex (Offline Index): This number increases when you send tokens to others or receive and verify tokens offline. It similarly protects against replay attacks during offline transactions.

Key Points:

   - Both OnIndex and OffIndex play crucial roles in transaction security.
   - Their increments safeguard against unauthorized transaction duplication.


**Key Functionalities**

**Online Balance to Offline Balance:**

- Users download online balance to their wallet, securely storing balance, onIndex, and offIndex in the Secure Enclave.
- The central bank's public key verifies the downloaded offline balance.

**Offline to Offline Balance Transfer:**

- Users send a specified balance to another user's public key with a requested index.
- The sender generates a digital token containing the sender's public key, amount, and index using cryptographic signatures.
- The receiver verifies the token against the sender's public key and increments the balance securely in the Secure Enclave.

**Usage Instructions**

- **View current balance:** The current balance is displayed on the main screen.
- **Send a payment:**
   - Enter the amount to send.
   - Enter the recipient's public key (copied from the debug area or generated using `generate_keys.py`).
   - Tap the "Send" button.
- **Receive a payment:**
   - Enter the sender's signature, amount, and index.
   - Tap the "Verify and Increment Counter" button.

**Additional Information**

- **Key management:**
   - The application generates a private key during its first run and stores it securely in the Secure Enclave.
   - The public key is displayed in the user interface and used in transactions.
- **Debugging and key management:**
   - Copy the public key from the debug area in Xcode.
   - Optional bank keys are provided (`private_key.pem` and `public_key.pem`).
   - Generate new keys using `python3 generate_keys.py`.
   - Create a token for the user on the Benhlaf central bank using `python3 sign.py`.
- **Signature generation and verification:**
   - The project includes Python scripts for signature creation and verification (`signature_script.py`).
   - Ensure you have the required Python package: `pip install cryptography`
- **Security considerations:**
   - Private keys are securely stored in the Secure Enclave.
   - All sensitive data is encrypted and decrypted using cryptographic methods.
   - Signature verification prevents unauthorized balance modifications.

**For further assistance or inquiries, please refer to the project's GitHub repository or contact the developer.**
