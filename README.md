## Offline Payment Transaction

**Overview**

This iOS Xcode project demonstrates a secure method for conducting offline payment transactions. It utilizes encryption and the Secure Enclave to protect sensitive data, enabling payments even without a constant internet connection.

**Key Features:**

* Offline transaction processing
* Secure storage of balance and index data using Keychain
* Encryption with elliptic curve keys
* Digital signature verification

**Getting Started:**

1. **Clone the project:**

   ```bash
   git clone https://github.com/AVSaiKumar/OfflineXcode.git
   ```

2. **View the project in Xcode:**

   - Open the `OfflineService.xcodeproj` file.
   - Navigate to the `ContentView.swift` file.

3. **Run the project:**

   - Click the "Run" button to launch the simulator.

**Debugging and Key Management:**

- **Copy public key from debug area:** The public key will be printed in the debug area of Xcode. Copy it from there, as copying from the simulator can be difficult.

- **Bank keys (optional):**
   - The repository includes `private_key.pem` and `public_key.pem` files for bank keys.
   - To generate new keys:
     - Run `python3 generate_keys.py`.
     - Replace the contents of `public_key.pem` in `ContentView.swift` with the newly generated public key.

- **Token generation:**
   - Run `python3 sign.py` to create a token for the user on the Benhlaf central bank.

**Usage Instructions:**

1. **View current balance:** The current balance is displayed on the main screen.

2. **Send a payment:**
   - Enter the amount to send.
   - Enter the recipient's public key (copied from the debug area or generated using `generate_keys.py`).
   - Tap the "Send" button.

3. **Receive a payment:**
   - Enter the sender's signature, amount, and index.
   - Tap the "Verify and Increment Counter" button.

**Additional Information:**

- **Security:**
   - Data is encrypted using the Secure Enclave for enhanced protection.
   - Digital signatures are utilized for transaction verification.
- **Keychain usage:**
   - The balance and index are stored securely in the Keychain.
- **Code structure:**
   - The `SecureEnclaveManager` class handles key management and cryptographic operations.
   - The `ContentView` class manages the user interface and app logic.

**For further assistance or inquiries, please refer to the project's GitHub repository or contact the developer.**

**Note:** This README combines both sets of instructions you provided while maintaining clarity and conciseness. If you would like to separate the debugging and key management instructions, please let me know.


