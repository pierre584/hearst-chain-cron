# hearst-chain-cron

La tâche planifiée de la chaîne Hearst sur Sepolia, exécutée par GitHub Actions.

Toutes les 5 minutes, elle prend le code de [Hearst-Corporation/hearst-connect-v1](https://github.com/Hearst-Corporation/hearst-connect-v1) (branche `v2`) et lance `scripts/demo-chain.mjs` :

1. publie dans `HearstReserveRegistry` les mois clos pas encore attestés ;
2. publie dans `HearstMiningOracle` les relevés du réseau bitcoin, seulement s'ils comptent : nouvelle difficulté, frais de bloc en hausse ou en baisse de plus de 10 %, ou 30 minutes depuis la dernière publication. Le cours du BTC, lui, est lu en direct dans Chainlink par le contrat.

| | Adresse (Sepolia) |
|---|---|
| HearstReserveRegistry | `0x32faB21D6Ad0c01c62b3076409b7fAd802007144` |
| HearstMiningOracle | `0x489C70Bf7892F6B0F44e318F206a5BB11C3c127e` |
| Publication (HEARST CONNECT B) | `0xc4197d502133ECAf7983663E69BA4b895831196D` |

Le dépôt est public pour que GitHub Actions soit illimité ; la clé n'y figure pas. Secrets requis : `HEARST_PUBLISHER_KEY` et `HEARST_RPC_URL` (accès Alchemy Sepolia) (Settings → Secrets and variables → Actions), la clé privée du compte de publication. Lancer à la main : onglet Actions → « Hearst chain (Sepolia) » → Run workflow.
