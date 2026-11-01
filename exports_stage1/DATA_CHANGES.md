# Data changes and identity decision

## Applied in a separate snapshot
Two AOTY nominated labels changed from 0 to 1: Lana Del Rey in season 2019 and Chappell Roan in season 2024. Official sources confirm both; neither won flag changes. apply_confirmed_label_fixes.py requires the original hash, changes only these labels, adds one to each artist's prior_noms in strictly later seasons, and adds one to prior_noms_same_cat only for AOTY in later seasons. It never injects current-season nominations into predictors.

83 cells / 74 rows change: 2 labels, 72 prior_noms values and 9 prior_noms_same_cat values. See data_corrections/change_log.csv and change_manifest.json. No candidate is added and no original file is overwritten. This is a partial data repair, not a complete identity audit.

The corrected snapshot hash is 08b470c9b4f7d4fbaf4da55b39da88b4cb29c8cbfd47181310bf2940e02e0d76. Original results retain f2f8a3af293485500c7a792ed333bffaf7671aa075ef49f4f193633bb9d6b62c. All eight categories' training covariates are affected by Lana's prior_noms in later seasons. Therefore all 24 fits must be recomputed for corrected reporting. Cosmetic notebook changes preserve the old signature; data corrections necessarily change it.

## Silk Sonic: confirmed processing error; repair pending identity convention
Raw Billboard credit is `Silk Sonic (Bruno Mars & Anderson .Paak)`. The snapshot splits it into `silksonicbrunomars` / `Silk Sonic (Bruno Mars` and `andersonpaak` / `Anderson .Paak)`, while a separate `brunomars` series remains. In season 2021, the malformed group and Anderson rows each have 2 Hot 100 entries and 35 weeks; Bruno's standalone row has 0. The historical work table credits Silk Sonic, so its winner key is absent in the Stage 1 pool. This is not evidence the winner never charted.

Do not merely set Bruno and Anderson's winner flags, or rename the malformed row: chart exposure, identity-based prior history, group/member duplication and other awards must follow the same convention. silk_sonic_snapshot_audit.csv lists affected source rows and silk_sonic_raw_credits.csv the raw chart records.

The collaboration rule is accepted: credit every participating artist on a winning work. The remaining question is whether a named group is one artist/act or whether its members are also separately credited. Chat B currently keeps bands as bands. Recommended consistent extension: Silk Sonic as one named act; separately named collaborations credit all named acts. If Bruno Mars and Anderson .Paak should each receive Silk Sonic credit, implement a shared membership crosswalk across BOTH stages and avoid counting the group as a third participant. This choice changes targets and features; it has not been silently made here.

## Integration impact
The corrected labels already exist in B's work mapping; B reconstructs prior recognition from those work links. Its chart features still use the old artist snapshot, hence Silk Sonic affects both stages. All Stage 1 original-snapshot forecasts sent to B are explicitly provisional. No corrected-data forecast has been generated. No new labels should be written into old prediction exports and then described as retrained results.
