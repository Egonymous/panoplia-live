# Panoplia — flux d'événements de monde

Ce dépôt contient **uniquement** le flux d'événements que le jeu
[Panoplia](https://egonymous.itch.io/panoplia) consulte en direct. Aucun code,
aucune donnée de jeu.

| Fichier | Qui le lit |
|---|---|
| `events.json` | **Les joueurs.** Toute modification est en ligne en quelques minutes. |
| `events-staging.json` | Les builds de test et le staging. Modifier ce fichier ne touche aucun joueur. |

Le jeu relit son flux au démarrage puis toutes les 5 minutes. Un événement est
actif dans l'intervalle demi-ouvert `[startsAt, endsAt)` (dates ISO 8601, UTC).
Si le fichier est absent, invalide ou injoignable, le jeu fonctionne
normalement, simplement sans événement.

## Publier un événement

1. Essayer d'abord dans `events-staging.json`.
2. Une fois satisfait, reporter l'entrée dans `events.json`.

Le fichier livré contient un événement d'exemple **à dates passées** (donc
inactif) qui sert de gabarit : le dupliquer et ajuster titre, texte, dates et
modificateurs.

Champs : `id`, `title` (`fr`/`en`), `text` (`fr`/`en`), `startsAt`, `endsAt`,
et `modifiers` — facultatif, tout comme chacun de ses champs (un champ absent
n'a aucun effet) : `opponentStatMultiplier`, `goldMultiplier`,
`lootRarityWeightMultipliers` (clés valides : `rarity_common`, `rarity_rare`,
`rarity_epic`, `rarity_set`).
