---
title: "Hashing with Salt"
date: 2019-04-30T17:39:06+08:00
draft: false
tags: 
   - TAG
categories:
  - 技术
  - 归档
---

[TOC]

 如何防止被"脱裤"

<!--more-->

# "加盐"

在密码前面后者后面加一个随机字符串，叫做"盐salt"

## Hashing with salt

Salt should be generated using a Cryptographically Secure Pseudo-Random Number Generator (CSPRNG). 

To Store a Password

- Generate a long random salt using a CSPRNG.
- Prepend the salt to the password and hash it with a standard password hashing function like Argon2, bcrypt, scrypt, or PBKDF2.
- Save both the salt and the hash in the user's database record.

To Validate a Password

- Retrieve the user's salt and hash from the database.
- Prepend the salt to the given password and hash it using the same hash function.
- Compare the hash of the given password with the hash from the database. If they match, the password is correct. Otherwise, the password is incorrect.

## Making Password Cracking Harder: Slow Hash Functions

增加hash函数计算的时间，例如0.5s计算一次hash值。以防止字典或者暴力破解。

## What hash algorithm should I use?

使用[PBKDF2](https://en.wikipedia.org/wiki/PBKDF2) 算法

不要使用fast cryptographic hash functions such as MD5, SHA1, SHA256, SHA512, RipeMD, WHIRLPOOL, SHA3, etc.

## 伪码

```java
package geekbang.u17;

import edu.princeton.cs.algs4.StdOut;
import java.security.SecureRandom;
import java.util.Base64;

/**
 * Created by HuGuodong on 2019/4/30.
 */

public class TestSalt {

  public static final int SALT_BYTE_SIZE = 24;

  public static void main(String[] args) {
    SecureRandom random = new SecureRandom();
    byte[] salt = new byte[SALT_BYTE_SIZE];
    random.nextBytes(salt);

    String toBase64 = toBase64(salt);
    StdOut.printf("toBase64Salt: %s\n", toBase64);

  }

  private static byte[] fromBase64(String hex){
    return Base64.getDecoder().decode(hex);
  }

  private static String toBase64(byte[] array) {
    return Base64.getEncoder().encodeToString(array);
  }

  public boolean verifyPassword(String testHash, String correctHash){

  // testHash: password + hash(from database)
  // correctHash: hash

    return slowEquals(fromBase64(testHash), fromBase64(correctHash));
  }

  private static boolean slowEquals(byte[] a, byte[] b)
  {
    int diff = a.length ^ b.length;
    for(int i = 0; i < a.length && i < b.length; i++)
      diff |= a[i] ^ b[i];
    return diff == 0;
  }
}

```

## 参考

[hashing-security](https://crackstation.net/hashing-security.htm)

[PBKDF2-github](https://github.com/defuse/password-hashing)

