# 📁 Projecte NFS – DevOptimize Solutions

## Introducció
En aquest projecte desenvoluparem una solució que els nostres clients ens demanen molt sovint: **centralitzar dades en un entorn Linux** de manera segura i eficient.  

El client, **DevOptimize Solutions**, és una startup de desenvolupament de programari que treballa exclusivament amb Linux. Actualment tenen un problema important: el seu codi font i documents estan repartits en ordinadors individuals. Cada desenvolupador té la seva pròpia còpia i això provoca conflictes de versions, fitxers desactualitzats i molta pèrdua de temps.

Per solucionar-ho, implementarem un **servidor de fitxers centralitzat amb NFS (Network File System)**, la solució nativa i més utilitzada en entorns Linux. Com que no utilitzen cap sistema d’autenticació centralitzada, gestionarem l’accés mitjançant **usuaris, grups, permisos i configuració d’exports**.

---

## 🎯 Objectiu del Projecte
Crear una demostració funcional formada per:

- **Un servidor NFS (versió 3)** on centralitzarem els fitxers.  
- **Un client Linux** que accedirà a aquests recursos compartits.  
- **Usuaris i grups** que simulin l’empresa del client.  
- **Configuració d’exports i permisos** (`/etc/exports`, `chmod`, `chown`) per demostrar el control d’accés real.

L’objectiu és que DevOptimize Solutions pugui veure:
- Com quedarà la seva futura infraestructura.
- Quines millores incorpora.
- I també quines limitacions té treballar sense autenticació centralitzada.

---

## 📦 Repositori de la Tasca
Tens tota la descripció detallada aquí:

👉 **https://github.com/SMX2n/Projecte04-NFS**

Aquest README forma part de la documentació que acompanyarà la teva prova de concepte.

---

## 🧰 Què construiràs?
- Un **servidor** amb NFSv3 configurat.
- Un **client** que es connecta al recurs compartit.
- Directories, permisos i propietaris ajustats per simular l'empresa.
- Tests per validar que cada usuari té (o no té) accés als recursos.

---

## 🚀 Per què és important aquesta demo?
DevOptimize Solutions necessita:
- Centralitzar el seu codi.
- Evitar conflictes de versions.
- Estalviar temps i errors interns.

Amb aquesta implementació veuran una solució real, funcional i adaptada al seu entorn 100% Linux.

---

[Guia de la Tasca09](guia.md)

