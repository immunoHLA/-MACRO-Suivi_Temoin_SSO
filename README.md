# Suivi_Temoin_SSO

Autheur(s) : Louis PETRUS - Ingénieur Bioinformaticien

Service : Secteur HLA - Laboratoire d'Immunologie - Centre hôspitalier Bordeaux Pellegrin 

Date de mise en production : Juillet 2021

Language : VBA

Objectif : Permettre le suivi, l'interprétation et l'archivage des séries de billes des différents lots utilisés pour la technique de SSO


Mode d'emploi : 																							
																					
	1 - Pré-requis : Télécharger le rapport depuis Fusion																						
																							
																							
	Comme pour le suivi du témoin NGS, un rapport doit être téléchargé depuis le logiciel FUSION. Il permettra à la Macro de récupérer automatiquement les données du témoin sans besoin de																						
	recopier ou de copier-coller.																						
																							
	A savoir qu'un rapport peut contenir un ou plusieurs locus à la fois, à vous de choisir celui ou ceux que vous souhaitez archiver.																						
																							
	La procédure est décrite ci-dessous.																						
																							
	![image](https://user-images.githubusercontent.com/78468896/150347114-0fbda3b3-673f-495c-a6aa-7c9d53a15699.png)																			
	Dans FUSION, cliquer sur l'onglet "Reports"																						
	
  ![image](https://user-images.githubusercontent.com/78468896/150347202-77dd90b7-ae8f-4ad6-ace7-8f7c9e6a8ad1.png)
  Filtrer les rapports selon le "T ADN FL" (autrement les rapports seront trop volumineux et longs à télécharger)												
																							
  ![image](https://user-images.githubusercontent.com/78468896/150347236-82ed36f4-5794-482f-904d-b4ca8fa046b0.png)																						
	Cochez la ou les série(s)que vous souhaitez analyser.						
  Pour retrouver vos dernières séries, filtrez selon la date de test (cliquez sur "Test Date").
  
  ![image](https://user-images.githubusercontent.com/78468896/150347288-a04cfc54-a920-4f7c-821c-9693d2d5b0ec.png)
	Pour télécharger le rapport, cliquez sur l'onglet "Tools", puis "Export Data" et sélectionnez le modèle "1.SUIVI SSO T_ADN_FL"										
	(Un message vous proposant d'ouvrir ce fichier apparaîtra, cliquez sur "Non".	Si vous l'avez ouvert, fermez simplement le fichier)																					
																				
	Pour l'emplacement du fichier, choisissez de préférence un emplacement simple à atteindre (ex : le Bureau ou votre dossier dans le N-GBEA HLA).																						
	La macro le supprimera automatiquement une fois les données extraites afin qu'il ne pollue pas vos dossiers de travail.																						
																							
																							
																							
	2 - Lancer la macro pour Importer des données, Changer de lot ou Ajouter une série loupée																						
																							
																							
																							
	1 ) Cliquez sur l'onglet _MACROS_  dans la barre de tâches																						
	2 ) Cliquez sur le bouton SUIVI_SSO																						
																							
														![image](https://user-images.githubusercontent.com/78468896/150347517-663c84b4-ec87-486d-b395-e9ac9fcfeeef.png)									
																							
														(intitulés et logos sont succeptibles de changer)									
																																									
	Le formulaire suivant apparaît proposant différentes options facultatives 																						
																							
																							
										![image](https://user-images.githubusercontent.com/78468896/150347595-c6d6aeb5-41c9-4e07-bf25-bf8d2f41b221.png)
																													
	EXEMPLE : Pour juste charger une ou plusieur série(s) :																						
		Premièrement, ne rien cocher																					
		Deuxièmement, cliquez sur VALIDER et IMPORTER																					
																							
																							
	Après le message de fin reprenant les différents Locus enregistrés, il ne vous reste plus qu'à analyser vos séries et compléter la case commentaire.																						
	Dans le cas d'une série en échec pour une quelconque raison, et si les données sont trop différentes de la tendance jusqu'alors, cochez la case d'exclusion en haut de la colonne. Cette série sera exclue 																						
	des prochains calculs de moyenne et d'écart-type pour ne pas fausser l'attribution des couleurs.																						
																							
																							![image](https://user-images.githubusercontent.com/78468896/150347657-30e3d5b2-1625-4bc0-99d1-8bd446d67634.png)

	Détail des processus :																						
																							
		Changement de lot :																					
			La feuille "en cours" du locus concerné est réinitialisée et les données sont archivées dans la feuille "Historique" à la suite des précédentes. 																				
																							
		Série en échec et sans données :																					
			Dans la feuille "en cours" du Locus concerné, sont uniquement remplis les champs Technicien, Date d'analyse et Commentaire. Cette série sera automatiquement exclue des statistiques.																				
			Veillez à bien indiquer la raison de l'absence de données dans le commentaire. 																				
																							
		Importation d'un rapport FUSION :																					
			Dans la feuille "en cours" du Locus concerné …																				
			S'il s'agit de la première série pour ce lot, la macro complète les colonnes des numéros de billes, de la positivité (Rxn) et les Cutoff. Elle incrémente ensuite les valeurs 																				
			dans le tableau.																				
			Autrement, les trois colonnes précédentes sont déjà présentes, la macro se contente d'enregistrer la nouvelle série à la suite dans le tableau et attribue les couleurs.																				
																							
			A savoir : vous pouvez tout à fait modifier le Rxn d'une bille ou son Cutoff si vous détectez une erreur. Mais attention à ne pas ajouter ou supprimer de valeur.																				
																							
																							
																							
	Organisation du document																						
																							
																							
	Feuilles "Locus en cours" :																						
		Ce sont les feuilles de travail à jour, elles présentent entre autre le numéro de lot, le nom du témoin, les numéros de billes, la positivité ou non de celles-ci ainsi que 																					
		leur Cutoff et les valeurs de la dernière série.																					
		Egalement pour chaque série on observe les initiales du technicien, la date d'analyse et le commentaire technique.																					
																							
		A chaque nouvelle série, la moyenne de chaque bille et son ecart-type sont recalculés pour attribuer le code couleur suivant :																					
																							
				VERT :  Donnée comprise dans un intervalle de deux Ecart-types autour de la moyenne 																			
				JAUNE : Donnée comprise dans un intervalle de deux à trois Ecart-types autour de la moyenne 																			
				ROUGE : Donnée hors de l'intervalle de trois Ecart-types autour de la moyenne 																			
				VIOLET: Donnée supérieure au Cutoff pour une bille Négative -> Faux positif																			
				BLEU :  Donnée inférieure au Cutoff pour une bille Positive -> Faux négatif																			
																							
																							
																							
	Feuilles "Historique" :																						
		Ces feuilles recensent les séries des lots précédents. Aucun action est nécessaire, elles constituent uniquement un recueil des données pour permettre le suivi.																					
																							
																							
																							
																							
	Statistiques																						
																							
																							
	Cliquez sur le bouton dédié dans la feuille "Stats" pour entrer une année d'intérêt.																						
																							
																							
																							
																							
											(intitulés et logos sont succeptibles de changer)												
																							
																							
																							
	Ainsi la Macro parcourt chaque feuille "en cours" et "Historique" pour extraire les données de cette année et afficher par Locus et par technicien(ne) :																						
		le nombre de séries réalisées																					
		le nombre de séries exclues																					
		le taux de valeurs vertes obtenu																					
		le taux de valeurs oranges obtenu																					
		le taux de valeurs rouges obtenu																					
		le taux de faux positifs obtenus																					
		le taux de faux négatifs obtenus																					
																							
	Egalement une synthèse de l'année (tous locus confondus) est généré																						
																							
																							
																							
																							
	Evolution des billes																						
																							
																							
	Cet onglet est uniquement informatif et se remplie automatiquement.																						
																							
	A chaque ajout de nouvelle série, les moyennes et ecart-types des billes sont recalculées et cela peut engendrer un changement de catégorisation des valeurs des séries précédentes (vert, orange, rouge, violet, bleu).																						
	Ces changements sont detectés (à partir de 10 séries minimum dans le lot) et reportés dans l'onglet "Evolution des billes", dans un tableau reprenant la date d'analyse de la série impactée, le lot, le numéro de la bille et la nature du changement de catégorie. 																						
																							
	Vous pouvez trier ces données comme vous le souhaitez, il vous est simplement demandé de ne pas modifier, ajouter ou supprimer de données pour des raison d'intégrité.																						
