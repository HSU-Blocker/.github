# Blockchain-Based IoT Software Update Platform  
> Hansung University Team Blocker

<img width="960" src="https://github.com/user-attachments/assets/1290dadf-f65c-4e51-af90-b5ec2b2ebfa1" />

&nbsp;
## *****Contents*****
- [Project Description](#project-description)
- [Architecture](#architecture)
- [Installation](#installation)
- [Technologies Used](#technologies-used)
- [Main Features](#-main-features)
  - [Manufacturer](#manufacturer)
  - [Device](#device)
- [Expected Impact](#expected-impact)
- [Achievements and Future Research](#achievements-and-future-research)
- [Additional Info](#additional-info)
- [Team Blocker Developers](#️-team-blocker-developers)

&nbsp;
## *****Project Description*****
This project presents a decentralized software update platform that integrates **blockchain** and **CP-ABE (Ciphertext-Policy Attribute-Based Encryption)** technologies to ensure secure IoT device updates.  
By recording update logs on the blockchain, the system ensures transparency and prevents tampering by manufacturers.  
Smart contracts enable **atomic software distribution and payment**, ensuring both security and accountability.  
Using CP-ABE, only devices whose attributes match the manufacturer’s update policy can decrypt and install updates, providing a fine-grained access control mechanism.  
Additionally, **IPFS** is used for distributed storage of large update files, improving scalability and fault tolerance.  
The platform guarantees **device authentication, data integrity, auditability, and high availability**, offering a secure and efficient environment for both manufacturers and users.

&nbsp;
## *****Architecture*****
<p align="center">
  <img width="1860" height="1500" alt="Blocker Architecture Open Source" src="https://github.com/user-attachments/assets/1508c083-76b8-439b-a385-8e39b34d9fc9" />
</p>

&nbsp;
## *****Installation*****

Please follow the installation order below:

1. [Blockchain](https://github.com/HSU-Blocker/Blocker_Blockchain_Network/blob/main/install.md)  
2. [Device](https://github.com/HSU-Blocker/Blocker_Device/blob/main/install.md)  
3. [Manufacturer Backend](https://github.com/HSU-Blocker/Blocker_Manufacturer_Backend/blob/main/install.md)  
4. [Device Frontend](https://github.com/HSU-Blocker/Blocker_Device_Frontend/blob/main/install.md)  
5. [Manufacturer Frontend](https://github.com/HSU-Blocker/Blocker_Manufacturer_Frontend/blob/main/install.md)

For detailed setup instructions, refer to the `install.md` file in each repository.

&nbsp;
## *****Technologies Used*****

### Frontend
- React  
- Vite  
- TypeScript  
- JavaScript  
- Three.js (for visualization)  
- Docker  

### Backend
- Python  
- Flask  
- Web3.py (Blockchain integration)  
- Docker  
- AWS  
- Swagger (API Documentation)

### Blockchain
- Solidity (Smart Contracts)  
- Ganache (Local blockchain test environment)  
- Ethereum Smart Contract  
- Registry Service  
- Web3.py  
- Docker  
- AWS  

### Security / Cryptography
- CP-ABE (Attribute-Based Encryption)  
- AES-256 (Symmetric Encryption)  
- SHA3-256 (Integrity Hash)  
- ECDSA (Digital Signature and Verification)

### Distributed File System
- IPFS (InterPlanetary File System)


&nbsp;
## ✨ *****Main Features*****

### Manufacturer
<table>
  <tr>
    <td><img width="500" height="250" src="https://github.com/user-attachments/assets/b9aeac84-ceb9-4d2f-bda7-06174e1e72cd" /></td>
    <td><img width="500" height="250" src="https://github.com/user-attachments/assets/69b90301-c7ef-4aa5-85b9-f2aee1d46f71" /></td>
  </tr>
  <tr>
    <td><img width="500" height="250" src="https://github.com/user-attachments/assets/f9a37c23-d531-4734-a88f-4a39f24d5ed5" /></td>
    <td><img width="500" height="250" src="https://github.com/user-attachments/assets/b1e83948-0e5a-4865-b9f5-79eae5d0b4eb" /></td>
  </tr>
</table>

**Manufacturer Functions**
- Encrypts update files using **AES-256**, then encrypts the symmetric key with **CP-ABE** to enforce **access control policies**.  
- Generates **SHA3-256 hash values** for integrity verification.  
- Uploads encrypted files to **IPFS**, obtaining the **Content Identifier (CID)**.  
- Registers update UID, IPFS hash (CID), and encrypted key on the **smart contract**.  
- Signs the registered data using **ECDSA private key** and records it on the blockchain for **tamper prevention**.  
- Handles **software distribution and payment atomically** via smart contracts.  
- Registers deployed contract addresses to the **registry contract** for centralized referencing.  
- Uses **Three.js** for visualizing blockchain/IPFS-based update registration processes.



### Device
<table>
  <tr>
    <td><img width="500" height="250" src="https://github.com/user-attachments/assets/1290dadf-f65c-4e51-af90-b5ec2b2ebfa1" /></td>
    <td><img width="500" height="250" src="https://github.com/user-attachments/assets/b0f34620-ff57-46ce-b87a-61108d3c85bc" /></td>
  </tr>
</table>

**Device Functions**
- Detects new software update registration events on the blockchain.  
- Downloads encrypted update files (Es) from **IPFS**.  
- Computes **SHA3-256 hash** and compares it to the registered hash (hEbj) for integrity verification.  
- Decrypts the **CP-ABE-encrypted symmetric key** to obtain the original key (kbj).  
- Hashes the serialized kbj using SHA-256 to generate an **AES-256 key**.  
- Decrypts the update file with the AES key to restore the original file (bj).  
- Installs the verified update and records installation status on the blockchain.  
- Visualizes the update installation process using **Three.js**.  
- Demonstrates actual IoT device operations (e.g., move forward/backward) after successful installation.

&nbsp;
## *****Expected Impact*****

1. **Security Enhancement**  
   Prevents unauthorized access, forgery, and payment bypass during IoT software updates.  
   Ensures device authentication and data integrity.  

2. **Trustworthiness**  
   CP-ABE ensures only devices matching the manufacturer’s policy can decrypt updates.  
   Smart contracts reinforce transparency and reliability in distribution and payment.  

3. **Auditability**  
   All update records are immutably stored on the blockchain for transparent auditing.  

4. **Scalability & Availability**  
   IPFS-based distributed storage ensures scalability and reliability across large IoT ecosystems.


&nbsp;
## *****Achievements and Future Research*****
> ※ **2025년 한국자동차공학회 춘계학술대회** 논문 투고  
> 자동차 ECU 환경의 소프트웨어 업데이트를 위한 해시 함수 성능 평가 연구   
> 속성 만료와 속성 레벨 키 갱신을 활용한 CP-ABE 기반 IoT 소프트웨어 업데이트의 보안성 강화 연구 
>
> ※ **2025 한성대학교 컴퓨터공학부 캡스톤 디자인 우수상** (모바일소프트웨어트랙 부분)
> 
> ※ **SW산학협력프로젝트**를 통해 현대자동차 연구원의 자문을 받아 SDV(Software-Defined Vehicle) 환경에 최적화된 음성 인식 기반 OTA 소프트웨어 업데이트 기법을 연구



&nbsp;
## *****Additional Info*****

| Category | Description |
|-----------|-------------|
| Demo Video | [Watch the demo](https://youtu.be/v9fQUMm7_Fg) |
| Panel Info | [View panel](https://github.com/user-attachments/files/20480591/Blocker.pdf) |


&nbsp;
## ⛓️ *****Team Blocker Developers*****
| <a href="https://github.com/kharabiner" target="_blank"><img width="128" src="https://avatars.githubusercontent.com/u/168187962?v=4" /></a> | <a href="https://github.com/se0y" target="_blank"><img width="128" src="https://avatars.githubusercontent.com/u/127683099?v=4" /></a> | <a href="https://github.com/3DUCK" target="_blank"><img width="128" src="https://avatars.githubusercontent.com/u/170965462?v=4" /></a> | <a href="https://github.com/marulog" target="_blank"><img width="128" src="https://avatars.githubusercontent.com/u/150882419?v=4" /></a> | <a href="https://github.com/mmije0ng" target="_blank"><img width="128" src="https://avatars.githubusercontent.com/u/127730905?v=4" /></a> |
|:-------------:|:------:|:------:|:------:|:------:|
| [박한빈(팀장)](https://github.com/kharabiner) | [공서연](https://github.com/se0y) | [김건우](https://github.com/3DUCK) | [박준희](https://github.com/marulog) | [박미정](https://github.com/mmije0ng) |

### Contact
- **박한빈**: 2271432@hansung.ac.kr  
- **공서연**: 2271014@hansung.ac.kr
- **김건우**: kermit7520k@gmail.com  
- **박준희**: marubug117@gmail.com  
- **박미정**: arsvita0116@gmail.com  
