# Guide d'installation de Wan2GP (WanGP) — Windows

> Wan2GP est un générateur de vidéos / images / audio par IA, open source,
> conçu pour tourner sur des cartes graphiques grand public (dès 6 Go de VRAM).
> Dépôt officiel : https://github.com/deepbeepmeep/Wan2GP

---

## 🧩 Prérequis (à faire une seule fois)

1. **Carte graphique Nvidia RTX** (2060, 3060, 4070, 5080…) → mets à jour les
   pilotes via *GeForce Experience* ou https://www.nvidia.com/drivers
2. **Git** : https://git-scm.com/download/win (options par défaut)
3. **Miniconda** : https://docs.conda.io/en/latest/miniconda.html (Windows 64-bit)

---

## 🚀 Méthode A — Installateur automatique (recommandée)

1. Menu Démarrer → ouvre **« Anaconda Prompt »**.
2. Copie-colle ces lignes, une par une :

```bat
git clone https://github.com/deepbeepmeep/Wan2GP.git
cd Wan2GP
scripts\install.bat
```

Le script installe tout automatiquement (environnement Python, PyTorch,
dépendances, accélérateurs selon ta carte). ⏳ Plusieurs Go à télécharger.

3. Pour lancer l'application :

```bat
conda activate wan2gp
python wgp.py
```

4. Une adresse locale s'affiche (ex. `http://localhost:7860`).
   Ouvre-la dans ton navigateur → l'interface apparaît. 🎉

> À chaque utilisation suivante : ouvrir Anaconda Prompt →
> `cd Wan2GP` → `conda activate wan2gp` → `python wgp.py`

---

## 🔧 Méthode B — Manuelle (si l'installateur auto échoue)

Pour une carte **RTX 20xx à 50xx** :

```bat
git clone https://github.com/deepbeepmeep/Wan2GP.git
cd Wan2GP
conda create -n wan2gp python=3.11.14 -y
conda activate wan2gp
pip install torch==2.10.0 torchvision==0.25.0 torchaudio==2.10.0 --index-url https://download.pytorch.org/whl/cu130
pip install -r requirements.txt
python wgp.py
```

*(Pour une ancienne GTX 10xx : Python 3.10.9 + PyTorch 2.7.1 + CUDA 12.8.)*

### Options d'accélération (facultatif, RTX 40xx-50xx)

```bat
:: Sage Attention (plus rapide)
pip install https://github.com/woct0rdho/SageAttention/releases/download/v2.2.0-windows.post4/sageattention-2.2.0+cu130torch2.9.0andhigher.post4-cp39-abi3-win_amd64.whl

:: Flash Attention
pip install https://github.com/deepbeepmeep/kernels/releases/download/Flash2/flash_attn-2.8.3-cp311-cp311-win_amd64.whl
```

---

## ⭐ Méthode C — Sans terminal : Pinokio

1. Installe Pinokio : https://pinokio.computer
2. Cherche **« wan2gp »** dans son catalogue → clique sur *Install*.

---

## 📌 À retenir

- **6 Go de VRAM minimum** ; plus tu en as, plus tu peux générer long / haute qualité.
- Le **premier lancement télécharge les modèles IA** (plusieurs Go) → espace disque + patience.
- La génération est **100 % locale** sur ton PC (rien n'est envoyé sur internet).

## 🔐 Sécurité — l'essentiel, honnêtement

- **Pas de dommage matériel ni de ralentissement permanent.** Pendant la
  génération, le PC chauffe et les ventilos tournent fort : c'est normal et
  temporaire (comme un jeu exigeant).
- Projet **open source réputé et très utilisé** → risque faible, mais
  **pas « zéro risque »** : tout `pip install` télécharge du code tiers.
- Bonnes pratiques : télécharger **uniquement** depuis le dépôt officiel,
  garder **Windows Defender** actif, profiter de l'isolation offerte par `conda`.
