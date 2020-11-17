# Crypter

Пакет для шифрования и дешифрования данных по заданному ключу.


Пример:

```
package main

import (
	"fmt"
	"log"

	crypter "github.com/NuclearLouse/utilities-crypter"
)

var key string

func init() {

	key = crypter.GenerateKey16byte()
}

func main() {

	text := `Это достаточно секретное письмо, которое надо зашифровать!`

	cypher, err := crypter.Encrypt(key, text)
	if err != nil {
		log.Fatalln("encrypt:", err)
	}
	fmt.Println("Шифрованный текст:", cypher)
	// Шифрованный текст: e13eb358947ed6daa0ac32a313a74a8b498bf24d6cfac2b7d5b449fbd8.......

	decryptText, err := crypter.Decrypt(key, cypher)
	if err != nil {
		log.Fatalln("decrypt:", err)
	}
	fmt.Println("Расшифровка:", decryptText)
	// Расшифровка: Это достаточно секретное письмо, которое надо зашифровать!
}

```
