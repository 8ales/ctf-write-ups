## What_did_he_said (Crypto, 300pt)

The challenge provided us a zip file and a pdf describing the challenge's scope. Extracting the files from the zip file we have an `encrypted.txt` file and two recovered public keys.

Hint: What we recovered were few public keys, and confession of few inmates tells us that they had crooked Jailer’s machine to produce repetitive numbers.

`recovered_1.key`:
```
-----BEGIN PUBLIC KEY-----
MCwwDQYJKoZIhvcNAQEBBQADGwAwGAIRAMlciLTeSYml/7kmx5RUToUCAwEAAQ==
-----END PUBLIC KEY-----
```
`recovered_2.key`:
```
-----BEGIN PUBLIC KEY-----
MCwwDQYJKoZIhvcNAQEBBQADGwAwGAIRAOeiuMWobft9fGsyIB23Q4sCAwEAAQ==
-----END PUBLIC KEY-----
```

Taking into account the provided hint we tried to recover the private key using the RsaCtfTool. Executing the command ```./RsaCtfTool.py --publickey ./recovered_1.key --private``` we were able to obtain the private keys for both public keys provided. 

Private key from `recovered_1.key`:
```
-----BEGIN RSA PRIVATE KEY-----
MGQCAQACEQDJXIi03kmJpf+5JseUVE6FAgMBAAECEQCBjSRzYdTkVp/3XMtDUOn9
AgkAy6IS01t/Tp8CCQD9JOj2+9skWwIJAKyInjrGg48xAgkA9vbIdRS28dsCCBK5
zTXwmj24
-----END RSA PRIVATE KEY-----
```

Private key from `recovered_2.key`:
```
-----BEGIN RSA PRIVATE KEY-----
MGICAQACEQDnorjFqG37fXxrMiAdt0OLAgMBAAECEG6RQue+vTkExZ8O3AMwTeEC
CQDqP7G6H+bEkQIJAP0k6Pb72yRbAggUtosdnSKHsQIJAPb2yHUUtvHbAggQ79Zf
iqQHaA==
-----END RSA PRIVATE KEY-----
```

Thus, it's time to decrypt the encrypted file. Using the same tool we were able to decrypt the file as shown below:
```
RsaCtfTool.py --public recovered_2.key --verbose --uncipher encrypt.txt 
[*] Performing hastads attack.
[*] Performing factordb attack.
[+] Clear text : BabaSaidJaiJugad
```
So the flag is hackim18{'BabaSaidJaiJugad'}
