
new set of APIs that have
been implemented by Microsoft

**Initialize the algorithm provider**
==BCryptOpenAlgorithmProvider==(&hAesAlg, BCRYPT_AES_ALGORITHM,
NULL, 0)
**Prepare the key:**
==BCryptGenerateSymmetricKey==(hAesAlg, &hKey, pbKeyObject,
cbKeyObject, (PBYTE)SecretKey, sizeof(SecretKey), 0)
**Encrypt or decrypt data:**
==BCryptEncrypt==(hKey, pbPlainText, cbPlainText, NULL, pbIV,
cbBlockLen, NULL, 0, &cbCipherText, BCRYPT_BLOCK_PADDING)
**Cleanup:**
BCryptCloseAlgorithmProvider, BCryptDestroyKey, and HeapFree
