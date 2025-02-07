# Déploiement PrestaShop avec Ansible


Ce projet automatise le déploiement d'une boutique PrestaShop en séparant le serveur web (PrestaShop) et le serveur de base de données (MySQL).

---

## Prérequis

- Ansible 2.17+
- Accès SSH par clé
- 2 serveurs Ubuntu (un pour le web, un pour MySQL)

---

## Configuration

1. **Cloner le dépôt**  
   ```bash
   git clone https://github.com/mohakadd/ansible-prestashop.git
   cd ansible-prestashop
   ```

2. **Modifier l'inventaire**  
   Editez `inventaire.yml` pour définir les adresses IP et les groupes de serveurs.

3. **Configurer les variables**  
   Mettez à jour les fichiers dans `group_vars` (`all.yml` et `db.yml`) avec vos paramètres (utilisateur, mot de passe, nom de base, etc.).

---

## Utilisation

Lancez le playbook principal :

```bash
ansible-playbook -i inventaire.yml playbook.yml
```

Ensuite, finalisez la configuration de PrestaShop via votre navigateur en accédant à l'IP du serveur web.

---

## Structure du Projet

```plaintext
.
├── ansible.cfg
├── group_vars/
│   ├── all.yml
│   └── db.yml
├── inventaire.yml
├── playbook.yml
└── roles/
    ├── mysql/
    │   ├── handlers/main.yml
    │   └── tasks/main.yml
    └── prestashop/
        ├── tasks/main.yml
        └── templates/prestashop.conf.j2
```

---

N'oubilez pas de supprimer le repertoire install après installation

```bash
sudo rm -Rf /var/www/html/prestashop/install/
```