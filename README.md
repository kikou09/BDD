# BDD


SELECT raison,activité FROM entreprise


SELECT inscrit FROM inscrire WHERE sess= "CRUNGA" 


Avec jointure explicite :
SELECT nom FROM participant JOIN inscrire using (inscrit) WHERE sess= "CRUNGA" 
Avec jointure implicite:
SELECT A.nom FROM participant A ,inscrire B WHERE A.inscrit=B.inscrit AND B.sess="CRUNGA" 
Avec imbrication :
SELECT nom FROM participant WHERE inscrit IN( SELECT inscrit FROM inscrire WHERE sess="CRUNGA")


SELECT nom FROM participant join inscrire using (inscrit) WHERE sess="CRUNGA" AND entr IS NULL 

Avec jointure explicite :
SELECT DISTINCT raison FROM entreprise join participant using(entr) ORDER BY raison ASC 
Avec jointure implicite :
SELECT DISTINCT raison FROM entreprise A ,participant B WHERE A.entr=B.entr 

SELECT sess , intitulé , date_format(début, "%a %d") as jour FROM session WHERE début BETWEEN '1984-08-01' AND '1984-08-31' 

SELECT nom , date , sess , début FROM session JOIN inscrire USING (sess) JOIN participant USING (inscrit) WHERE date= début - 1 


Avec jointure implicite:
SELECT DISTINCT A.raison , B.activité FROM entreprise A ,entreprise B WHERE A.activité=B.activité AND A.entr != B.entr 
Avec jointure explicite :
SELECT DISTINCT A.raison , B.activité FROM entreprise A JOIN entreprise B USING (activité) WHERE A.entr != B.entr 
