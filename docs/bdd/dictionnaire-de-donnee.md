# Dictionnaire de données de l'application de gestion agricole

## 1. Utilisateurs

### **Table `Utilisateur`**
| Champ         | Type       | Description | Contraintes |
|--------------|-----------|-------------|-------------|
| `id`         | UUID      | Identifiant unique de l'utilisateur | Clé primaire, auto-généré |
| `nom`        | String    | Nom complet de l'utilisateur | Non nul |
| `email`      | String    | Adresse e-mail de l'utilisateur | Unique, non nul |
| `mot_de_passe` | Hash     | Stockage sécurisé du mot de passe | Non nul |
| `date_creation` | DateTime | Date d'inscription de l'utilisateur | Valeur par défaut: NOW() |
| `role`       | Text      | Rôle de l'utilisateur (`admin`, `agriculteur`) | Valeur par défaut: `agriculteur` |

---

## 2. Terrains

### **Table `Terrain`**
| Champ         | Type       | Description | Contraintes |
|--------------|-----------|-------------|-------------|
| `id`         | UUID      | Identifiant unique | Clé primaire, auto-généré |
| `nom`        | String    | Nom ou numéro du terrain | Non nul |
| `surface`    | Float     | Surface du terrain en hectares ou mètres carrés | Non nul, valeur positive |
| `utilisateur_id` | UUID  | Référence à l'utilisateur propriétaire | Clé étrangère vers `Utilisateur(id)` |
| `date_creation` | DateTime | Date d'ajout du terrain | Valeur par défaut: NOW() |
| `date_modification` | DateTime | Date de dernière mise à jour | Valeur par défaut: NOW(), mise à jour automatique |

---

## 3. Espaces de Culture

### **Table `EspaceCulture`**
| Champ         | Type       | Description | Contraintes |
|--------------|-----------|-------------|-------------|
| `id`         | UUID      | Identifiant unique | Clé primaire, auto-généré |
| `nom`        | String    | Nom de l'espace de culture | Non nul |
| `type`       | Text      | Type d'espace (`rizière`, `champ`, `verger`, `potager`) | Enum limité aux valeurs prédéfinies |
| `terrain_id` | UUID      | Référence au terrain | Clé étrangère vers `Terrain(id)` |
| `date_creation` | DateTime | Date d'ajout de l'espace de culture | Valeur par défaut: NOW() |
| `date_modification` | DateTime | Date de dernière mise à jour | Valeur par défaut: NOW(), mise à jour automatique |

---

## 4. Planches de Culture

### **Table `PlancheCulture`** (Uniquement pour les potagers)
| Champ         | Type      | Description | Contraintes |
|--------------|----------|-------------|-------------|
| `id`         | UUID     | Identifiant unique | Clé primaire, auto-généré |
| `nom`        | String   | Nom de la planche | Non nul |
| `espace_culture_id` | UUID | Référence à l'espace de culture | Clé étrangère vers `EspaceCulture(id)` |
| `date_creation` | DateTime | Date d'ajout de la planche de culture | Valeur par défaut: NOW() |

---

## 5. Cultures

### **Table `Culture`**
| Champ         | Type      | Description | Contraintes |
|--------------|----------|-------------|-------------|
| `id`         | UUID     | Identifiant unique | Clé primaire, auto-généré |
| `nom`        | String   | Nom de la culture | Non nul |
| `variete`    | String   | Variété de la culture | Nullable |
| `date_plantation` | Date | Date de plantation | Non nulle |
| `date_recolte` | Date | Date estimée ou réelle de récolte | Nullable |
| `statut` | Text | Statut (`en croissance`, `récolté`, `malade`, etc.) | Valeur par défaut: `en croissance` |
| `espace_culture_id` | UUID | Référence à l'espace de culture | Clé étrangère vers `EspaceCulture(id)` |
| `planche_id` | UUID (nullable) | Référence à la planche | Clé étrangère vers `PlancheCulture(id)`, nullable |
| `date_creation` | DateTime | Date d'ajout | Valeur par défaut: NOW() |

---

Ce dictionnaire de données a été mis à jour avec les contraintes pour chaque champ. D'autres ajouts peuvent être faits si nécessaire.
