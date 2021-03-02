# Poor Men

### Description
**_I followed the description in the section 5.3 to implement the cryptosystem. However, my friend who is a crypto expert told me that there's something wrong about this, can you figure it out?_**

### Solution

We are provided with a data.txt file containing a list of public RSA keys and cs (Cipher String?) and a pdf file containing a research paper written on an RSA-type cryptosystem.

After reading through the document, we find that the only relevant part is the encryption algorithm and Section 5 Point 3, where it states that the message is broken down into several parts for encryption and then recombined after decryption.

![alt text](Section 3.png)

Normally this would be safer, however, if the actual message part that was encrypted turned out to be very short we can decrypt it with a brute force algorithm. We run through each character, encrypt it using the RSA public key and algorithm given, then output the one that matches the ciphertext.

```
pubkeys = [[...]]
cs = [...]
e = 65537
length = len(cs)
for i in range(0,length):
    for a in range(1, 200):
        c = pow(2, e*a, pubkeys[i][1])
        if c == cs[i]:
            print(chr(a), end='')
```
We get the output which is the flag **_DSO-NUS{983945f1246c3c60b9f49ead20ab97f11ff917215dc93da04bfbb2db7197f3d3}**
