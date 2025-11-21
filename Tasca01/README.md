# Tasca: Gestió de Còpies de Seguretat

## Introducció
Durant aquesta tasca treballareu sobre el tema de còpies de seguretat amb un cas pràctic. Aprendreu a prioritzar dades, definir periodicitat i tipus de còpia, escollir mitjans i dissenyar polítiques de recuperació.

## Cas Client
**Empresa:** Muntatges i Serveis Tècnics SL  
**Activitat:** Instal·lació i manteniment d'equips industrials  

**Infraestructura:**
- **Servidor de Fitxers (Ubuntu Server):**
  - Documents de Projectes: Plànols i especificacions tècniques (300 GB)
  - Bases de Dades (Comptabilitat i Clients): 20 GB, canvi constant
  - Carpetes Personals dels Usuaris: 100 GB
- **10 Equips Clients (Windows 10/11):** Fitxers locals temporals per tècnics
- **Connexió a Internet:** Fibra òptica 600 Mbps simètrica

**Requisits de Recuperació:**
- **RTO:** ≤ 4 hores per dades de Comptabilitat/Clients  
- **RPO:** ≤ 4 hores per Comptabilitat/Clients, 24h per la resta  
- **Retenció:** ≥ 1 mes

## Fase 1: Treball Individual
- **Què copiar?** Prioritzar dades crítiques i decidir si cal copiar els equips clients.  
- **Periodicitat i tipus de còpia:** Diari, setmanal, mensual; completa, diferencial o incremental.  
- **Mitjans i ubicació:** Escollir discs externs, NAS, Cloud o cintes segons la regla 3-2-1.

## Fase 2: Treball per Parelles
- Comparar respostes individuals i arribar a consens.  
- Dissenyar un esquema unificat de còpies 3-2-1:  
  - **Element:** Dades crítiques  
  - **Proposta de la Parella**  
  - **Justificació**  
  - **Periodicitat, tipus de còpia, mitjà local i extern**

## Fase 3: Treball en Grup
- Debat i selecció de la millor proposta  
- Redacció de la política definitiva de còpies de seguretat per al client  

## Document Final
El document final ha de contenir:
1. **Dades objecte de còpia:** Crítiques i no crítiques, servidor i clients  
2. **Cronograma setmanal:** Dia a dia, tipus de còpia i mitjà  
3. **Elecció de mitjans i ubicació (3-2-1):** Local, extern i fora de lloc  
4. **Estratègia de recuperació (RTO/RPO):** Com s’assegura disponibilitat i mínim de pèrdua de dades

## Materials i Recursos
- Moodle 0226 Seguretat Informàtica: RA2.AA3Còpies  
- INCIBE: [Copias de seguridad. Guía para el empresario](https://www.incibe.es)  
- Xataka: [Backup 3-2-1, método definitivo](https://youtu.be/PM_M4Iz6I4o?si=F7DRyDDTZE3hjWn8) (YouTube, Setembre 2017)

## ENLLAÇ INFORME
[Informe](infomre.md)
