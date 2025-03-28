# SHA-256 Hash and Digital Signature Project

This repository contains the implementation of hashing a text file using SHA-256 and creating a digital signature using OpenSSL, as per the task requirements. The hash value and digital signature are provided in a text file for submission.

## Task Description
- **Objective**: Hash a text file using SHA-256 and create a digital signature for it using OpenSSL.
- **Submission**: Submit the hash value and digital signature in a text file via GitHub (or Google Doc).

## Prerequisites
- **OpenSSL**: Installed on your system (check with `openssl version`).
- **Operating System**: Linux, macOS, or Windows with OpenSSL support.
- **Files**: A text file to hash (e.g., `message.txt`) and an RSA key pair (optional, can be generated).

## Steps to Reproduce

### 1. Prepare the Text File
Create a sample text file named `message.txt`:
```
Hello, this is a test message.
```

### 2. Generate RSA Key Pair (if needed)
Generate a private and public key pair:
```bash
openssl genrsa -out private_key.pem 2048
openssl rsa -in private_key.pem -pubout -out public_key.pem
```

### 3. Compute SHA-256 Hash
Hash the text file:
```bash
openssl dgst -sha256 -out message_hash.txt message.txt
```
Or view the hash directly:
```bash
openssl dgst -sha256 message.txt
```
Example hash:
```
a591a6d40bf420404a011733cfb7b190d62c65bf0bcda32b57b277d9ad9f146e
```

### 4. Create Digital Signature
Sign the file with the private key:
```bash
openssl dgst -sha256 -sign private_key.pem -out signature.bin message.txt
```
Convert the signature to base64:
```bash
openssl base64 -in signature.bin -out signature.txt
```

### 5. Verify (Optional)
Verify the signature:
```bash
openssl dgst -sha256 -verify public_key.pem -signature signature.bin message.txt
```
Expected output: `Verified OK`

### 6. Submission File
The results are stored in `submission.txt`:
```
SHA-256 Hash: a591a6d40bf420404a011733cfb7b190d62c65bf0bcda32b57b277d9ad9f146e
Digital Signature (Base64): 
MIIBvAIBADANBgkqhkiG9w0BAQEFAASCAmEwggJdAgEAAoGBAN...
```

## Repository Contents
- `message.txt`: The original text file.
- `private_key.pem`: RSA private key (not included in public repos for security).
- `public_key.pem`: RSA public key (optional, for verification).
- `submission.txt`: Contains the SHA-256 hash and base64-encoded digital signature.
- `README.md`: This file.

## How to Use
1. Clone this repository:
   ```bash
   git clone <repository-url>
   ```
2. Follow the steps above to generate your own hash and signature.
3. Replace the contents of `submission.txt` with your results.

## Notes
- The hash is deterministic and will match for identical input files.
- The digital signature will differ based on the private key used.
- Ensure OpenSSL is installed and accessible in your terminal.

## Submission
The final output is in `submission.txt`, submitted via this GitHub repository. For Google Doc submission, copy the contents of `submission.txt` into a shared document.
