# Assistant Fiscal Handicap & Protection Juridique

Démo web de l'assistant fiscal RAG spécialisé IR 2026 (revenus 2025) pour les situations handicap, invalidité, tutelle, curatelle, sauvegarde de justice et habilitation familiale.

## Architecture

- **Frontend** : `index.html` statique (HTML + CSS + JS vanilla, aucun build).
- **Backend** : Edge Function Supabase `rag-answer`.
- **LLM** : Anthropic Claude Sonnet 4.6 via tool use JSON.
- **Retrieval** : recherche keyword / full-text / trigram sur 3 899 chunks officiels (BOFiP, impots.gouv, Service-Public, Légifrance).

## Déploiement

Page servie via GitHub Pages depuis `main`. L'Edge Function tourne sur `https://vwrbgbvpzhpnvrrtugpn.supabase.co/functions/v1/rag-answer`.

La clé Supabase exposée dans le HTML est la clé **anon publique** (JWT rôle anon), conçue pour le front. Les secrets (service-role, Anthropic, OpenAI) restent côté Edge.

## Test

- `hello` → accueil court
- `invalidité` → 1 question de relance précise
- `Je suis tuteur, où déclarer les frais de tutelle ?` → réponse structurée complète avec sources cliquables
