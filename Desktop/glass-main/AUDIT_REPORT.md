## Rapport d’audit — Glass (Pickle)

### A. Résumé exécutif

- Problèmes trouvés: 17
- Critiques: webSecurity désactivé; `open-external` non filtré; clé Portkey en dur; Firebase config en dur
- Majeurs: engine Node Functions 18; version `dotenv` invalide; fuites listeners; pas de gating capture; rate limiting manquant
- Mineurs: interval non nettoyé; règles Firestore manquantes; validations IPC légères; Error Boundary absent

### B. Détails et corrections

1) `src/window/windowManager.js`: webSecurity activé (edit appliqué)
2) `src/bridge/windowBridge.js`: `open-external` filtré http/https/mailto (edit appliqué)
3) `src/features/common/ai/providers/openai.js`: suppression clé Portkey et lecture via env + validation (edit appliqué)
4) `src/features/common/services/firebaseClient.js`: config Firebase via env + validation (edit appliqué)
5) `pickleglass_web/utils/firebase.ts`: config Firebase via `NEXT_PUBLIC_*` (edit appliqué)
6) Autres recommandations: Node 20 pour Functions; `dotenv@^16.4.5`; Error Boundary; validations IPC; règles Firestore

### C. Plan d’action priorisé

- Sprint 1 (fait): sécurisation webSecurity, validation URL, Portkey env, Firebase env
- Sprint 2: Node 20 (Functions) et déploiement; cleanup listeners; rate limiting/backoff; gating capture écran/audio
- Sprint 3: Compatibilité Windows (loopback, signer, chemins)
- Sprint 4: Optimisations (AEC, intervals, tests, lint, audit deps)

### D. Variables d’environnement

- Electron (root):
  - FIREBASE_API_KEY, FIREBASE_AUTH_DOMAIN, FIREBASE_PROJECT_ID, FIREBASE_STORAGE_BUCKET, FIREBASE_MESSAGING_SENDER_ID, FIREBASE_APP_ID, FIREBASE_MEASUREMENT_ID
  - PORTKEY_API_KEY (si Portkey utilisé)
- Next (`pickleglass_web`):
  - NEXT_PUBLIC_FIREBASE_API_KEY, NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN, NEXT_PUBLIC_FIREBASE_PROJECT_ID, NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET, NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID, NEXT_PUBLIC_FIREBASE_APP_ID, NEXT_PUBLIC_FIREBASE_MEASUREMENT_ID

### E. Sujets à surveiller

- `AskView` cleanup listeners; `setInterval` tokenTracker; règles Firestore; `dotenv` version; Functions Node 20


