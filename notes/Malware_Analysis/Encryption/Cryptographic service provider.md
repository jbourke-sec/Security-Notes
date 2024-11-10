**Initialization:** ==CryptAcquireCotext== API

CryptAcquireContext(&hProv,NULL,MS_STRONG_PROV,PROV_RSA_FULL,0);

**PROV_RSA_FULL:** DES, Triple DES, RC2, and RC4 for encryption.
RSA for key exchange and signatures

**PROV_RSA_AES**: AES, RC2, and RC4 encryption, RSA for key exchange and signatures

Supported providers in
**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\Defaults\Provider**

author uses their plain text key and hashes it using any of the known
hashing algorithms

==CryptCreateHash==(hProv,CALG_MD5,0,0,&hHash);
==CryptHashData==(hHash,secretkey,secretkeylen,0);

create a session key from this hash using ==CryptDeriveKey==

CryptDeriveKey(hProv,CALG_3DES,hHash,0,&

CALG_DES = 0x00006601,// DES encryption algorithm.
CALG_3DES = 0x00006603,// Triple DES encryption algorithm.
CALG_AES = 0x00006611,// Advanced Encryption Standard (AES).
ALG_RC4 = 0x00006801,// RC4 stream encryption algorithm.
CALG_RSA_KEYX = 0x0000a400,// RSA public key exchange
algorithm.

**Key Blob**
Some malware authors use a KEYBLOB, which includes their key,
with CryptImportKey

typedef struct KEYBLOB {
BYTE bType;
BYTE bVersion;
WORD reserved;
ALG_ID aiKeyAlg;
DWORD KEYLEN;
BYTE\[\] KEY;
}

PLAINTEXTKEYBLOB (0x8): States a plain text key for a symmetric algorithm,
such as DES, 3DES, or AES
PRIVATEKEYBLOB (0x7): States that this key is the private key of an asymmetric
algorithm
PUBLICKEYBLOB (0x6): States that this key is the public key of an asymmetric
algorithm

malware uses **CryptEncrypt** or **CryptDecrypt** to encrypt or decrypt the data

CryptEncrypt(hKey,NULL,1,0,cyphertext,ctlen,sz);
CryptDecrypt(hKey,NULL,1,0,plaintext,&ctlen);

CryptDestroyKey, CryptDestroyHash, and CryptReleaseContext APIs frees memory