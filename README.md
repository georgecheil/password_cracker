# password_cracker
The Python code is a simple script for brute-forcing password hashes using either MD5 or SHA-1 hashing algorithms. Here's an explanation of the code:

1. **Importing hashlib:**
   ```python
   import hashlib
   ```
   This line imports the hashlib module, which provides a common interface to various secure hash and message digest algorithms, including MD5 and SHA-1.

2. **User Input:**
   ```python
   type_of_hash = str(input('Which type of hash you want to bruteforce ?'))
   file_path = str(input('Enter path to the file to bruteforce with: '))
   hash_to_decrypt = str(input('Enter Hash Value To Bruteforce: '))
   ```
   These lines prompt the user to input the type of hash (either 'md5' or 'sha1'), the path to the file containing passwords, and the hash value to be decrypted.

3. **Opening and Reading the File:**
   ```python
   with open(file_path, 'r') as file:
   ```
   This line opens the specified file in read mode.

   ```python
   for line in file.readlines():
   ```
   This loop iterates through each line in the file.

4. **Hashing and Comparison:**
   ```python
   if type_of_hash == 'md5':
       hash_object = hashlib.md5(line.strip().encode())
       hashed_word = hash_object.hexdigest()
       if hashed_word == hash_to_decrypt:
           print('Found MD5 Password: ' + line.strip())
           exit(0)
   ```
   If the user specified 'md5', the script calculates the MD5 hash for each line in the file, compares it with the provided hash, and prints the password if a match is found.

   ```python
   if type_of_hash == 'sha1':
       hash_object = hashlib.sha1(line.strip().encode())
       hashed_word = hash_object.hexdigest()
       if hashed_word == hash_to_decrypt:
           print('Found SHA1 Password: ' + line.strip())
           exit(0)
   ```
   If the user specified 'sha1', the script does the same but for SHA-1 hashes.

5. **Print Result or Not Found:**
   ```python
   print('Password Not In File.')
   ```
   If no match is found in the entire file, this message is printed.

Note: This script is a basic example and might not be the most efficient or secure way to handle password hashing. 

Additionally, brute-forcing passwords is generally not recommended due to ethical and legal considerations.
