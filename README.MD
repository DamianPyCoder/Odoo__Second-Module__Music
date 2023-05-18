# VERSION 1

Crearem el mòdul infomusic que tindrà els següents models:

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






duration
Duration
Integer



  
Modifiqueu els models i les vistes per tenir en compte les següents relacions entre els diferents models:
Un disc conté diferents cançons. 
Un disc pot tenir diferents cantants
Un cantant pot tenir diferents discs.
Quan definim una relació One2many s’ha de definir obligatòriament la relació complementària Many2one. 


Crearem vistes tree i form pels models disc, singer i song. Feu servir el widget float_time per la duració de la cançó.
A les vistes formulari han d'aparèixer tots els camps del model inclosos els camps relacionals.
No definirem cap action a la vista song.xml perquè no apareixerà al menú.

Instal·larem el mòdul i farem que al menú principal aparegui el nom ‘Infomusic <NC>’. On <NC> són les inicials del nostre nom i cognom.

