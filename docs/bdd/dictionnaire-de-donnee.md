# Dictionnaire de données de l'application de gestion agricole

## 1. Utilisateurs

### **Table `User`**
| Champ         | Type       | Description | Contraintes |
|--------------|-----------|-------------|-------------|
| `id`         | UUID      | Identifiant unique de l'utilisateur | Clé primaire, auto-généré |
| `name`       | VARCHAR    | Nom complet de l'utilisateur | Non nul |
| `email_address` | VARCHAR    | Adresse e-mail de l'utilisateur | Unique, non nul |
| `password` | Hash     | Stockage sécurisé du mot de passe | Non nul |
| `creation_date` | TIMESTAMP | Date d'inscription de l'utilisateur | Valeur par défaut: NOW() |
| `role`       | TEXT      | Rôle de l'utilisateur (`admin`, `agriculteur`) | Valeur par défaut: `agriculteur` |

---

## 2. Terrains

### **Table `Land`**
| Champ         | Type       | Description | Contraintes |
|--------------|-----------|-------------|-------------|
| `id`         | UUID      | Identifiant unique | Clé primaire, auto-généré |
| `name`       | VARCHAR    | Nom ou numéro du terrain | Non nul |
| `area`       | NUMERIC     | Surface du terrain en hectares ou mètres carrés | Non nul, valeur positive |
| `id_user` | UUID  | Référence à l'utilisateur propriétaire | Clé étrangère vers `User(id)` |
| `creation_date` | TIMESTAMP | Date d'ajout du terrain | Valeur par défaut: NOW() |
| `modification_date` | TIMESTAMP | Date de dernière mise à jour | Valeur par défaut: NOW(), mise à jour automatique |

---

## 3. Espaces de Culture

### **Table `CultivationSpace`**
| Champ         | Type       | Description | Contraintes |
|--------------|-----------|-------------|-------------|
| `id`         | UUID      | Identifiant unique | Clé primaire, auto-généré |
| `name`       | VARCHAR    | Nom de l'espace de culture | Non nul |
| `type`       | TEXT      | Type d'espace (`rizière`, `champ`, `verger`, `potager`) | Enum limité aux valeurs prédéfinies |
| `id_land` | UUID      | Référence au terrain | Clé étrangère vers `Land(id)` |
| `creation_date` | TIMESTAMP | Date d'ajout de l'espace de culture | Valeur par défaut: NOW() |
| `modification_date` | TIMESTAMP | Date de dernière mise à jour | Valeur par défaut: NOW(), mise à jour automatique |

---

## 4. Planches de Culture

### **Table `CultivationPlot`** (Uniquement pour les potagers)
| Champ         | Type      | Description | Contraintes |
|--------------|----------|-------------|-------------|
| `id`         | UUID     | Identifiant unique | Clé primaire, auto-généré |
| `name`       | VARCHAR   | Nom de la planche | Non nul |
| `id_cultivation_space` | UUID | Référence à l'espace de culture | Clé étrangère vers `CultivationSpace(id)` |
| `creation_date` | TIMESTAMP | Date d'ajout de la planche de culture | Valeur par défaut: NOW() |

---

## 5. Cultures

### **Table `Crop`**
| Champ         | Type      | Description | Contraintes |
|--------------|----------|-------------|-------------|
| `id`         | UUID     | Identifiant unique | Clé primaire, auto-généré |
| `name`       | VARCHAR   | Nom de la culture | Non nul |
| `variety`    | VARCHAR   | Variété de la culture | Nullable |
| `planting_date` | DATE | Date de plantation | Non nulle |
| `harvest_date` | DATE | Date estimée ou réelle de récolte | Nullable |
| `status` | TEXT | Statut (`en croissance`, `récolté`, `malade`, etc.) | Valeur par défaut: `en croissance` |
| `id_cultivation_space` | UUID | Référence à l'espace de culture | Clé étrangère vers `CultivationSpace(id)` |
| `id_cultivation_plot` | UUID (nullable) | Référence à la planche | Clé étrangère vers `CultivationPlot(id)`, nullable |
| `creation_date` | TIMESTAMP | Date d'ajout | Valeur par défaut: NOW() |

---

## Relations Merise (Cardinalités et Verbes d'Association)

- Un **User** (1,1) *possède* plusieurs **Land** (0,n)
- Un **Land** (1,1) *contient* plusieurs **CultivationSpace** (0,n)
- Un **CultivationSpace** (1,1) *peut avoir* plusieurs **CultivationPlot** (0,n)
- Un **CultivationSpace** (1,1) *peut accueillir* plusieurs **Crop** (0,n)
- Une **CultivationPlot** (0,n) *peut contenir* plusieurs **Crop** (0,n)
- Un **Crop** (1,1) *est cultivé sur* un **CultivationSpace** (1,1) ou une **CultivationPlot** (0,1)

Ce dictionnaire de données inclut désormais les relations entre entités selon la méthode Merise avec les cardinalités et verbes d'association.
