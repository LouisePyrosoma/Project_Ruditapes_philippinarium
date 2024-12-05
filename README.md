# Notre projet^^
La palourde japonaise _Ruditapes philippinarum_ représente une espèce clé de l’aquaculture mondiale, contribuant à 25 % de la production de mollusques. En France, elle a été introduite dans les années 1970 pour ses qualités remarquables : fécondité élevée, croissance rapide ou encore résistance aux maladies. Toutefois, cette espèce a subi un déclin significatif en Europe entre 2000 et 2015 en raison de deux pathogènes, dont _Vibrio tapetis_. Comprendre les réponses métaboliques de la palourde face à ce pathogène, en particulier les mécanismes de résistance, est essentiel pour élaborer des stratégies de gestion durable et limiter les épidémies.

# Objectif 
Une étude publiée en 2020 [Smits et al. 2020](./bibliographie/Smits_et_al_2020.pdf) a consisté à comparer différents profils protéomiques de palourdes japonaises exposées à _Vibrio tapetis_. A l'issue de quatres semaines d'expérimentation, les palourdes ont été classées comme infectées lorsque les diagnostics visuel et par PCR étaient positifs, et résistantes lorsque les diagnostics visuel et par PCR étaient négatifs. Les profils protéomiques des palourdes ont été comparés selon leur diagnostic.
Le présent projet vise à rendre plus FAIR cette étude qui n'est plus reproductible avec les nouvelles versions du logiciel PERSEUS utilisé par l'auteure, à actualiser les résultats sur la base des dernières données protéomiques disponibles et à proposer d'éventuelles améliorations quant au choix des méthodes d'analyse (ex : choix des tests statistiques). 

# Analyses
Les données sont tirées de l'article [Smits et al. 2020](./bibliographie/Smits_et_al_2020.pdf). Elles ne sont pas en libre accès et ont été fournies par l'auteure. L'ensemble du code utilisé pour l'analyse a été réalisé sur le logiciel R dans sa version V4.4.1. 

## Sélectionner les protéines pertinentes pour la comparaison des palourdes infectées et résistantes
La liste des protéines détectées chez les individus de palourdes est disponible dans le fichier [proteins.csv](input/proteins.csv). Les transcriptomes des protéines sélectionnées ont été exportés dans le fichier fasta Reads.fa pour future comparaison avec une base de données de type NCBI. Voir le [Notebook 1](./1_selection_proteines.ipynb) pour plus de détails sur la sélection des protéines pertinentes pour la comparaison des palourdes infectées et résistantes, réalisée conformément à la publication initiale. 

## Déterminer la fonction des protéines sélectionnées
Les transcriptomes des protéines sélectionnés listés dans le fichier Reads.fa ont été soumis à la base de données NCBI pour déterminer leur fonction. Voir le [Notebook 2](./2_proteines_vers_fasta.ipynb) pour plus de détails sur la méthode et l'assignation d'une fonction aux protéines qui expliquaient les différences entre les profils protéomiques des palourdes infectées et résistantes.

## Résultats et visuels
Les palourdes infectées et résistantes présentes des profils protéomiques différents...

## Méthode alternative
Une méthode alternative qui garantit l'emploi des tests statistiques adéquats (non paramétriques quand nécessaire) a été testée pour la sélection des protéines d'intérêt [Notebook 3](./3_alternative_selection_proteines.ipynb). Elle a conduit à la création d'une seconde liste de protéines disponible dans le fichier [alt_proteins.csv](input/alt_proteins.csv). 
Attention : explorer la fonction des protéines ainsi sélectionnées oblige à modifier en conséquence le fichier importé dans le [Notebook 2](./2_proteines_vers_fasta.ipynb). 

# Conclusion

# Is it FAIR ?
Les données d'entrée de l'étude sont désormais publiques. 
Le logiciel utilisé (R) permet le partage du code utilisé pour l'analyse et garantit ainsi la transparence sur les méthodes employées pour aboutir aux résultats. 
Le code ici fourni permettra d'actualiser facilement l'étude sur la base des futures données disponibles. 

### Attention
Trois des 49 loci dans le fichier final "cleaned_query_description" sont différents des 49 loci dans l'article de Smits et al. 2020 (tableau 2). Cela est lié à la présence de doublons dans le fichier original ["proteins.csv"](input/proteins.csv). Au vu de ces trois différences, il semble que les codes proposés ici ont une méthode différente de PERSEUS pour sélectionner le doublon à conserver. Ces doublons présentent néanmoins les mêmes caractéristiques, à l'exception du locus assigné et le poids moyen. De plus, ils renvoient bien à une séquence nucléotidique identique, et donc vers la même fonction de protéine assignée par NCBI. Il est donc probable que cette différence de locus et de poids moyen différents entre les deux protéines soit issu d'erreurs informatiques. Nous estimons ainsi que quel que soit le doublon éliminé, les conclusions demeurent identiques. 
