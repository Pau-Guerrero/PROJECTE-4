# GUIA SSH
---

## 1. Instal·lació del servei SSH

Per començar, instal·lem el servei SSH amb la comanda:

```bash
sudo apt install ssh
```

## 2. Comprovació del servei

Un cop instal·lat, podem verificar que el servei està actiu amb:
```bash
sudo systemctl status ssh
```

sudo systemctl status ssh
![](img/image01.png)

## 3. Connexió al servidor via SSH

Per connectar-nos al servidor, obrim PowerShell i executem la comanda:

```bash
ssh <nom_d'usuari>@<IP_del_servidor>
```
Després introduïm la contrasenya de l'usuari. Un cop verificada, establirem la connexió amb el servidor i podrem treballar de manera remota.

![](img/image02.png)

## 4. Comprovació de la connexió

Un cop connectats al servidor via SSH, podem verificar que estem treballant al sistema remot executant:

```bash
hostname
```

![](img/image03.png)

## 5. Afegir un usuari nou

Per crear un usuari nou al servidor, utilitzarem la comanda següent:

```bash
sudo adduser <nom_del_usuari>
```

![](img/image04.png)

## 6. Configuració del fitxer SSH

Per editar la configuració del servei SSH, obrim el fitxer `/etc/ssh/sshd_config` amb permisos de superusuari:

```bash
sudo nano /etc/ssh/sshd_config
```

Un cop dins, assegureu-vos de modificar o afegir les següents línies segons els requisits:

- Port 22 (*Activar el port 22*)
- LoginGraceTime 120 (*Temps d'espera per a login*)
- PermitRootLogin prohibit-password (*Denegar login directe de root amb contrasenya*)
- StrictModes yes (*Comprovar permisos dels fitxers i directoris*)
- RSAAuthentication yes (*Permetre autenticació RSA*)
- PubkeyAuthentication yes (*Permetre autenticació per clau pública*)
- AllowUsers <nom_d_usuari> (*Permetre només l'usuari especificat*)
  
![](img/image05.png)
![](img/image06.png)


Ara sortim del SSH amb:
```bash
exit
```
I provem d’entrar amb l’usuari creat:
```bash
ssh <nom d'usuari creat>@<IP del servidor>
```
Si apareix “Access denied” significa que la configuració és correcta.
![](img/image07.png)

# 6.Configuració de xarxa al client Windows

Ara entrarem al client de Windows i configurarem la xarxa segons la informació de la imatge.

Passos a seguir:

1. Obrir les **Propietats d’Internet**.
2. Accedir a **Configuració de LAN**.
3. Activar l’opció **Usar proxy**.
4. Entrar a **Opcions avançades**.
5. Modificar el **SOCKS** i el **port** segons les dades de la imatge.

![](img/image08.png)

# 7. Instal·lació i ús de Wireshark
Després instal·larem **Wireshark** seguint aquests passos:

1. Anar a la pàgina oficial de Wireshark i descarregar el programa.
2. Instal·lar Wireshark seguint l’assistent d’instal·lació.
3. Obrir Wireshark.
4. Començar a capturar paquets a la interfície de xarxa corresponent.

![](img/image09.png)

# 9. Instal·lació del Servidor OpenSSH a Windows
Ara instal·larem el **Servidor OpenSSH** a Windows:

1. Obrir **Configuració** de Windows.
2. Anar a **Aplicacions** → **Característiques opcionals**.
3. Buscar l’opció **Servidor OpenSSH**.
4. Seleccionar-la i prémer **Instal·lar**.

![](img/image10.png)
