___

><font color="#e36c09">🔑 Github and SSH</font>

Generamos un par de claves:

```
ssh-keygen -t ed25519 -C "tu_email@ejemplo.com"
```

Ejecutamos en segundo plano el agente ssh para que gestione nuestras claves:

```
eval "$(ssh-agent -s)"
```

Creamos un archivo de configuración de SSH sino lo tenemos creado:

```
touch .ssh/config
```

Dentro del .ssh/config agregamos una reglas de conexión para github:

```
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519
    AddKeysToAgent yes
    
    # En caso de usar WSL, pueda que sean necesarias las siguientes líneas
    KexAlgorithms sntrup761x25519-sha512@openssh.com,curve25519-sha256,curve25519-sha256@libssh.org
    Ciphers chacha20-poly1305@openssh.com,aes256-gcm@openssh.com,aes128-gcm@openssh.com,aes256-ctr
    MACs hmac-sha2-512-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512,hmac-sha2-256
```

Cargamos nuestra clave privada a nuestro agente SSH

```
ssh-add ~/.ssh/id_ed25519
```

Dentro de la configuración de Github agregamos nuestra clave pública:

```
[ Github Profile Settings > SSH and GPG Keys > New SSH key ]
	
	{ - Key type --> Authentication Key }
	{ - Key --> Copiamos nuestra clave pública completa }
	
	{- Add SSH key }
```

Opcional/En .bashrc indicamos que el agente SSH se inicie cada vez abrimos una nueva terminal:

```
if [ -z "$SSH_AUTH_SOCK" ]; then
  eval "$(ssh-agent -s)" > /dev/null
fi
```

Comprobamos la conexión con Github, la conexión debería ser exitosa:

```
ssh -T git@github.com
>> Hi user! You've successfully authenticated, but GitHub does not provide shell access.
```

___