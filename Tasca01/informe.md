# **Informe de còpies de seguretat**
---

## FASE 1
#### QUE COPIAREM?
- Les dades més crítiques del servidor inclouen els documents de projectes, la base de dades de Comptabilitat i Clients i les carpetes personals dels usuaris. No és necessari fer còpia de tots els 10 equips clients, només de les carpetes on els tècnics guarden fitxers importants temporalment.

#### CADA QUAN I DE QUINA MANERA?
- Pel tipus de còpia, es fara una còpia diària incremental per a les dades de Comptabilitat i Clients, còpia setmanal completa de tot el servidor, còpia diària diferencial de la documentació i les carpetes personals, i còpia mensual completa de totes les dades per complir amb la retenció mínima d’un mes.

#### MITJANS I UBICACIÓ
- El mitjà de còpia escollit és un NAS per a còpies ràpides i centralitzades, amb la còpia més recent guardada a l’oficina. A més, es manté una còpia addicional al Cloud per garantir recuperació fora del lloc en cas d’incident greu.


---

## FASE 2
#### DISCUSSIÓ I CONSENS
- Hem estat generalment d’acord a les dades que desitgem emmagatzemar, però al hora de fer la còpia de les Carpetes de cada Usuari la resposta 1 especifica fer una còpia simplement de la carpeta “Documents” mentres que la resposta 2 fa la còpia de totes les carpetes personals.

- Totalment d’acord en no emmagatzemar tots els fitxers ja que es un gast innecessari d’espai ja que simplement cal guardar el fitxers importants.

- A la resposta 1 s’ha proposat fer còpies de seguretat més sovint mentre que la 2 tot i fer còpies diariament de forma menys recurrent. Quan al tipus hem estat totalment d’acord.


#### ELABORACIÓ D'UNA PROPOSTA UNIFICADA
| Element               | Proposta de la Parella                       | Justificació                                                                 |
|-----------------------|---------------------------------------------|----------------------------------------------------------------------------|
| Dades Crítiques       | Documents de projectes, BD de Comptabilitat i Clients, carpetes personals | Són les dades essencials per al funcionament diari |
| Periodicitat (BD)     | Diària                                      | Permet recuperar els canvis més recents sense perdre dadesimportants.  |
| Tipus de Còpia (BD)   | Incremental diària, completa setmanal      | Incremental diària per rapidesa i eficiència; completa setmanal per estabilitat. |
| Mitjà 1 (Local)       | NAS                                         | emmagatzema totes les còpies en un sol lloc, permet recuperació ràpida dins de l’oficina.     |
| Mitjà 2 (Extern)      | Cloud                                       | Assegura recuperació fora del lloc en cas d’incident greu, complint regla 3-2-1. |

---

## FASE 3

**Debat i Selecció: Cada parella presenta el seu esquema. El grup debat els pros i contres de cada proposta (cost, temps de recuperació, seguretat, simplicitat).**

-Les dues propostes estan d’acord en prioritzar les dades més crítiques (bases de dades, documents de projecte, carpetes personals) i no incloure còpia completa dels equips clients, només carpetes clau.
-L’esquema de la parella Pol i Pau pot ser més fàcil de implementar i administrar diàriament, amb una recuperació ràpida per a la majoria d’incidents i un cost assumible per una empresa petita.
-L’esquema de Xavi/Blai aprofundeix en la periodicitat adaptada a RPO/RTO, i inclou opcions de còpia a llarg termini i diversificació de mitjans que incrementen robustesa, però amb més complexitat i cost.


**Disseny de la Política Final: El grup ha de redactar la Política de Còpies de Seguretat Definitiva que presentaran a l'empresa "Muntatges i Serveis Tècnics SL".**

-A Muntatges i Serveis Tècnics SL es garanteix la protecció de les dades més rellevants, incloent documents de projectes, la base de dades de Comptabilitat i Clients i les carpetes personals dels usuaris.
Les còpies es realitzaran de la següent manera: les dades de Comptabilitat i Clients tindran còpies incrementals diàries i una còpia completa setmanal. La documentació i les carpetes personals dels usuaris disposaran de còpies diferencials diàries, i un cop al mes es farà una còpia completa de totes les dades per assegurar la retenció mínima d’un mes.
El mitjà principal serà un NAS ubicat a l’oficina, que permet una recuperació ràpida de la informació. A més, es mantindrà una còpia addicional al Cloud per garantir recuperació fora del lloc en cas d’incident greu. Aquesta política assegura la disponibilitat i seguretat de les dades, complint amb els requisits de l’empresa.

### Document Final (Fase 3)

El grup ha de generar un document amb els següents punts resolts:

## 1) Dades Objecte de Còpia

### Servidor

| Tipus de Dada                     | Crítica | Freqüència de Còpia                        |
|----------------------------------|--------|--------------------------------------------|
| Bases de Dades (Comptabilitat/Clients) | ✅      | Incremental cada 4 h + completa diària     |
| Documents de Projectes            | ✅      | Incremental diària + completa setmanal    |
| Carpetes Personals dels Usuaris   | ❌      | Incremental diària + completa setmanal    |

### Equips Clients

| Tipus de Dada                     | Crítica       | Freqüència de Còpia                       |
|----------------------------------|--------------|-------------------------------------------|
| Documents locals temporals        | ❌            | No es copia (es recomana guardar al servidor) |
| Configuracions especials          | ✅ (si n’hi ha) | Còpia puntual si són difícils de recuperar |

### Quines dades es copien i amb quina freqüència

**Servidor:**

- **Dades crítiques:** Base de dades de Comptabilitat i Clients, documents de projectes → còpia incremental diària, còpia completa setmanal, còpia mensual completa.  
- **Dades no crítiques:** Carpetes personals dels usuaris → còpia diferencial diària, còpia mensual completa.

**Clients:**

- **Dades crítiques:** Només les carpetes clau dels tècnics → còpia diferencial diària, còpia mensual completa.  
- **Dades no crítiques:** La resta dels fitxers dels equips clients no es copien, ja que la informació important està centralitzada al servidor.

---

## 2) Cronograma Setmanal Detallat

| Dia       | Dades (Ex: BD)                              | Tipus de còpia      | Mitjà        |
|-----------|---------------------------------------------|-------------------|-------------|
| Dilluns   | Comptabilitat/Clients, documents de projectes | Incremental       | NAS         |
|           | Carpetes personals dels usuaris              | Diferencial       | NAS         |
| Dimarts   | Comptabilitat/Clients, documents de projectes | Incremental       | NAS         |
|           | Carpetes personals dels usuaris              | Diferencial       | NAS         |
| Dimecres  | Comptabilitat/Clients, documents de projectes | Incremental       | NAS         |
|           | Carpetes personals dels usuaris              | Diferencial       | NAS         |
| Dijous    | Comptabilitat/Clients, documents de projectes | Incremental       | NAS         |
|           | Carpetes personals dels usuaris              | Diferencial       | NAS         |
| Divendres | Comptabilitat/Clients, documents de projectes | Incremental       | NAS         |
|           | Carpetes personals dels usuaris              | Diferencial       | NAS         |
| Dissabte  | Comptabilitat/Clients, documents de projectes | Incremental       | NAS         |
|           | Carpetes personals dels usuaris              | Diferencial       | NAS         |
| Diumenge  | Còpia completa de tot el servidor i dades clients | Completa         | NAS + Cloud |

---

## 3) Elecció de Mitjans i Ubicació (Regla 3-2-1)

- **Mitjà 1 (Local):** NAS ubicat a l’oficina, que emmagatzema totes les còpies de manera centralitzada i permet una recuperació ràpida de la informació.  
- **Mitjà 2 (Extern):** Cloud, utilitzant un servei segur com Microsoft Azure o Google Cloud, per garantir còpia fora del lloc i alta disponibilitat.  
- **Ubicació Fora de Lloc:** La còpia externa es guarda al Cloud, gestionada pel proveïdor del servei i supervisada pel responsable de sistemes de l’empresa per assegurar accessibilitat i seguretat en cas d’incident.

---

## 4) Estratègia de Recuperació (RTO/RPO)

- Per garantir que les dades de Comptabilitat i Clients compleixen amb un **RPO de 4 hores**, es realitzen còpies incrementals diàries que capturen els canvis més recents i minimitzen la pèrdua de dades.  
- Per assolir un **RTO de 4 hores**, la recuperació es fa des del NAS local per obtenir accés immediat, amb la còpia al Cloud com a alternativa en cas que el servidor local no estigui disponible.  
- Això garanteix que les dades es puguin recuperar ràpidament i que els problemes afectin poc el funcionament de l’empresa.

