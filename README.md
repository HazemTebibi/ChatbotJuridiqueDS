 
            CHATBOT JURIDIQUE RAG - DROIT DU TRAVAIL FRANÇAIS


Assistant virtuel spécialisé en droit du travail français utilisant la 
technologie RAG (Retrieval-Augmented Generation).

 
PRÉREQUIS
 

- Python 3.8 ou supérieur
- pip (gestionnaire de paquets Python)
- Compte Google (pour Google Colab)
- Clé API Gemini (optionnelle) : https://makersuite.google.com/app/apikey

 
INSTALLATION ET EXÉCUTION
 

 
OPTION 1 : Google Colab (Recommandé)
 

1. Ouvrir Google Colab : https://colab.research.google.com

2. Créer un nouveau notebook

3. Copier-coller tout le contenu du fichier Python dans une cellule

4. Configurer la clé API (optionnel) :
   - Menu gauche : Secrets (icône clé)
   - Ajouter : OPEN_AI_KEY = votre clé Gemini
   
5. Exécuter : Runtime > Run all

6. Attendre ~5-7 minutes (installation automatique)

7. Cliquer sur le lien Gradio généré

 
OPTION 2 : Installation Locale
 

1. Créer un environnement virtuel :
   
   python -m venv venv

2. Activer l'environnement :
   
   Windows :
   venv\Scripts\activate
   
   Linux/Mac :
   source venv/bin/activate

3. Installer les dépendances :
   
   pip install langchain==0.3.0 langchain-community==0.3.0 langchain-huggingface
   pip install langchain-text-splitters sentence-transformers transformers
   pip install faiss-cpu pypdf PyPDF2 pdfplumber
   pip install beautifulsoup4 lxml chromadb gradio==4.13.0
   pip install python-dotenv unidecode pandas matplotlib seaborn requests
   pip install huggingface-hub>=0.20.0 google-generativeai

4. Créer un fichier .env (optionnel) :
   
   echo "OPEN_AI_KEY=votre_clé_api" > .env

5. Exécuter le programme :
   
   python rag_ds.py


Le programme va automatiquement :
- Installer les dépendances manquantes
- Créer les dossiers nécessaires (data/, data/raw/, etc.)
- Créer le corpus juridique
- Construire la base vectorielle
- Lancer l'interface Gradio

Durée totale : ~7-10 minutes

 
UTILISATION
 

 
Questions acceptées ✓
 
- "Quelle est la durée légale du travail ?"
- "Quels sont mes droits au congé payé ?"
- "Qu'est-ce que le harcèlement moral ?"
- "Comment fonctionne le licenciement économique ?"

 
Questions refusées ✗
 
- "Comment créer une SARL ?" (hors périmètre)
- "Quel est le taux de TVA ?" (hors périmètre)

 
DÉMONSTRATION
 

Le programme inclut 4 tests automatiques qui s'exécutent avant le lancement 
de l'interface.

Pour tester manuellement dans le code :

result = rag_pipeline.process_query("Votre question ici")
print(result['response'])

 
RÉSOLUTION DE PROBLÈMES
 

Erreur d'installation :
    pip install --upgrade pip
    pip install [nom_du_module_manquant]

Port déjà utilisé :
    Le script détecte automatiquement un port libre (7860-7870)

Gradio ne se lance pas :
    pip install gradio==4.13.0 --force-reinstall

 
FICHIERS GÉNÉRÉS AUTOMATIQUEMENT
 

Lors de l'exécution, le programme crée :

./
├── data/
│   ├── raw/
│   │   ├── code_travail_sample.json
│   │   └── cnil_guides.json
│   ├── processed/
│   │   ├── metrics.png
│   │   ├── corpus_distribution.png
│   │   └── rapport_evaluation.txt
│   └── vectorstore/
│       ├── index.faiss
│       └── index.pkl

Note : Ces fichiers sont créés automatiquement, ne pas les créer manuellement.

 
AVERTISSEMENT
 

Ce chatbot est éducatif uniquement. Il ne constitue pas un avis juridique. 
Consultez un avocat pour des conseils personnalisés.

 
DÉMARRAGE RAPIDE
 

 
Google Colab :
 
1. Ouvrir colab.research.google.com
2. Copier le code Python dans une cellule
3. Runtime > Run all
4. Attendre 5-7 min
5. Cliquer sur le lien Gradio

 
Local :
 
python -m venv venv
source venv/bin/activate
pip install [toutes les dépendances ci-dessus]
python rag_ds.py

 
C'est tout !
 
