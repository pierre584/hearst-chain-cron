# hearst-chain-cron

La tâche horaire de la chaîne Hearst sur Sepolia, exécutée par GitHub Actions.

Chaque heure, elle prend le code de [Hearst-Corporation/hearst-connect-v1](https://github.com/Hearst-Corporation/hearst-connect-v1) (branche `v2`) et lance `scripts/demo-chain.mjs` :

1. publie dans `HearstReserveRegistry` les mois clos pas encore attestés ;
2. publie dans `HearstMiningOracle` les relevés du réseau bitcoin.

| | Adresse (Sepolia) |
|---|---|
| HearstReserveRegistry | `0x0d0756DfB37F8162Cb7bA633912772D3D4545d62` |
| HearstMiningOracle | `0x489C70Bf7892F6B0F44e318F206a5BB11C3c127e` |
| Publication (HEARST CONNECT B) | `0xc4197d502133ECAf7983663E69BA4b895831196D` |

Secret requis : `HEARST_PUBLISHER_KEY` (Settings → Secrets and variables → Actions), la clé privée du compte de publication. Lancer à la main : onglet Actions → « Hearst chain (Sepolia) » → Run workflow.
