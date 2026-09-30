# Rate Limiting

- Token Bucket: chaque client a un bucket qui se remplit de token régulièrement
	chaque appel consomme un token
	si le bucket est vide, la requête est refusée
	-> permet à un client d'avoir ponctuellement une pic de requêtes (le bucket est plein)

- Leaky Bucket: les requêtes sont empilées et dépilées à un rythme régulier
	le flux de traitement à l'intérieur du système est toujours le même quelque soit le flux d'arrivée

- Fixed window: chaque client a un nombre déterminé de requêtes sur une période de temps fixe
	ex: 100 requêtes par minute
	le compteur est réinitialisé à chaque changement de période

- Sliding window: chaque client à un nombre déterminé de requêtes sur une période de temps glissante
	ex: 100 requêtes sur les 60 dernières secondes

HTTP standard headers:
	X-RateLimit-Limit : le nombre autorisé de tentatives
	X-RateLimit-Remaining: le nombre de tentatives restantes
	X-RateLimit-Reset : QUAND le nombres de tentatives autorisées sera reset
	Retry-After: COMBIEN DE TEMPS attendre avant qu'il soit possible de faire à nouveau une requête
