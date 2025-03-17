# Dictionnaire de données de l'application de gestion agricole

## 1. Utilisateurs

### **Table `User`**
| Champ         | Type       | Description | Contraintes |
|--------------|-----------|-------------|-------------|
| `id`         | UUID      | Identifiant unique de l'utilisateur | Clé primaire, auto-généré |
| `name`        | VARCHAR    | Nom complet de l'utilisateur | Non nul |
| `email_address`      | VARCHAR    | Adresse e-mail de l'utilisateur | Unique, non nul |
| `password` | Hash     | Stockage sécurisé du mot de passe | Non nul |
| `creation_date` | TIMESTAMP | DATE d'inscription de l'utilisateur | Valeur par défaut: NOW() |
| `role`       | TEXT      | Rôle de l'utilisateur (`admin`, `agriculteur`) | Valeur par défaut: `agriculteur` |

---

## 2. Terrains

### **Table `Land`**
| Champ         | Type       | Description | Contraintes |
|--------------|-----------|-------------|-------------|
| `id`         | UUID      | Identifiant unique | Clé primaire, auto-généré |
| `name`        | VARCHAR    | Nom ou numéro du terrain | Non nul |
| `area`    | NUMERIC     | Surface du terrain en hectares ou mètres carrés | Non nul, valeur positive |
| `id_user` | UUID  | Référence à l'utilisateur propriétaire | Clé étrangère vers `User(id)` |
| `creation_date` | TIMESTAMP | DATE d'ajout du terrain | Valeur par défaut: NOW() |
| `modification_date` | TIMESTAMP | DATE de dernière mise à jour | Valeur par défaut: NOW(), mise à jour automatique |

---

## 3. Espaces de Crop

### **Table `CultivationSpace`**
| Champ         | Type       | Description | Contraintes |
|--------------|-----------|-------------|-------------|
| `id`         | UUID      | Identifiant unique | Clé primaire, auto-généré |
| `name`        | VARCHAR    | Nom de l'espace de culture | Non nul |
| `type`       | TEXT      | Type d'espace (`rizière`, `champ`, `verger`, `potager`) | Enum limité aux valeurs prédéfinies |
| `id_land` | UUID      | Référence au terrain | Clé étrangère vers `Land(id)` |
| `creation_date` | TIMESTAMP | DATE d'ajout de l'espace de culture | Valeur par défaut: NOW() |
| `modification_date` | TIMESTAMP | DATE de dernière mise à jour | Valeur par défaut: NOW(), mise à jour automatique |

---

## 4. Planches de Crop

### **Table `CultivationPlot`** (Uniquement pour les potagers)
| Champ         | Type      | Description | Contraintes |
|--------------|----------|-------------|-------------|
| `id`         | UUID     | Identifiant unique | Clé primaire, auto-généré |
| `name`        | VARCHAR   | Nom de la planche | Non nul |
| `id_cultivation_space` | UUID | Référence à l'espace de culture | Clé étrangère vers `CultivationSpace(id)` |
| `creation_date` | TIMESTAMP | DATE d'ajout de la planche de culture | Valeur par défaut: NOW() |

---

## 5. Cultures

### **Table `Crop`**
| Champ         | Type      | Description | Contraintes |
|--------------|----------|-------------|-------------|
| `id`         | UUID     | Identifiant unique | Clé primaire, auto-généré |
| `name`        | VARCHAR   | Nom de la culture | Non nul |
| `variety`    | VARCHAR   | Variété de la culture | Nullable |
| `planting_date` | DATE | DATE de plantation | Non nulle |
| `harvest_date` | DATE | DATE estimée ou réelle de récolte | Nullable |
| `status` | TEXT | Statut (`en croissance`, `récolté`, `malade`, etc.) | Valeur par défaut: `en croissance` |
| `id_cultivation_space` | UUID | Référence à l'espace de culture | Clé étrangère vers `CultivationSpace(id)` |
| `id_cultivation_plot` | UUID (nullable) | Référence à la planche | Clé étrangère vers `CultivationPlot(id)`, nullable |
| `creation_date` | TIMESTAMP | DATE d'ajout | Valeur par défaut: NOW() |

---

Ce dictionnaire de données a été mis à jour avec les contraintes pour chaque champ. D'autres ajouts peuvent être faits si nécessaire.
