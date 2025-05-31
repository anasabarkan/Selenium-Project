🌤️ WeatherShopper E2E Automation Project

Ce projet contient des **tests automatisés end-to-end (E2E)** de la boutique en ligne [WeatherShopper](https://weathershopper.pythonanywhere.com) en utilisant **Selenium + Pytest**. Il simule l’achat automatique de produits (crèmes solaires ou hydratants) en fonction de la température affichée sur le site.

## 🎯 Objectif

- Automatiser le parcours utilisateur complet :
  1. Lire la température
  2. Choisir les bons produits
  3. Ajouter les deux produits les moins chers au panier
  4. Vérifier le panier
  5. Effectuer un paiement via Stripe
  6. Vérifier la confirmation de paiement

## 🛠️ Technologies utilisées

- Python 3
- Selenium WebDriver
- Pytest
- ChromeDriver
- `pytest-html` (pour les rapports)

## 📁 Structure du projet

```bash
projet_test/
│
├── pages/
│   ├── home.py
│   ├── moisturizers.py
│   ├── sunscreens.py
│   ├── cart.py
│   └── payment_page.py
│
├── tests/
│   └── test_happy_path.py
│
├── conftest.py
├── report.html
└── README.md
```

## 🚀 Lancer les tests

1. Installe les dépendances nécessaires :

```bash
pip install -r requirements.txt
```

2. Lance le test avec génération du rapport :

```bash
pytest --html=report.html
```

## ✅ Résultat attendu

```
✅ Panier validé : 2 articles pour un total de XXX Rs
✅ Stripe modal ouverte.
✅ Message de confirmation trouvé.
✅ Test terminé avec succès ! Paiement effectué.
```

## 📝 Notes

- Le test est basé sur des **données de test Stripe** :
  - Carte : `4242 4242 4242 4242`
  - Exp : `12/34` (entré sous forme `"1234"`)
  - CVC : `123`
- Le test est sensible au **chargement des iframes Stripe** → des `wait()` et des `send_keys()` lents sont utilisés.

## 📸 Screenshots
[Screenshot Stripe](images/stripe_after_submit.png)
[payment](images/verifaction.png.png)
[home_page :weathershopper.pythonanywhere.com](images/home_page.png)
[proudit_pages: ajouter produit au panier ](images/Produit.png)
Le test prend automatiquement une capture d'écran `stripe_after_submit.png` après la soumission du formulaire Stripe pour aider au débogage.

## 🧑‍💻 Auteur

Projet développé par [votre nom ou pseudo] pour l'apprentissage des tests E2E avec Python.
