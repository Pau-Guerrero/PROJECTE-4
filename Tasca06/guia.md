# GUIA T06
--- 

## 1) Màquines virtuals

Per començar, necessitarem dues màquines virtuals per practicar el suport remot. Aquestes màquines serviran com a entorn de prova sense tocar equips reals.

### Passos:

**-Instal·lar Windows 11:**

 - Crear una màquina virtual amb almenys 4 GB de RAM, 2 CPU i 60 GB de disc.

 - Crear un usuari amb permisos d’administrador.



**-Instal·lar Zorin OS:**

 - Crear una altra màquina virtual amb característiques similars (4 GB de RAM, 2 CPU, 20-40 GB de disc).

 - Crear un usuari amb permisos normals i, si cal, afegir-lo al grup sudo.



**-Xarxa:**

 - Posar a les dues màquines una connexió NAT per tenir Internet i una connexió “Host-Only” per poder comunicar-se entre elles.

 - Comprovar que es poden fer ping entre les dues màquines per assegurar que es veuen.

## 2) Remot

Ara entrarem a windows y anirem a configuracio, despres anirem a systema y activarem la opcio de escritori remot.

despres casmbiarem el nom de la maquina, per fer això anirem a inicio y a adalt ens sortira el nom del nostre ordinador actual y una opcio q iu "cambia nom" cliquem en alla y posarem un nom facil, jo he posat hola

despres tornarem a les opcions de escritori remot, en alla anirem a usuaris de escritorio remoto. s'ens obrira una finestra y a on posa escribe los nombres del objeto  posarem:
```bash
HOLA\User
```
