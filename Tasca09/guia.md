# GUIA NFS
--- 
## 1) Instalar el servicio NFS

Instalamos el demonio que permitirá exportar carpetas por red. Esto añade también las utilidades necesarias y el servicio `nfs-kernel-server`.

```bash
sudo apt update
sudo apt install nfs-kernel-server
```

![](img/image09.png)

***

## 2) Crear grupos de acceso

Los grupos controlan quién puede entrar en cada carpeta. Creamos `devs` y `admins`; así, los permisos serán fáciles de mantener.

```bash
sudo groupadd devs
sudo groupadd admins
```

![](img/image01.png)

***

## 3) Crear usuarios y asignarlos a su grupo

Creamos cuentas de ejemplo y las añadimos al grupo correcto. Esto no obliga a usarlas, pero te sirve para probar permisos desde el servidor.

```bash
# Dev
sudo adduser dev01
sudo adduser dev01 devs

# Admin
sudo adduser admin01
sudo adduser admin01 admins
```

![](img/image02.png)
![](img/image03.png)

***

## 4) Fijar UIDs coherentes

En NFS, el servidor **no envía identidades**, sino números (UID/GID). Fijarlos evita “usuarios desconocidos” y permisos raros en los clientes.

```bash
sudo usermod -u 1001 dev01
sudo usermod -u 1002 admin01
```

![](img/image04.png)

***

## 5) Crear las carpetas a exportar

Ubicamos las compartidas bajo `/srv/nfs/` por orden y porque es una ruta habitual para servicios. Creamos ambas de una vez.

```bash
sudo mkdir -p /srv/nfs/dev-projectes
sudo mkdir -p /srv/nfs/admin_tools
```

![](img/image05.png)

***

## 6) Asignar propiedad y permisos a **dev-projectes**

Ponemos el grupo `devs` y **setgid** (`2` en `2770`) para que **todo lo que se cree herede el grupo**. Sin acceso para “otros”.

```bash
sudo chown root:devs /srv/nfs/dev-projectes
sudo chmod 2770      /srv/nfs/dev-projectes
```

![](img/image06.png)

***

## 7) Asignar propiedad y permisos a **admin\_tools**

Mismo criterio para admins: grupo, permisos estrictos y herencia de grupo por setgid. Así sólo admins podrán leer/escribir.

```bash
sudo chown root:admins /srv/nfs/admin_tools
sudo chmod 2770        /srv/nfs/admin_tools
```

![](img/image07.png)

> **Referencia de error común:** usar `0755` (lectura para “otros”) **abre la carpeta a todo el mundo**.  
> **Imagen del caso no recomendado:** `image10.png`.

***

## 8) Verificar permisos

Comprueba que ves `drwxrws---` (la `s` indica setgid) y los grupos correctos en cada directorio.

```bash
ls -ld /srv/nfs/dev-projectes /srv/nfs/admin_tools
```

![](img/image08.png)

***

## 9) Definir los clientes autorizados en `/etc/exports`

Indica **qué clientes** pueden montar y con qué opciones. Usa la IP/subred del cliente (tu captura muestra `192.168.56.106`).

```bash
sudo nano /etc/exports
```

Contenido de ejemplo:

    /srv/nfs/admin_tools  192.168.56.106(rw,sync,no_subtree_check,root_squash)
    /srv/nfs/dev-projectes 192.168.56.106(rw,sync,no_subtree_check,root_squash)

![](img/image012.png)
![](img/image011.png)

***

## 10) Aplicar exportación NFS 

Tras editar, recarga los exports. `exportfs -ra` reexporta; `-u` desexporta una ruta (útil si cambiaste opciones y quieres “limpiar” antes).

```bash
sudo exportfs -ra
# (opcional) desexportar temporalmente
sudo exportfs -u /srv/nfs/admin_tools
sudo exportfs -u /srv/nfs/dev-projectes
```

![](img/image13.png)

***

## 11) Instalar el cliente NFS

En los clientes sólo necesitas las herramientas de usuario (`nfs-common`) para poder montar las compartidas del servidor.

```bash
sudo apt update
sudo apt install nfs-common
```

![](img/image19.png)

***

## 12) Crear grupos con **GID** fijos

Para que los permisos “casen”, crea los grupos con los **mismos GID** que en el servidor (p. ej. 1001 y 1002).

```bash
sudo groupadd -g 1001 devs
sudo groupadd -g 1002 admins
```

![](img/image17.png)

***

## 13) Crear usuarios con **UID** fijos

Crea las cuentas locales con **UID** iguales a los del servidor y así verán los ficheros con la propiedad correcta.

```bash
sudo useradd -m -u 1001 -g 1001 dev01
sudo useradd -m -u 1002 -g 1002 admin01
```

![](img/image18.png)

***

## 14) Crear puntos de montaje y montar **dev-projectes**

Crea el directorio donde vas a montar y prueba el montaje manual. Si funciona, la red y los exports están OK.

```bash
sudo mkdir -p /mnt/dev-projectes
sudo mount -t nfs 192.168.56.101:/srv/nfs/dev-projectes /mnt/dev-projectes
```

![](img/image16.png)

***

## 15) Montar **admin\_tools**

Repite el proceso para la carpeta de administración. Así podrás validar permisos para cada grupo por separado.

```bash
sudo mkdir -p /mnt/admin_tools
sudo mount -t nfs 192.168.56.101:/srv/nfs/admin_tools /mnt/admin_tools
```

![](img/image15.png)

***

## 16) Montaje persistente en `/etc/fstab`

Añade entradas para montar automáticamente al arrancar. Usa el mismo formato de la prueba manual.

```bash
sudo nano /etc/fstab
```

Ejemplo:

    192.168.56.101:/srv/nfs/admin_tools  /mnt/admin_tools  nfs  defaults  0 0
    192.168.56.101:/srv/nfs/dev-projectes /mnt/dev-projectes nfs defaults 0 0

![](img/image14.png)

***

## 17) Probar `mount -a` y solucionar errores comunes

`mount -a` monta todo lo del `fstab`. Si te da **“mount point … does not exist”**, crea primero el directorio y vuelve a intentar.

```bash
sudo mount -a
# Si falla por punto de montaje inexistente:
sudo mkdir -p /mnt/dev-projectes /mnt/admin_tools
sudo systemctl daemon-reload
sudo mount -a
```

![](img/image20.png)

***

## 18) Comprobaciones rápidas de permisos

Valida que **cada archivo hereda el grupo correcto** y que “otros” no tienen acceso. Esto confirma el efecto del **setgid**.

```bash
# Como dev01:
sudo -u dev01 touch /mnt/dev-projectes/prueba_dev.txt
ls -l /mnt/dev-projectes/prueba_dev.txt

# Como admin01:
sudo -u admin01 touch /mnt/admin_tools/prueba_admin.txt
ls -l /mnt/admin_tools/prueba_admin.txt
```


***

## 19) Evitar permisos 0755 en compartidas privadas

`0755` da lectura/ejecución a cualquiera con acceso local. Para recursos de grupo, mantén `2770` (o ajusta con ACLs si necesitas casos mixtos).

```bash
sudo chmod 2770 /srv/nfs/admin_tools
sudo chmod 2770 /srv/nfs/dev-projectes
```

![](img/image10.png)

***

## 20) Consulta rápida de estado

En servidor, lista lo exportado; en cliente, comprueba montajes activos. Útil para diagnóstico final.

```bash
# Servidor
sudo exportfs -v

# Cliente
mount | grep nfs
```

