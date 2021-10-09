# Caesar Cipher Formula

**The formula to convert a given plaintext ‘P’ to ciphertext ‘C’ using key ‘K’ is:**

**C = ( P + K ) % 26**

**Similarly, the formula to convert a given ciphertext ‘C’ to plaintext ‘P’ using key ‘K’ is:**

**P = ( C - K ) % 26**

Here, we assign each alphabet a number – A = 0, B = 1, C = 2, D = 3,…,Z = 25. We perform a summation between the number concerning the alphabet and the key value. Then, we perform a modulus operation on that value. For the obtained value, we assign it the alphabet, which is the ciphertext [alphabet](https://www.pythonpool.com/python-alphabet/).

![](https://www.pythonpool.com/wp-content/uploads/2021/05/image-38-1536x768.png)



Suppose our plaintext was ‘ATTACK’ and the key was 10, then for each letter, the encryption would be:

A : C1 = ( 0 + 10 ) % 26 = 10 % 26 = 10 = K

T : C2 = ( 19 + 10 ) % 26 = 29 % 26 = 3 = D

T : C3 = ( 19 + 10 ) % 26 = 29 % 26 = 3 = D

A : C4 = ( 0 + 10 ) % 26 = 10 % 26 = 10 = K

C : C5 = ( 2 + 10 ) % 26 = 12 % 26 = M

K : C6 = ( 10 + 10 ) % 26 = 20 % 26 = U

```python
def encrypt(text, s):
	result = ""
	
	#transverse the plain text
	for i in range(len(text)):
		char = text[i]
		
		#encrypt uppercase
		if char.isupper():
			result += chr((ord(char) + s - 65) % 26 + 65)
		
		#encrypt lowercase	
		else:
			result += chr((ord(char) + s - 97) % 26 + 97)
		return result
	
#check the function
text = "CEASER CIPHER DEMO"
s = 4

print(f"Plain Text: {text}")
print(f"Shift pattern: {str(s)}")
print(f"Cipher: {encrypt(text, s)}")
			
```