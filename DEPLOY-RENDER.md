# Déploiement Spree sur Render

## Étapes rapides

1. **Poussez votre code sur GitHub**

2. **Allez sur https://render.com**
   - Créez un compte (gratuit)
   - Connectez votre compte GitHub

3. **Créez un nouveau Web Service**
   - New > Web Service
   - Sélectionnez votre repository
   - Render détecte automatiquement `render.yaml`

4. **Configurez (si pas de render.yaml):**
   - **Environment:** Ruby
   - **Build Command:** `bundle install && bundle exec rails assets:precompile`
   - **Start Command:** `bundle exec rails server -p $PORT`

5. **Ajoutez PostgreSQL**
   - New > PostgreSQL
   - Plan: Free
   - Connectez-le à votre service

6. **Variables d'environnement:**
   - `RAILS_ENV=production`
   - `DATABASE_URL` (automatique depuis PostgreSQL)
   - `SECRET_KEY_BASE` (générez avec `rails secret`)

7. **Déployez!**

## URL finale

Votre app sera sur: `https://spree-commerce.onrender.com`

## Configuration Cloudflare Workers

Après déploiement, configurez votre Worker:
```bash
wrangler secret put BACKEND_URL
# Entrez: https://spree-commerce.onrender.com
```

