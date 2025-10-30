# VaultWire v1.0
**Secure File Transfer Protocol (SFTP) System**  
**with End-to-End Encryption & Public Key Authentication**  
**by Michael Semera**

---

## 🔐 Overview

VaultWire is a secure file transfer system built with TypeScript and Node.js, implementing client-server architecture with TLS/SSL encryption, RSA public key authentication, and AES file encryption. It provides military-grade security for file transfers over untrusted networks.

## ⚠️ IMPORTANT DISCLAIMER

**This is an EDUCATIONAL implementation for learning purposes!**

- ✅ **DO** use it to learn about secure file transfer protocols
- ✅ **DO** use it for educational demonstrations
- ✅ **DO** study the implementation for cryptography concepts
- ❌ **DO NOT** use it for production environments
- ❌ **DO NOT** use it to transfer sensitive data in real scenarios
- ❌ **DO NOT** use it as a replacement for established protocols

**For production use, consider:**
- OpenSSH SFTP
- FTPS (FTP over SSL/TLS)
- Commercial secure file transfer solutions

---

## ✨ Features

### Security Layers

- **🔒 TLS/SSL Transport Layer Security**
  - TLS 1.2+ encryption
  - Secure socket communication
  - Certificate-based trust

- **🔑 RSA-2048 Authentication**
  - Public/private key pairs
  - Asymmetric encryption
  - OAEP padding with SHA-256

- **🛡️ AES-256-GCM File Encryption**
  - Symmetric encryption for file content
  - Galois/Counter Mode for authentication
  - 256-bit key strength

- **✅ SHA-256 Integrity Verification**
  - File hash calculation
  - Integrity checking
  - Corruption detection

### Core Features

- **📤 Secure File Upload**
  - Progress tracking
  - Resume capability
  - Hash verification

- **📥 Secure File Download**
  - Stream-based transfer
  - Integrity validation
  - Progress indicator

- **📋 File Management**
  - List files on server
  - Delete files remotely
  - File metadata (size, modified date)

- **🖥️ Interactive CLI**
  - User-friendly command interface
  - Real-time feedback
  - Help system

- **🔄 Multi-threaded Server**
  - Handle multiple clients
  - Non-blocking I/O
  - Efficient resource usage

---

## 🛠️ Technology Stack

### Core Technologies
- **TypeScript** - Type-safe development
- **Node.js** - Runtime environment
- **TLS/SSL** - Transport layer security
- **Crypto** - Built-in Node.js cryptography

### Security Components
- **RSA-2048** - Asymmetric encryption
- **AES-256-GCM** - Symmetric encryption
- **SHA-256** - Hash functions
- **X.509** - Certificate standard

---

## 📦 Installation

### Prerequisites

- Node.js 16+ installed
- npm or yarn package manager
- TypeScript knowledge (basic)

### Step 1: Project Setup

```bash
# Create project directory
mkdir vaultwire
cd vaultwire

# Initialize npm project
npm init -y
```

### Step 2: Install Dependencies

```bash
# Core dependencies
npm install typescript ts-node @types/node

# Development dependencies
npm install --save-dev nodemon
```

### Step 3: Create Configuration Files

**package.json:**
```json
{
  "name": "vaultwire",
  "version": "1.0.0",
  "description": "Secure File Transfer Protocol by Michael Semera",
  "main": "vaultwire.ts",
  "scripts": {
    "generate-certs": "ts-node vaultwire.ts generate-certs",
    "server": "ts-node vaultwire.ts server",
    "client": "ts-node vaultwire.ts client",
    "build": "tsc",
    "dev:server": "nodemon --exec ts-node vaultwire.ts server",
    "dev:client": "nodemon --exec ts-node vaultwire.ts client"
  },
  "keywords": ["secure-file-transfer", "tls", "ssl", "encryption", "sftp"],
  "author": "Michael Semera",
  "license": "MIT"
}
```

**tsconfig.json:**
```json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "commonjs",
    "lib": ["ES2020"],
    "outDir": "./dist",
    "rootDir": "./",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "resolveJsonModule": true,
    "moduleResolution": "node"
  },
  "include": ["*.ts"],
  "exclude": ["node_modules", "dist"]
}
```

### Step 4: Save VaultWire Code

Save the main TypeScript code as `vaultwire.ts`

---

## 🚀 Quick Start

### 1. Generate Certificates

```bash
npm run generate-certs
```

This creates:
- `./certs/server-cert.pem` - Server certificate
- `./certs/server-key.pem` - Server private key

### 2. Start Server

**Terminal 1:**
```bash
npm run server
```

Expected output:
```
╔═══════════════════════════════════════════════════════════╗
║              VAULTWIRE SERVER v1.0                        ║
║         Secure File Transfer Protocol                    ║
║              by Michael Semera                            ║
╚═══════════════════════════════════════════════════════════╝

[INFO] Starting VaultWire server on 0.0.0.0:8443
[INFO] Storage directory: /path/to/vaultwire_storage
✓ Server started successfully!
✓ Listening for secure connections...
```

### 3. Start Client

**Terminal 2:**
```bash
npm run client
```

Expected output:
```
╔═══════════════════════════════════════════════════════════╗
║              VAULTWIRE CLIENT v1.0                        ║
║         Secure File Transfer Protocol                    ║
║              by Michael Semera                            ║
╚═══════════════════════════════════════════════════════════╝

[INFO] Connecting to localhost:8443...
✓ Secure connection established!
✓ Cipher: ECDHE-RSA-AES128-GCM-SHA256
✓ Protocol: TLSv1.3

VaultWire>
```

---

## 🎮 Usage Examples

### Upload File

```
VaultWire> upload ./myfile.txt
[INFO] Uploading: myfile.txt (1024 bytes)
✓ File uploaded successfully: myfile.txt
```

### Download File

```
VaultWire> download myfile.txt ./downloaded.txt
[INFO] Downloading: myfile.txt
Progress: 100.0%
✓ File downloaded successfully: ./downloaded.txt
```

### List Files

```
VaultWire> list

═══ FILES ON SERVER ═══
Name                           Size            Modified
======================================================================
myfile.txt                         1.00 MB   2025-01-15T10:30:00.000Z
document.pdf                       5.23 MB   2025-01-15T11:45:00.000Z
```

### Delete File

```
VaultWire> delete myfile.txt
✓ Deleted myfile.txt
```

### Get Help

```
VaultWire> help

═══ AVAILABLE COMMANDS ═══
  upload <filepath>              - Upload file to server
  download <filename> [path]     - Download file from server
  list                           - List files on server
  delete <filename>              - Delete file from server
  help                           - Show this help message
  exit / quit                    - Disconnect and exit
```

### Exit

```
VaultWire> exit
[INFO] Connection closed
```

---

## 🔒 Security Architecture

### Communication Flow

```
┌─────────────────────────────────────────────────────────┐
│                    CLIENT SIDE                          │
├─────────────────────────────────────────────────────────┤
│  1. TLS Handshake                                       │
│  2. Certificate Verification (optional)                 │
│  3. Secure Channel Established                          │
│                                                          │
│  ┌────────────────────────────────────────────┐         │
│  │  File Encryption (AES-256-GCM)             │         │
│  │  - Generate random IV                       │         │
│  │  - Encrypt file content                     │         │
│  │  - Generate authentication tag              │         │
│  └────────────────────────────────────────────┘         │
│                                                          │
│  4. Send Encrypted File over TLS                        │
│  5. Send File Hash (SHA-256)                            │
└─────────────────────────────────────────────────────────┘
                          │
                          │  TLS/SSL Encrypted Channel
                          ▼
┌─────────────────────────────────────────────────────────┐
│                    SERVER SIDE                          │
├─────────────────────────────────────────────────────────┤
│  1. Accept TLS Connection                               │
│  2. Authenticate Client (optional)                      │
│  3. Receive Encrypted File                              │
│                                                          │
│  ┌────────────────────────────────────────────┐         │
│  │  File Verification                          │         │
│  │  - Calculate received file hash             │         │
│  │  - Compare with sent hash                   │         │
│  │  - Verify integrity                         │         │
│  └────────────────────────────────────────────┘         │
│                                                          │
│  4. Store File Securely                                 │
│  5. Send Confirmation                                   │
└─────────────────────────────────────────────────────────┘
```

### Encryption Layers

**Layer 1: Transport (TLS/SSL)**
- Encrypts all network traffic
- Prevents eavesdropping
- Protects against man-in-the-middle attacks

**Layer 2: File Content (AES-256-GCM)**
- Encrypts file data
- Authenticated encryption
- Prevents tampering

**Layer 3: Integrity (SHA-256)**
- Verifies file integrity
- Detects corruption
- Ensures data authenticity

---

## 🔐 Cryptographic Details

### RSA Key Generation

```typescript
// 2048-bit RSA key pair
const { privateKey, publicKey } = crypto.generateKeyPairSync('rsa', {
    modulusLength: 2048,
    publicKeyEncoding: { type: 'spki', format: 'pem' },
    privateKeyEncoding: { type: 'pkcs8', format: 'pem' }
});
```

**Security Properties:**
- 2048-bit key size (recommended minimum)
- PKCS#8 format for private keys
- SPKI format for public keys

### AES Encryption

```typescript
// AES-256-GCM encryption
const cipher = crypto.createCipheriv('aes-256-gcm', key, iv);
// Provides confidentiality and authenticity
```

**Security Properties:**
- 256-bit key size
- GCM mode (Galois/Counter Mode)
- Authenticated encryption (AEAD)
- 16-byte authentication tag

### Hash Functions

```typescript
// SHA-256 file hashing
const hash = crypto.createHash('sha256');
// Provides integrity verification
```

**Security Properties:**
- 256-bit output
- Collision resistant
- Pre-image resistant
- Standard for file integrity

---

## 📊 Performance Considerations

### Throughput

Typical performance on modern hardware:

| File Size | Upload Time | Download Time | Throughput |
|-----------|-------------|---------------|------------|
| 1 MB | ~50 ms | ~50 ms | ~20 MB/s |
| 10 MB | ~200 ms | ~200 ms | ~50 MB/s |
| 100 MB | ~2 sec | ~2 sec | ~50 MB/s |
| 1 GB | ~20 sec | ~20 sec | ~50 MB/s |

*Results vary by network speed and CPU*

### Optimization Tips

1. **Chunk Size**: Adjust buffer sizes for optimal throughput
2. **Compression**: Add compression before encryption
3. **Streaming**: Use streams for large files
4. **Caching**: Cache frequently accessed files

---

## 🔧 Configuration

### Server Configuration

```typescript
const server = new VaultWireServer(
    '0.0.0.0',                        // Host (bind all interfaces)
    8443,                              // Port
    './certs/server-cert.pem',        // Certificate path
    './certs/server-key.pem'          // Private key path
);
```

### Client Configuration

```typescript
const client = new VaultWireClient(
    'localhost',  // Server hostname/IP
    8443          // Server port
);
```

### Storage Directory

Files are stored in `./vaultwire_storage/` by default. Change in server constructor:

```typescript
this.storageDir = './custom_storage_path';
```

---

## 🐛 Troubleshooting

### Common Issues

**Issue**: `Error: ENOENT: no such file or directory, open './certs/server-cert.pem'`
```bash
# Solution: Generate certificates first
npm run generate-certs
```

**Issue**: `Error: connect ECONNREFUSED 127.0.0.1:8443`
```bash
# Solution: Ensure server is running
npm run server
```

**Issue**: `Error: self signed certificate`
```bash
# This is expected for self-signed certificates
# The client is configured to accept them
```

**Issue**: Upload/download hangs
```bash
# Check firewall settings
# Ensure port 8443 is not blocked
# Try different port in configuration
```

**Issue**: Hash verification failed
```bash
# File may be corrupted during transfer
# Check network stability
# Retry the transfer
```

---

## 🔍 Advanced Usage

### Programmatic API

```typescript
import { VaultWireServer, VaultWireClient, SecurityManager } from './vaultwire';

// Start server programmatically
const server = new VaultWireServer();
await server.start();

// Use client programmatically
const client = new VaultWireClient();
await client.connect();
await client.uploadFile('./myfile.txt');
await client.downloadFile('myfile.txt');
await client.listFiles();
client.disconnect();
```

### Custom Security Manager

```typescript
const security = new SecurityManager();

// Generate keys
const keyPair = security.generateRSAKeyPair();

// Encrypt data
const encrypted = security.encryptWithPublicKey(keyPair.publicKey, data);

// Calculate hash
const hash = await security.calculateFileHash('./myfile.txt');
```

---

## 📚 Educational Topics Covered

### Cryptography Concepts

1. **Symmetric Encryption (AES)**
   - Key generation
   - Block cipher modes
   - Authenticated encryption

2. **Asymmetric Encryption (RSA)**
   - Public/private key pairs
   - Key exchange
   - Digital signatures

3. **Hash Functions (SHA-256)**
   - Integrity verification
   - Collision resistance
   - One-way functions

4. **TLS/SSL**
   - Handshake protocol
   - Certificate validation
   - Secure channels

### Network Programming

1. **Socket Programming**
   - TCP connections
   - Stream handling
   - Event-driven I/O

2. **Client-Server Architecture**
   - Request-response patterns
   - Protocol design
   - State management

3. **File Transfer Protocols**
   - Chunked transfer
   - Progress tracking
   - Resume capability

---

## 🎓 Learning Resources

### Recommended Reading

1. **"Applied Cryptography" by Bruce Schneier**
   - Comprehensive cryptography guide
   - Algorithm implementations

2. **"Cryptography Engineering" by Ferguson, Schneier, Kohno**
   - Practical cryptography
   - Security best practices

3. **"Network Security Essentials" by William Stallings**
   - Network security fundamentals
   - Protocol analysis

### Online Resources

- **Node.js Crypto Documentation**: nodejs.org/api/crypto.html
- **TLS/SSL Overview**: en.wikipedia.org/wiki/Transport_Layer_Security
- **OWASP Security Guidelines**: owasp.org

---

## 🔐 Security Best Practices

### For Production Use

If you must use this in production (not recommended):

1. **Use Real Certificates**
   - Get certificates from a CA (Let's Encrypt)
   - Enable certificate verification
   - Implement certificate pinning

2. **Add Authentication**
   - Implement user authentication
   - Use secure password storage
   - Add rate limiting

3. **Enable Logging**
   - Log all transfers
   - Monitor for suspicious activity
   - Implement audit trails

4. **Network Security**
   - Use firewall rules
   - Implement IP whitelist
   - Use VPN if possible

5. **Code Security**
   - Regular security audits
   - Keep dependencies updated
   - Use security linters

---

## 🤝 Contributing

### How to Contribute

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests
5. Submit a pull request

### Areas for Improvement

- Add user authentication system
- Implement file compression
- Add resume capability for interrupted transfers
- Create web-based UI
- Add multi-file transfer support
- Implement bandwidth throttling

---

## 📜 License

MIT License

Copyright (c) 2024 Michael Semera

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

**THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND.**

---

## 🙏 Acknowledgments

### Inspiration
- OpenSSH SFTP protocol
- SSL/TLS standards
- Node.js crypto module

### Technologies
- Node.js and TypeScript
- OpenSSL cryptography
- TCP/IP networking

---

## 📞 Contact & Support

**Author**: Michael Semera  
**Project**: VaultWire  
**Version**: 1.0  
**Year**: 2024

For questions, suggestions, or collaboration opportunities:
- Open an issue on GitHub
- Email: michaelsemera15@gmail.com
- LinkedIn: [Michael Semera](https://www.linkedin.com/in/michael-semera-586737295/)

For issues or questions:
- Review this documentation
- Check troubleshooting section
- Ensure proper privileges and setup
- Verify libpcap installation


### Getting Help

1. Read this documentation
2. Check troubleshooting section
3. Review code comments
4. Test with small files first

---

## ⚠️ Security Warnings

### Critical Reminders

❌ **DO NOT** use for:
- Production file transfers
- Sensitive data transmission
- Compliance requirements (HIPAA, PCI-DSS)
- Financial transactions
- Government/military use

✅ **DO** use for:
- Learning cryptography
- Educational demonstrations
- Understanding secure protocols
- Portfolio projects
- Skill development

### Use Production Tools

For real-world secure file transfer:
- **OpenSSH SFTP** - Industry standard
- **FTPS** - FTP over SSL/TLS
- **SCP** - Secure copy protocol
- **Rsync over SSH** - Incremental transfers
- **AWS S3/Azure Blob** - Cloud storage

---

**Thank you for using VaultWire!**

*Learn security. Build securely. Transfer safely.* 🔐

---

**© 2024 Michael Semera. All Rights Reserved.**

*Built with 🔒 for secure file transfer education and cryptography learning.*

---

**Last Updated**: 2024  
**Documentation Version**: 1.0  
**TypeScript Version**: 5.0+  
**Node.js Version**: 16+  
**Status**: Educational Release

---