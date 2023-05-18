# VERSION 1

1- Crearem el mòdul infomusic que tindrà els següents models:

Singer
| CAMP | LABEL | TIPUS | ATRIBUT |
| ------------- | ------------- | ------------- | ------------- |
| name  | Name  | Char | Required |
| birthday  | Date of birth  | Date |


Disk	
| CAMP | LABEL | TIPUS | ATRIBUT |
| ------------- | ------------- | ------------- | ------------- |
| name  | Title  | Char | Required |
| publish_date  | Publishing date  | Date |


Song
| CAMP | LABEL | TIPUS | ATRIBUT |
| ------------- | ------------- | ------------- | ------------- |
| name  | Title  | Char | Required |
| order  | Order  | Integer |
| duration | Duration | Integer |
  
  
2- Modifiqueu els models i les vistes per tenir en compte les següents relacions entre els diferents models:
- Un disc conté diferents cançons. 
- Un disc pot tenir diferents cantants
- Un cantant pot tenir diferents discs.
Quan definim una relació One2many s’ha de definir obligatòriament la relació complementària Many2one. 

![](https://github.com/DamianPyCoder/Odoo__Second-Module__Music/blob/main/screenshots_statement/grafico1.png)

  
3- Crearem vistes tree i form pels models disc, singer i song. Feu servir el widget float_time per la duració de la cançó.
A les vistes formulari han d'aparèixer tots els camps del model inclosos els camps relacionals.
No definirem cap action a la vista song.xml perquè no apareixerà al menú.
  
  
4- Instal·larem el mòdul i farem que al menú principal aparegui el nom ‘Infomusic <NC>’. On <NC> són les inicials del nostre nom i cognom.



# VERSION 2
  
1- Crea un nou mòdul infomusicplus basat en  el mòdul infomusic. Fes servir el paràmetre ‘depends’ del fitxer manifest.py.
  
  
2- Afegeix les següents característiques als models i a les vistes fent servir herència de model i de vista:
- Al cantant se li afegeix l’atribut country_of_birth i serà visible tant en la vista tree com a la vista formulari.
- Al cantant se li afegeix també l’atribut photo que inclourà una foto del cantant.
- Al disc se li afegeix l’atribut genre, i podrem escollir entre rock, pop, pop-rock, heavy, … El valor de defecte serà rock.
- Al disc se li afegeix també l’atribut cover que inclourà una foto amb la caràtula del disc.
Per les imatges feu servir el widget image i ajusteu la mida a 150 x 150 pixels com a màxim. Mireu els paràmetres del camp Image.
  
  
3- Afegirem els següents models per les gires del cantant.
Tour
| CAMP | LABEL | TIPUS | ATRIBUT |
| ------------- | ------------- | ------------- | ------------- |
| name | Title | Char | Required |

TourCity
| CAMP | LABEL | TIPUS | ATRIBUT |
| ------------- | ------------- | ------------- | ------------- |
| name | Title | Char | Required |
| country | Country | res.country | Required |
| date | Date | Date |
  
  
4- Modifiqueu els models i les vistes per tenir en compte les següents relacions entre els diferents models:
- Un cantant pot fer diferents gires. 
- Una gira té diferents ciutats
Quan definim una relació One2many s’ha de definir obligatòriament la relació complementaria Many2one.

![](https://github.com/DamianPyCoder/Odoo__Second-Module__Music/blob/main/screenshots_statement/grafico2.png)


5- Afegirem una nova vista tipus tree i formulari pels nous models. A les vistes formulari han d'aparèixer tots els camps del model inclosos els camps relacionals.
  
  
6- Sobreescriviu el menú root per reaprofitar el menú d’Infomusic i afegiu les noves entrades per tour i tour_city.
***   <menuitem name="Infomusic+ <NC>" id="infomusic.menu_root"/>***
 On <NC> són les inicials del nostre nom i cognom.
Afegiu una nova entrada al menú vertical Tours i una nova acció Tours penjant d’aquest menu.
No definirem cap action a la vista tour_city.xml perquè no apareixerà al menú.


7- Instal·larem el mòdul i comprovarem que al menú principal aparegui el nom ‘Infomusic+NC'
  
  
8- Desinstaleu el mòdul Infomusic i comproveu que també es desinstal·la el mòdul Infomusic+. Instaleu de nou el mòdul Infomusic+ i comproveu que també s’instal·la el mòdul Infomusic. 


# VERSION 3

Haurem d’implementar els següents requiments addicionals:  
  
3.1- Afegirem al model disk un nou camp nbr_of_songs que calcularem comptant el número de cançons del disc.  
  
3.2- Afegirem un nou camp age al cantant que calcularem a partir de la data de naixement.  
  
3.3- El valor del camp name dels models singer, disk i tour ha de ser únic.  
  
3.4- No es podran afegir més de 4 ciutats a una gira.  
  
3.5- Afegirem al model tour_city un camp confirmed que calcularem a partir de la data de la gira. Tindrà valor True si el camp date està omplert i valor False si no ho està.  
  
3.6- Afegirem al model tour un camp state amb els valors: New, Confirmed, Done i Cancelled.  
  
- Passem de tour.state = New a Confirmed quan totes les tour_city estan confirmades.  
- Passem de tour.state = Confirmed a New quan alguna de les tour_city no està confirmada.
- Passem de  tour.state = Confirmed a Done en clicar el botó Done
- Passem de  tour.state = New o Planned a Cancelled en clicar el botó Cancel  
  
3.7- Només es podran esborrar les gires en estat Cancelled o Done.  
  
