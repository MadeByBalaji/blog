---
title: Chess-Based Encryption Tool
description: Creating a Chess-Based Encryption Tool: A Journey Through Code
date: 2024-09-24 10:20:00 -0530
categories: [Hobbyist Haven]
tags: [python,tool,encryption]
image:
  path: /assets/img/blog/2024/chess-encry/chess-encrypt.jpg
  lqip: /assets/img/blog/2024/chess-encry/chess-encrypt.jpg
---

## Overview:

In the world of cybersecurity, encryption techniques play a pivotal role in securing data from unauthorized access. With a passion for both cryptography and chess, I embarked on a creative journey to combine these two areas and build a fun yet functional encryption tool. This blog post walks through the code that powers the Chess Encryption tool and explores how chess moves can be transformed into secure data encryption. As an open-source advocate, I also forked the algorithm from the WintrCat [repository](https://github.com/WintrCat/chessencryption) to further develop and enhance the project.



## Why Chess Encryption?

Encryption typically revolves around complex mathematical algorithms, but adding chess as a medium provides an interesting layer of complexity. Chess is a game of strategy, and by mapping chess moves to data points, we can create a non-traditional encryption pattern. This pattern, when decoded correctly, results in the original file, adding a layer of security that’s both robust and fun to work with.


## The Encryption and Decryption Code Breakdown

Here’s a detailed breakdown of the Python code that drives this tool:


### 1. Project Initialization:

The program starts by collecting user input for both encryption and decryption operations:

```python
def encrypt_init():
    input_file = input("Enter the file path: ")
    output_file_path = input("Enter the output file name: ")
    output_file_path+= ".txt"
    return input_file, output_file_path
```  

### 2. The Encryption Function:

The heart of the tool lies in the encryption function. Here’s how it works:

```python
def encryption(source_file, encrypted_file):
   try:

        source_file_size = os.path.getsize(source_file)
        print(f"⏳ Estimated time for Encryption {int((source_file_size/1024)*2)} seconds")
        encrypted_result = encode(source_file)       
        with open(encrypted_file, "w") as file:
            file.write(encrypted_result)
        print(f"🔒 Encrypt successfully saved to {encrypted_file}")
    except FileNotFoundError:
        print(f"❌ Error: The file '{source_file}' was not found.")
    except Exception as e:
        print(f"❌ An error occurred: {e}")  
```

#### Explanation:

1. The function begins by estimating the time required to encrypt the file based on its size.

1. It then calls the encode function (which I forked from the WintrCat repo) to perform the actual encryption.

1. The encrypted result is saved to the specified output file.

1. Error handling is included to ensure the user is notified if the source file is missing or if an exception occurs.

### 3. The Decryption Function:

Just as important as encryption is the ability to decrypt the data back to its original form. Here’s the corresponding function:

```python
def decryption(encrypted_file, source_file):
   try:
        with open(encrypted_file, 'r') as f:
            pgn_string = f.read()     
        decode(pgn_string, source_file)
        print(f"🔓 Decoded data has been written to {source_file}")
    except FileNotFoundError:
        print(f"❌ Error: File '{encrypted_file}' not found.")
    except Exception as e:
        print(f"❌ An error occurred: {e}")
```


#### Explanation:

1. This function reads the encrypted file (in PGN format, which holds chess moves).

1. The decode function reverses the process, restoring the original data.

1. Once the data is decoded, it’s saved back to its original format (which could be an image, document, etc.).



### 4. Decryption Initialization:

Just like the encryption process, we also need to initialize the decryption process:

```python
def decrypt_init():
    input_file = input("Enter the encrypt file path: ")
    output_file_path = input("Enter the output file name ( with extension example- pic.png ): ")
    return input_file, output_file_path
```

#### Explanation:

The function prompts the user for the path of the encrypted file and the name of the file where the decrypted data will be stored. The extension (e.g., .png, .txt) ensures the original file type is maintained.


### 5. The Main Execution Block:

Finally, the main execution block coordinates the entire process:

```python
if name == "__main__": 
	source_file, encrypted_file = encrypt_init()
	encryption(source_file, encrypted_file)
    encrypted_file, decrypted_original_file = decrypt_init()
    decryption(encrypted_file, decrypted_original_file)
```

#### Explanation:

This block runs when the script is executed, first prompting the user for encryption input, performing encryption, then handling decryption.



## The Algorithm: Forking from WintrCat
The core encoding and decoding logic that powers the encode and decode functions was forked from the WintrCat Chess Encryption repository[^wintrcat-repo]. By building upon this, I’ve been able to streamline the user interface and expand the tool’s functionality. This is the beauty of open-source software: it allows developers to collaborate, improve, and adapt innovations that benefit the wider community.


## Final Thoughts
The Chess Encryption tool may appear playful, but it offers a unique method to encrypt data, leveraging the complex and unpredictable nature of chess. Whether you’re a chess enthusiast, a cryptography student, or a developer looking for a creative project, this tool demonstrates the power of combining seemingly unrelated fields to create something new and functional.

Feel free to explore the code, contribute, or suggest new features. You can find the complete project on my GitHub repository[^balaji-repo].


## Key Takeaways:
Innovation in Encryption: Using chess moves to secure data adds a novel layer to encryption algorithms.

Forking the Project: The encode/decode functions were originally forked from the WintrCat repo, showcasing the power of open-source collaboration.

User-friendly Interface: With simple prompts and clear instructions, this tool allows anyone to encrypt and decrypt files easily.


Thank you for reading! I’d love to hear your thoughts on how this concept could be expanded or integrated with other forms of data security.


[^wintrcat-repo]: [link](https://github.com/WintrCat/chessencryption)
[^balaji-repo]: [link](https://github.com/MadeByBalaji/chessencryption)