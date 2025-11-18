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
