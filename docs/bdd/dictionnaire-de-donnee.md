# Dictionnaire de données de l'application de gestion agricole

## 1. Utilisateurs

### **Table `Utilisateur`**
| Champ         | Type       | Description |
|--------------|-----------|-------------|
| `id`         | UUID      | Identifiant unique de l'utilisateur |
| `nom`        | String    | Nom complet de l'utilisateur |
| `email`      | String    | Adresse e-mail de l'utilisateur |
| `mot_de_passe` | Hash     | Stockage sécurisé du mot de passe |
| `date_creation` | DateTime | Date d'inscription de l'utilisateur |
| `role`       | Text      | Rôle de l'utilisateur (`admin`, `agriculteur`) |

---

## 2. Terrains

### **Table `Terrain`**
| Champ         | Type       | Description |
|--------------|-----------|-------------|
| `id`         | UUID      | Identifiant unique |
| `nom`        | String    | Nom ou numéro du terrain |
| `surface`    | Float     | Surface du terrain en hectares ou mètres carrés |
| `utilisateur_id` | UUID  | Référence à l'utilisateur propriétaire |
| `date_creation` | DateTime | Date d'ajout du terrain |
| `date_modification` | DateTime | Date de dernière mise à jour |

---

## 3. Espaces de Culture

### **Table `EspaceCulture`**
| Champ         | Type       | Description |
|--------------|-----------|-------------|
| `id`         | UUID      | Identifiant unique |
| `nom`        | String    | Nom de l'espace de culture |
| `type`       | Text      | Type d'espace (`rizière`, `champ`, `verger`, `potager`) |
| `terrain_id` | UUID      | Référence au terrain |
| `date_creation` | DateTime | Date d'ajout de l'espace de culture |
| `date_modification` | DateTime | Date de dernière mise à jour |

---

## 4. Planches de Culture

### **Table `PlancheCulture`** (Uniquement pour les potagers)
| Champ         | Type      | Description |
|--------------|----------|-------------|
| `id`         | UUID     | Identifiant unique |
| `nom`        | String   | Nom de la planche |
| `espace_culture_id` | UUID | Référence à l'espace de culture |
| `date_creation` | DateTime | Date d'ajout de la planche de culture |

---

## 5. Cultures

### **Table `Culture`**
| Champ         | Type      | Description |
|--------------|----------|-------------|
| `id`         | UUID     | Identifiant unique |
| `nom`        | String   | Nom de la culture (ex: Riz, Blé, Tomate) |
| `variete`    | String   | Variété de la culture |
| `date_plantation` | Date | Date de plantation ou semis |
| `date_recolte` | Date | Date estimée ou réelle de récolte |
| `statut` | Text | Statut (`en croissance`, `récolté`, `malade`, etc.) |
| `espace_culture_id` | UUID | Référence à l'espace de culture |
| `planche_id` | UUID (nullable) | Référence à la planche (si applicable) |
| `date_creation` | DateTime | Date d'ajout |

---

## 6. Actions Agricoles

### **Table `ActionAgricole`**
| Champ        | Type       | Description |
|-------------|-----------|-------------|
| `id`        | UUID      | Identifiant unique |
| `action_personnalisee_id` | UUID | Référence à une action personnalisée |
| `detail`    | String    | Description spécifique de l'action |
| `date`      | Date      | Date de réalisation |
| `commentaire` | Text    | Notes ou observations |
| `espace_culture_id` | UUID | Référence à l'espace de culture |
| `planche_id` | UUID (nullable) | Référence à la planche (si applicable) |
| `culture_id` | UUID (nullable) | Référence à une culture (si applicable) |

---

## 7. Actions Personnalisées

### **Table `ActionPersonnalisee`**
| Champ         | Type       | Description |
|--------------|-----------|-------------|
| `id`         | UUID      | Identifiant unique |
| `nom`        | String    | Nom de l'action |
| `description` | Text    | Détail sur l'action |
| `utilisateur_id` | UUID | Référence à l'utilisateur créateur |

---

## 8. Observations et Météo

### **Table `Observation`**
| Champ         | Type       | Description |
|--------------|-----------|-------------|
| `id`         | UUID      | Identifiant unique |
| `date`       | Date      | Date de l'observation |
| `temperature` | Float    | Température moyenne du jour |
| `pluviometrie` | Float   | Précipitations en mm |
| `ravageurs` | String    | Observations sur les ravageurs |
| `maladies`  | String    | Problèmes identifiés |
| `espace_culture_id` | UUID | Référence à l'espace de culture |
| `commentaire` | Text    | Notes supplémentaires |
