# 🚀 Guide de Déploiement — LPA Site Web
## Sécurité + SEO + HTTPS + Google Indexation

---

## 📁 Fichiers à uploader sur votre serveur

```
/                          ← Racine du site
├── index.html             (anciennement index_lpa_final.html)
├── about.html
├── services.html
├── contact.html
├── agro-alimentaire.html
├── analyse-eau.html
├── prelevement.html
├── laboratoire.html
├── sitemap.xml            ← NOUVEAU
├── robots.txt             ← NOUVEAU
├── .htaccess              ← NOUVEAU (sécurité + HTTPS)
└── [vos images : *.jpg, *.webp, *.jpeg, etc.]
```

> ⚠️ **Renommer** `index_lpa_final.html` → `index.html` avant upload.

---

## 🔒 1. HTTPS — Activer le certificat SSL

### Chez votre hébergeur (cPanel, Hostinger, OVH, etc.)
1. Aller dans **SSL/TLS** ou **Let's Encrypt**
2. Générer un certificat gratuit pour `www.lpa-ci.com` et `lpa-ci.com`
3. Activer **HTTPS automatique** (force redirect)
4. Uploader le `.htaccess` → il gère la redirection HTTP→HTTPS

---

## 🛡️ 2. Headers de Sécurité

Le fichier `.htaccess` fourni configure automatiquement :

| Header | Protection |
|--------|-----------|
| `Strict-Transport-Security` | Force HTTPS pour 1 an |
| `X-Frame-Options: SAMEORIGIN` | Anti-clickjacking |
| `X-Content-Type-Options: nosniff` | Anti-MIME sniffing |
| `Content-Security-Policy` | Contrôle les ressources chargées |
| `Referrer-Policy` | Protège l'URL de provenance |
| `Permissions-Policy` | Bloque caméra, micro, géoloc |
| `X-XSS-Protection` | Protection XSS navigateur |

**Vérifier vos headers après déploiement :**  
→ https://securityheaders.com/?q=www.lpa-ci.com

---

## 🔍 3. SEO — Ce qui a été intégré dans chaque page

Chaque page HTML contient maintenant :

```html
<!-- Balises SEO primaires -->
<title>Titre optimisé | LPA</title>
<meta name="description" content="...">
<meta name="keywords" content="...">
<meta name="robots" content="index, follow">
<link rel="canonical" href="https://www.lpa-ci.com/page.html">

<!-- Open Graph (partage Facebook/LinkedIn) -->
<meta property="og:title" content="...">
<meta property="og:description" content="...">
<meta property="og:image" content="https://www.lpa-ci.com/LOGO LPA.jpg">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">

<!-- Données structurées JSON-LD (Google Rich Results) -->
<script type="application/ld+json">{ "@type": "Organization" ... }</script>
```

---

## 🗺️ 4. Soumettre le Sitemap à Google

### Étape 1 — Google Search Console
1. Aller sur https://search.google.com/search-console
2. Ajouter votre propriété : `https://www.lpa-ci.com`
3. **Vérifier la propriété** via fichier HTML ou DNS TXT

### Étape 2 — Soumettre le sitemap
1. Dans Search Console → **Sitemaps**
2. Entrer : `sitemap.xml`
3. Cliquer **Envoyer**

### Étape 3 — Demander l'indexation rapide
1. Dans Search Console → **Inspection d'URL**
2. Entrer chaque URL (ex: `https://www.lpa-ci.com/index.html`)
3. Cliquer **Demander l'indexation**

---

## 🌐 5. Indexation Google — robots.txt

Le fichier `robots.txt` autorise les robots de Google :
```
User-agent: *
Allow: /
Sitemap: https://www.lpa-ci.com/sitemap.xml
```

**Vérifier :** https://www.lpa-ci.com/robots.txt

---

## ✅ Checklist de vérification post-déploiement

- [ ] `https://www.lpa-ci.com` s'affiche avec le cadenas 🔒
- [ ] `http://lpa-ci.com` redirige automatiquement vers HTTPS
- [ ] `https://www.lpa-ci.com/robots.txt` accessible
- [ ] `https://www.lpa-ci.com/sitemap.xml` accessible
- [ ] https://securityheaders.com → Note A ou A+
- [ ] https://search.google.com/search-console → Sitemap soumis
- [ ] https://developers.google.com/rich-results → Données structurées validées

---

## 📞 Support

Développé par **Jonathan N'GUETTIA**  
LPA — Laboratoire Privé d'Analyse  
📍 Abidjan, Côte d'Ivoire  
📞 +225 07 87 65 23 68
