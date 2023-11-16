# TD2_MEP de Arthur HURDEBOURG

## Partie docker local

### Configuration intiale :
- Commencer par build le conteneur avec le fichier docker-compose
  docker compose up --build -d
- Ensuite on exécute le conteneur en l'ouvrant avec une interface bash :
  docker compose exec -it db bash

### Test sur le conteneur :
- On se connecte sur la base de donnees avec le login "postgres" et le mot de passe "postgres"
  psql -h localhost -p 5432 -U postgres -d postgres

- Inserer des données dans la base de données
  INSERT INTO vaccination_center (id,address,city, name, postal_code) VALUES (1, '5 rue du poisson','Paris','Centre de Paris','75000');
    INSERT INTO vaccination_center (id,address,city, name, postal_code) VALUES (2, '2 rue de Brabois','Nancy','Centre de Nancy','54000');

- Afficher le contenu de la base de données
   SELECT * FROM vaccination_center;

- On peut quitter l'interface postgres avec :
  \q puis exit

### Appel Backend
- On peut maintenant tester le backend avec notre fonction getAllCenter() :
  GET http://localhost:8081/api/center/
  ou
  curl 'http://localhost:8081/api/center/'

### Pour désactiver les docker on fait :
  docker compose down

### Source
https://github.com/jredel/jenkins-compose
