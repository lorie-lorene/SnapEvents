# SnapEvents

---
# A- Definition des Modules

## **1. Module Utilisateur**
### **Fonctionnalités :**
- **Inscription et Authentification** : via email, réseaux sociaux ou numéro de téléphone.
- **Gestion du Profil** : photo de profil, description, préférences événementielles.
- **Système d'Amis / Suivi** : ajouter des amis, suivre des organisateurs.
- **Notifications** : recevoir des alertes sur les événements et interactions.
- **Messagerie Privée** : discuter avec d’autres utilisateurs en one-to-one ou en groupe.

### **Cas d’Utilisation :**
1. Un utilisateur s'inscrit sur la plateforme via Google ou Facebook.
2. Il met à jour son profil avec une photo et une description.
3. Il suit un organisateur d’événements pour recevoir des mises à jour.
4. Il reçoit une notification lorsqu’un ami l’invite à un événement.
5. Il échange avec un autre participant via la messagerie privée.

---

## **2. Module Événements**
### **Fonctionnalités :**
- **Création d’un événement** : ajouter un titre, une description, une image de couverture, une localisation et une date.
- **Gestion des événements** : modifier/supprimer un événement, voir les participants.
- **Invitations** : inviter des amis ou des groupes à participer.
- **Découverte d’événements** : explorer les événements publics via un fil d’actualité ou une carte interactive.
- **Commentaires et Évaluations** : donner son avis et interagir avec la communauté.

### **Cas d’Utilisation :**
1. Un utilisateur crée un événement pour une soirée privée et envoie des invitations.
2. Un autre utilisateur découvre un événement via la carte interactive et s’y inscrit.
3. Après l’événement, les participants laissent des commentaires et évaluent l’expérience.

---

## **3. Module Cagnotte**
### **Fonctionnalités :**
- **Création d’une cagnotte** : l’organisateur peut créer une cagnotte liée à un événement.
- **Participation Financière** : les invités peuvent contribuer en ligne.
- **Suivi des Contributions** : voir qui a participé et combien a été récolté.
- **Retrait / Remboursement** : l’organisateur peut récupérer les fonds ou effectuer un remboursement.

### **Cas d’Utilisation :**
1. Un organisateur crée une cagnotte pour une soirée et fixe un objectif financier.
2. Les participants versent une contribution via un paiement sécurisé.
3. L’organisateur retire la somme récoltée pour financer l’événement.
4. Un invité demande un remboursement avant l’événement.

---

## **4. Module Réseau Social**
### **Fonctionnalités :**
- **Fil d’actualité** : voir les événements passés et futurs des amis.
- **Suggestions d’événements** : recommandations basées sur les préférences et la localisation.
- **Interactions sociales** : liker, commenter et partager des événements.
- **Groupes de discussion** : créer des groupes pour échanger sur un événement spécifique.

### **Cas d’Utilisation :**
1. Un utilisateur consulte le fil d’actualité et voit qu’un ami a assisté à un concert.
2. Il réagit en laissant un commentaire et partage l’événement sur son profil.
3. Il rejoint un groupe de discussion pour organiser le covoiturage jusqu’à l’événement.

---

## **5. Module Monétisation**
### **Fonctionnalités :**
- **Événements Payants** : possibilité de fixer un prix d’entrée pour un événement.
- **Vente de Billets** : achat sécurisé et génération d’un QR Code pour l’entrée.
- **Gestion des Transactions** : suivi des ventes et paiements.
- **Publicités et Partenariats** : espace dédié aux promotions d’événements.

### **Cas d’Utilisation :**
1. Un organisateur met en place un prix de 10€ pour son événement.
2. Un utilisateur achète un billet via l’application et reçoit un QR Code.
3. À l’entrée de l’événement, l’organisateur scanne le QR Code pour valider l’accès.

---

## **6. Module Notifications et Communication**
### **Fonctionnalités :**
- **Alertes Personnalisées** : rappels d’événements à venir.
- **Invitations** : notifications en temps réel pour les nouvelles invitations.
- **Messagerie Instantanée** : possibilité d’échanger avec des amis et des participants.
- **Rappels et mises à jour** : notifications sur les changements de dernière minute.

### **Cas d’Utilisation :**
1. Un utilisateur reçoit une alerte 1h avant un événement auquel il s’est inscrit.
2. Il est notifié lorsqu’un nouvel événement correspondant à ses préférences est créé.
3. Un participant discute avec l’organisateur pour poser des questions sur l’événement.

---

## **7. Expérience Utilisateur Améliorée**
### **Fonctionnalités :**
- **Mode Hors-Ligne** : possibilité de consulter les événements enregistrés sans connexion.
- **Intégration Calendrier** : synchronisation des événements avec Google Calendar ou Apple Calendar.
- **Rappels Automatiques** : ajout d’événements au calendrier avec notifications.

### **Cas d’Utilisation :**
1. Un utilisateur synchronise ses événements avec son agenda personnel.
2. Il consulte un événement même lorsqu’il n’a pas accès à Internet.
3. Il reçoit une notification automatique pour un événement enregistré.

---

# B- Description formelles  des Modules

## **Document de Conception : Module Utilisateur**

## **1. Description du Module**
Le module utilisateur permet la gestion des comptes, des profils et des interactions sociales.
 Il inclut l'inscription, l'authentification, la gestion des amis, les notifications et la messagerie privée.

## **2. Type Abstrait de Données (TAD)**
### **Utilisateur**
- **Attributs** :
  - id : String
  - nom : String
  - email : String
  - motDePasse : String (hashé)
  - photoProfil : String (URL)
  - description : String
  - preferences : Liste<String>
  - amis : Liste<String> (IDs des amis)
  - evenementsParticipe : Liste<String> (IDs des événements rejoints)
  - notifications : Liste<Notification>
  - messages : Liste<Message>
  - dateInscription : Date

### **Notification**
- **Attributs** :
  - id : String
  - utilisateurId : String
  - contenu : String
  - date : Date
  - lu : Boolean

### **Message**
- **Attributs** :
  - id : String
  - expediteurId : String
  - destinataireId : String
  - contenu : String
  - date : Date
  - lu : Boolean

## **3. Scénarios d’Utilisation**
### **Scénario 1 : Inscription d’un nouvel utilisateur**
1. L’utilisateur entre son email et son mot de passe ou utilise une connexion via un réseau social.
2. Il remplit les informations de son profil (nom, photo, préférences, description).
3. Le système enregistre l’utilisateur et génère un identifiant unique.
4. L’utilisateur est redirigé vers l’écran principal.

### **Scénario 2 : Ajout d’un ami**
1. L’utilisateur recherche un autre utilisateur par son nom ou son identifiant.
2. Il envoie une demande d’amitié.
3. L’autre utilisateur reçoit une notification et peut accepter ou refuser.
4. En cas d’acceptation, les utilisateurs apparaissent dans leur liste d’amis respective.

### **Scénario 3 : Réception et consultation d’une notification**
1. Un utilisateur est invité à un événement par un ami.
2. Une notification est générée et stockée dans sa liste de notifications.
3. L’utilisateur ouvre son application et consulte ses notifications.
4. Il clique sur la notification pour voir les détails de l’invitation.

### **Scénario 4 : Envoi d’un message privé**
1. Un utilisateur sélectionne un ami dans sa liste.
2. Il rédige un message et l’envoie.
3. Le message est stocké dans la base de données et une notification est envoyée au destinataire.
4. Le destinataire ouvre l’application et lit le message.

## **4. Définition des Collections NoSQL (MongoDB)**
### **Collection : Utilisateurs**
```json
{
  "_id": "ObjectId",
  "nom": "String",
  "email": "String",
  "motDePasse": "String",
  "photoProfil": "String",
  "description": "String",
  "preferences": ["String"],
  "amis": ["ObjectId"],
  "evenementsParticipe": ["ObjectId"],
  "notifications": [
    {
      "id": "ObjectId",
      "contenu": "String",
      "date": "Date",
      "lu": "Boolean"
    }
  ],
  "messages": ["ObjectId"],
  "dateInscription": "Date"
}
```

### **Collection : Messages**
```json
{
  "_id": "ObjectId",
  "expediteurId": "ObjectId",
  "destinataireId": "ObjectId",
  "contenu": "String",
  "date": "Date",
  "lu": "Boolean"
}
```

### **Collection : Notifications**
```json
{
  "_id": "ObjectId",
  "utilisateurId": "ObjectId",
  "contenu": "String",
  "date": "Date",
  "lu": "Boolean"
}
```

## **Document de Conception : Module Événements**

### **1. Description du module**

Le module Événements permet aux utilisateurs de créer, gérer et découvrir des événements sur la plateforme. Il facilite les interactions sociales autour des événements, incluant l'invitation de participants, la gestion des inscriptions et l'évaluation des événements.

### **2. Type Abstrait de Données (TAD)**

#### **TAD Evénement**

**Type :**

```
Evenement = (id, titre, description, imageCouverture, localisation, date, organisateur, participants, commentaires, evaluations)
```

**Opérations :**

```
- creerEvenement(titre, description, imageCouverture, localisation, date, organisateur) → Evenement
- modifierEvenement(id, titre, description, imageCouverture, localisation, date) → Evenement
- supprimerEvenement(id) → Boolean
- inviterParticipants(id, listeParticipants) → Boolean
- inscrireUtilisateur(idEvenement, idUtilisateur) → Boolean
- commenterEvenement(idEvenement, idUtilisateur, commentaire) → Commentaire
- evaluerEvenement(idEvenement, idUtilisateur, note) → Evaluation
- rechercherEvenements(filtre) → Liste<Evenement>
```

### **3. Scénarios d’utilisation**

#### **Scénario 1 : Création d’un événement**

1. L'utilisateur ouvre l'interface de création d'événement.
2. Il saisit le titre, la description, la date, l'image et la localisation.
3. Il valide la création de l'événement.
4. L'événement est sauvegardé dans la base de données et s'affiche dans son profil.

#### **Scénario 2 : Participation à un événement**

1. Un utilisateur consulte la liste des événements disponibles.
2. Il sélectionne un événement et accède aux détails.
3. Il clique sur "Participer".
4. Son ID est ajouté à la liste des participants.
5. Il reçoit une confirmation et l'événement est ajouté à son agenda.

#### **Scénario 3 : Commentaire et évaluation d'un événement**

1. Après la fin d'un événement, l'utilisateur reçoit une notification pour laisser un avis.
2. Il accède à l'événement et ajoute un commentaire.
3. Il attribue une note sur 5 étoiles.
4. Les avis et évaluations sont sauvegardés et accessibles publiquement.

### **4. Définition des Collections NoSQL (MongoDB)**

#### **Collection: events**

```json
{
  "_id": ObjectId,
  "title": "Nom de l'événement",
  "description": "Détails de l'événement",
  "image_cover": "URL de l'image",
  "location": {
    "latitude": 48.8566,
    "longitude": 2.3522,
    "address": "Adresse complète"
  },
  "date": ISODate("2025-06-15T20:00:00Z"),
  "organizer_id": ObjectId,
  "participants": [ObjectId, ObjectId],
  "comments": [
    {
      "user_id": ObjectId,
      "text": "Super événement !",
      "timestamp": ISODate("2025-06-16T10:00:00Z")
    }
  ],
  "ratings": [
    {
      "user_id": ObjectId,
      "score": 5
    }
  ]
}
```

## **Document de Conception : Module Cagnotte**  

### **1. Description du module**  
Le module Cagnotte permet aux organisateurs d'événements de collecter des fonds auprès des participants.
 Il facilite la gestion des contributions financières pour financer des événements, tout en offrant des options de suivi des paiements, de retrait et de remboursement des fonds.  

---

### **2. Type Abstrait de Données (TAD)**  

#### **TAD Cagnotte**  

**Type :**  
```
Cagnotte = (id, idEvenement, objectif, montantRecolte, organisateur, participants, contributions, statut)
Contribution = (id, idCagnotte, idParticipant, montant, date)
```

**Opérations :**  
```
- creerCagnotte(idEvenement, objectif, organisateur) → Cagnotte
- contribuerCagnotte(idCagnotte, idParticipant, montant) → Contribution
- consulterCagnotte(idCagnotte) → Cagnotte
- retirerFonds(idCagnotte, idOrganisateur) → Boolean
- rembourserContribution(idCagnotte, idContribution) → Boolean
- obtenirListeContributeurs(idCagnotte) → Liste<Contribution>
```

---

### **3. Scénarios d’utilisation**  

#### **Scénario 1 : Création d’une cagnotte**  
1. L'organisateur accède à l'événement qu'il a créé.  
2. Il choisit l’option "Créer une cagnotte".  
3. Il définit un objectif financier (ex : 500€).  
4. Il valide la cagnotte, qui est enregistrée et associée à l’événement.  

#### **Scénario 2 : Participation à une cagnotte**  
1. Un participant consulte l’événement et voit une cagnotte active.  
2. Il clique sur "Contribuer" et saisit le montant de sa participation.  
3. Il effectue le paiement via un système sécurisé.  
4. Sa contribution est enregistrée et le montant total collecté est mis à jour.  

#### **Scénario 3 : Retrait des fonds**  
1. Une fois l’objectif atteint ou l’événement terminé, l’organisateur accède à la cagnotte.  
2. Il clique sur "Retirer les fonds".  
3. Le système vérifie son identité et transfère les fonds sur son compte bancaire.  

#### **Scénario 4 : Remboursement d’un participant**  
1. Un participant demande un remboursement avant l’événement.  
2. L’organisateur consulte la liste des contributions et sélectionne celle du participant.  
3. Il déclenche le remboursement, qui est traité via le système de paiement sécurisé.  
4. Le montant total collecté est mis à jour.  

---

### **4. Définition des Collections NoSQL **  

#### **Collection: pots (cagnottes)**  

```json
{
  "_id": ObjectId,
  "event_id": ObjectId,
  "organizer_id": ObjectId,
  "goal": 500.00,
  "collected_amount": 320.00,
  "contributors": [ObjectId, ObjectId],
  "status": "active" || "closed" || "completed"
}
```

#### **Collection: contributions**  

```json
{
  "_id": ObjectId,
  "pot_id": ObjectId,
  "participant_id": ObjectId,
  "amount": 50.00,
  "date": ISODate("2025-06-10T14:00:00Z)"
}
```

---
Voici une formalisation complète du **Module Réseau Social** avec description, TAD, scénarios d’utilisation et définition des collections NoSQL.  

---

## **Document de Conception :  Module Réseau Social**  

### **1. Description du module**  
Le module Réseau Social permet aux utilisateurs d'interagir autour des événements. Il offre un fil d'actualité personnalisé, 
des recommandations basées sur les préférences et la localisation, ainsi que des interactions sociales comme les likes, 
commentaires et partages. Il facilite aussi la communication entre participants grâce aux groupes de discussion dédiés aux événements.  

---

### **2. Type Abstrait de Données (TAD)**  

#### **TAD Publication (Post)**  

**Type :**  
```
Publication = (id, idUtilisateur, type, contenu, date, reactions, commentaires, partages)
Reaction = (id, idPublication, idUtilisateur, type, date)
Commentaire = (id, idPublication, idUtilisateur, texte, date)
GroupeDiscussion = (id, idEvenement, nom, membres, messages)
Message = (id, idGroupe, idUtilisateur, texte, date)
```

**Opérations :**  
```
- creerPublication(idUtilisateur, type, contenu) → Publication
- ajouterReaction(idPublication, idUtilisateur, type) → Reaction
- ajouterCommentaire(idPublication, idUtilisateur, texte) → Commentaire
- partagerPublication(idPublication, idUtilisateur) → Boolean
- obtenirFilActualite(idUtilisateur) → Liste<Publication>
- creerGroupeDiscussion(idEvenement, nom, membres) → GroupeDiscussion
- envoyerMessage(idGroupe, idUtilisateur, texte) → Message
```

---

### **3. Scénarios d’utilisation**  

#### **Scénario 1 : Interaction avec une publication**  
1. Un utilisateur consulte son fil d’actualité et voit qu’un ami a assisté à un concert.  
2. Il laisse un commentaire et ajoute une réaction (ex: emojies( 👍❤️🔥)).  
3. Il partage l’événement sur son profil pour en informer ses amis.  

#### **Scénario 2 : Recommandation d’événements**  
1. Un utilisateur reçoit une suggestion d’événement basée sur sa localisation et ses intérêts.  
2. Il consulte les détails de l’événement et voit que plusieurs amis y participent.  
3. Il décide de s'inscrire et partage l’événement sur son fil d’actualité.  

#### **Scénario 3 : Création d’un groupe de discussion**  
1. Un utilisateur souhaite organiser un covoiturage pour un festival.  
2. Il crée un groupe de discussion lié à l’événement et invite des participants.  
3. Les membres échangent des messages pour organiser les trajets et partager des informations.  

---

### **4. Définition des Collections NoSQL (MongoDB)**  

#### **Collection: posts (publications)**  
```json
{
  "_id": ObjectId,
  "user_id": ObjectId,
  "type": "event_participation", 
  "content": "Super concert hier soir !",
  "date": ISODate("2025-06-15T20:00:00Z"),
  "reactions": [
    {
      "user_id": ObjectId,
      "type": "like",
      "date": ISODate("2025-06-16T10:00:00Z")
    }
  ],
  "comments": [
    {
      "user_id": ObjectId,
      "text": "Ça avait l'air génial !",
      "date": ISODate("2025-06-16T11:00:00Z")
    }
  ],
  "shares": [ObjectId, ObjectId]
}
```

#### **Collection: groups (groupes de discussion)**  
```json
{
  "_id": ObjectId,
  "event_id": ObjectId,
  "name": "Covoiturage Festival",
  "members": [ObjectId, ObjectId, ObjectId],
  "messages": [
    {
      "user_id": ObjectId,
      "text": "On part à 15h, qui vient avec nous ?",
      "date": ISODate("2025-06-16T12:00:00Z")
    }
  ]
}
```
V

## **Document de Conception : Module Monétisation**  

### **1. Description du module**  
Le module Monétisation permet aux organisateurs de monétiser leurs événements en fixant un prix d'entrée et en gérant les ventes de billets. 
Il intègre un système sécurisé d'achat, de génération de QR Codes pour l'accès, ainsi que la gestion des transactions et des publicités pour promouvoir les événements.  

---

### **2. Type Abstrait de Données (TAD)**  

#### **TAD Événement Payant**  
**Type :**  
```
EvenementPayant = (id, idEvenement, prix, billetsVendus)
Billet = (id, idEvenement, idUtilisateur, codeQR, statut)
Transaction = (id, idUtilisateur, idEvenement, montant, date, statut)
Publicite = (id, idEvenement, idOrganisateur, budget, duree, cible)
```

**Opérations :**  
```
- fixerPrixEvenement(idEvenement, prix) → EvenementPayant
- acheterBillet(idEvenement, idUtilisateur) → Billet
- verifierBillet(idBillet) → Boolean
- suivreTransactions(idOrganisateur) → Liste<Transaction>
- creerPublicite(idEvenement, budget, cible, duree) → Publicite
- suivrePerformancePublicite(idPublicite) → Statistiques
```

---

### **3. Scénarios d’utilisation**  

#### **Scénario 1 : Achat d’un billet**  
1. Un utilisateur consulte un événement payant et voit son prix d’entrée.  
2. Il sélectionne l’option "Acheter un billet".  
3. Le paiement est traité et un billet avec QR Code est généré.  
4. L’utilisateur retrouve son billet dans son espace personnel.  

#### **Scénario 2 : Validation de l’entrée via QR Code**  
1. Un participant se rend à l’événement avec son billet électronique.  
2. L’organisateur scanne son QR Code via l’application.  
3. Le système vérifie la validité du billet et enregistre l’entrée.  
4. L’accès est accordé et le statut du billet passe à "utilisé".  

#### **Scénario 3 : Création d’une publicité pour un événement**  
1. Un organisateur souhaite promouvoir son événement payant.  
2. Il définit un budget et une audience cible pour la publicité.  
3. La publicité est diffusée aux utilisateurs correspondant aux critères.  
4. Il consulte les statistiques de performance pour ajuster sa campagne.  

---

### **4. Définition des Collections NoSQL (MongoDB)**  

#### **Collection: paid_events (événements payants)**  
```json
{
  "_id": ObjectId,
  "event_id": ObjectId,
  "price": 10.00,
  "tickets_sold": 50
}
```

#### **Collection: tickets (billets)**  
```json
{
  "_id": ObjectId,
  "event_id": ObjectId,
  "user_id": ObjectId,
  "qr_code": "ABC123XYZ",
  "status": "valid"
}
```

#### **Collection: transactions (paiements)**  
```json
{
  "_id": ObjectId,
  "user_id": ObjectId,
  "event_id": ObjectId,
  "amount": 10.00,
  "date": ISODate("2025-06-15T20:00:00Z"),
  "status": "completed"
}
```

#### **Collection: advertisements (publicités)**  
```json
{
  "_id": ObjectId,
  "event_id": ObjectId,
  "organizer_id": ObjectId,
  "budget": 100.00,
  "target_audience": ["Paris", "18-30 ans", "Concerts"],
  "duration_days": 7,
  "stats": {
    "impressions": 5000,
    "clicks": 300,
    "conversions": 50
  }
}
```
## **Document de Conception : **Module Notifications et Communication**

### 1. **Description du Module**
permet d’envoyer des notifications personnalisées, gérer les invitations en temps réel, 
permettre la messagerie instantanée entre les utilisateurs et fournir des rappels d’événements ou des mises à jour importantes. 
L’objectif est d’améliorer l’interactivité de l’application, en assurant que les utilisateurs soient constamment informés et connectés.

### 2. **TAD (Type Abstrait de Donnée)**
Voici les éléments de TAD qui vont structurer notre module :

#### **Notification**
- **Attributs** :
  - notification_id : Identifiant unique de la notification (généré automatiquement).
  - type : Type de notification (ex : alerte événement, invitation, mise à jour).
  - message : Contenu de la notification.
  - timestamp: Date et heure de l’envoi de la notification.
  - read_status : Statut de lecture de la notification (lu/non lu).
  - user_id : Identifiant de l'utilisateur à qui la notification est destinée.
  - event_id : (optionnel) Identifiant de l’événement lié à la notification.
  - priority : Priorité de la notification (ex : haute, moyenne, basse).

#### **Invitation**
- **Attributs** :
  - invitation_id : Identifiant unique de l’invitation.
  - event_id : Identifiant de l’événement pour lequel l’invitation est envoyée.
  - sender_user_id : Identifiant de l’utilisateur qui a envoyé l’invitation.
  - receiver_user_id : Identifiant de l’utilisateur qui reçoit l’invitation.
  - status` : Statut de l’invitation (en attente, acceptée, refusée).
  - timestamp` : Date et heure de l’envoi de l’invitation.

#### **Message**
- **Attributs** :
  - message_id : Identifiant unique du message.
  - sender_user_id : Identifiant de l’utilisateur qui envoie le message.
  - receiver_user_id : Identifiant de l’utilisateur qui reçoit le message.
  - content : Contenu du message.
  - timestamp : Date et heure d’envoi du message.
  - status : Statut du message (lu/non lu).

### 3. **Scénarios**
Voici quelques scénarios pour tester les différentes fonctionnalités du module.

#### Scénario 1 : Alerte pour événement
- **Précondition** : L’utilisateur est inscrit à un événement à venir dans une heure.
- **Action** : Le système envoie une notification de rappel à l’utilisateur une heure avant l’événement.
- **Résultat attendu** : L’utilisateur reçoit une notification indiquant l’heure et le lieu de l’événement à venir.

#### Scénario 2 : Notification pour nouvel événement
- **Précondition** : Un utilisateur a défini ses préférences de type d’événements (par exemple, événements musicaux).
- **Action** : Un événement musical est créé, et l’utilisateur reçoit une notification.
- **Résultat attendu** : L’utilisateur est notifié d’un événement correspondant à ses préférences.

#### Scénario 3 : Messagerie Instantanée
- **Précondition** : Un participant souhaite poser une question à l’organisateur d’un événement.
- **Action** : Le participant envoie un message à l’organisateur via la messagerie instantanée.
- **Résultat attendu** : Le message est livré en temps réel, et l’organisateur peut répondre.

#### Scénario 4 : Invitation à un événement
- **Précondition** : Un utilisateur invite un autre utilisateur à un événement.
- **Action** : L’invitation est envoyée, et l’utilisateur reçoit une notification de l’invitation.
- **Résultat attendu** : L’utilisateur reçoit la notification et peut accepter ou refuser l’invitation.

### 4. **Définition de la Table (NoSQL)**
Puisque tu utilises MongoDB (une base de données NoSQL), voici une proposition de structure pour les collections associées :

#### **Collection : Notifications**
```json
{
  "_id": ObjectId(),
  "type": "alerte événement",
  "message": "N'oubliez pas l'événement dans 1 heure!",
  "timestamp": ISODate("2025-03-11T10:00:00Z"),
  "read_status": false,
  "user_id": ObjectId("5f89f1b0b38b8902c6c8a14d"),
  "event_id": ObjectId("5f89f1b0b38b8902c6c8a14e"),
  "priority": "haute"
}
```

#### **Collection : Invitations**
```json
{
  "_id": ObjectId(),
  "event_id": ObjectId("5f89f1b0b38b8902c6c8a14e"),
  "sender_user_id": ObjectId("5f89f1b0b38b8902c6c8a14f"),
  "receiver_user_id": ObjectId("5f89f1b0b38b8902c6c8a150"),
  "status": "en attente",
  "timestamp": ISODate("2025-03-11T09:00:00Z")
}
```

#### **Collection : Messages**
```json
{
  "_id": ObjectId(),
  "sender_user_id": ObjectId("5f89f1b0b38b8902c6c8a14f"),
  "receiver_user_id": ObjectId("5f89f1b0b38b8902c6c8a150"),
  "content": "Puis-je avoir plus de détails sur l'événement ?",
  "timestamp": ISODate("2025-03-11T09:30:00Z"),
  "status": "non lu"
}
```
## **Document de Conception : Module Expérience Utilisateur Améliorée**,

### 1. **Description du Module**
Le **Module Expérience Utilisateur Améliorée** a pour but de rendre l'application plus fluide et pratique, en offrant des fonctionnalités permettant 
une gestion des événements même sans connexion Internet, en synchronisant les événements avec les calendriers personnels des utilisateurs, 
et en envoyant des rappels automatiques. Ce module vise à garantir une expérience sans interruption et optimisée pour les utilisateurs.

### 2. **TAD (Type Abstrait de Donnée)**
Voici les entités du module, avec leur description et les types associés.

#### **Mode Hors-Ligne**
- **Description** : Permet à l’utilisateur de consulter les événements enregistrés dans l'application sans être connecté à Internet. Les informations sont stockées localement sur l'appareil de l'utilisateur.
- **Attributs** :
  - event_id : `ObjectId` (identifiant unique de l'événement).
  - event_details : `String` (détails de l'événement, comme le titre, la description).
  - timestamp : `Date` (date et heure de l'événement).
  - status : `String` (indique si l'événement est visible hors ligne, par exemple "disponible" ou "non disponible").

#### **Synchronisation Calendrier**
- **Description** : Permet à l'utilisateur de synchroniser ses événements avec des services de calendrier comme Google Calendar ou Apple Calendar.
- **Attributs** :
  - event_id : `ObjectId` (identifiant unique de l'événement).
  - calendar_id : `String` (identifiant du calendrier externe, par exemple l’ID Google Calendar ou Apple Calendar).
  - sync_status : `String` (indique si l'événement a bien été synchronisé, par exemple "synchronisé" ou "en attente").
  - timestamp : `Date` (date et heure de la synchronisation).

#### **Rappels Automatiques**
- **Description** : Envoie des rappels automatiques pour les événements synchronisés avec le calendrier. Ces rappels se déclenchent à des moments définis (par exemple, 1 heure avant l'événement).
- **Attributs** :
  - event_id : `ObjectId` (identifiant unique de l'événement).
  - reminder_time : `Date` (date et heure du rappel).
  - reminder_message : `String` (message du rappel, ex : "N'oubliez pas l'événement dans 1 heure").
  - status : `String` (statut du rappel, par exemple "envoyé", "en attente").

### 3. **Scénarios**
Voici quelques scénarios de cas d’utilisation pour tester les fonctionnalités du module.

#### Scénario 1 : Synchronisation avec le calendrier
- **Précondition** : L'utilisateur a un événement à venir et a configuré la synchronisation avec Google Calendar ou Apple Calendar.
- **Action** : L'utilisateur synchronise l'événement avec son calendrier externe.
- **Résultat attendu** : L'événement apparaît dans le calendrier de l'utilisateur, et la synchronisation est marquée comme réussie.

#### Scénario 2 : Consultation en mode hors-ligne
- **Précondition** : L'utilisateur a déjà téléchargé et enregistré les événements dans l'application.
- **Action** : L'utilisateur consulte un événement alors qu'il n'a pas de connexion Internet.
- **Résultat attendu** : L'utilisateur peut consulter les détails de l'événement, même sans connexion.

#### Scénario 3 : Rappel automatique pour un événement
- **Précondition** : Un événement est enregistré et un rappel automatique a été configuré.
- **Action** : Le rappel est déclenché 1 heure avant l'événement.
- **Résultat attendu** : L'utilisateur reçoit une notification de rappel pour l'événement à venir.

### 4. **Définition de la Table (NoSQL)**
Nous allons utiliser MongoDB pour stocker ces informations. Voici une proposition de structure pour les collections associées.

#### **Collection : Événements Hors-Ligne**
```json
{
  "_id": ObjectId(),
  "event_id": ObjectId("event_id_example"),
  "event_details": "Détails de l'événement",
  "timestamp": ISODate("2025-03-11T10:00:00Z"),
  "status": "disponible"
}
```

#### **Collection : Synchronisation Calendrier**
```json
{
  "_id": ObjectId(),
  "event_id": ObjectId("event_id_example"),
  "calendar_id": "google_calendar_id",
  "sync_status": "synchronisé",
  "timestamp": ISODate("2025-03-11T09:00:00Z")
}
```

#### **Collection : Rappels Automatiques**
```json
{
  "_id": ObjectId(),
  "event_id": ObjectId("event_id_example"),
  "reminder_time": ISODate("2025-03-11T11:00:00Z"),
  "reminder_message": "N'oubliez pas l'événement dans 1 heure.",
  "status": "envoyé"
}
```

---


