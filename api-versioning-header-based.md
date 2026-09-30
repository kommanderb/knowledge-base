# API Versioning - Header based

-> Header: My-Api-Version
	inclus par le client dans sa requête
	parsé par un middleware avant d'atteindre le Controller

-> Pouvoir identifier la version courante de l'API
-> Associer une version à une clé API
-> Les versions sont des dates
-> Toutes les versions sont centralisées dans une classe

-> Middleware de transformation de la réponse
