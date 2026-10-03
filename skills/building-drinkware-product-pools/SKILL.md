---
name: building-drinkware-product-pools
description: Use when collecting, cleaning, restructuring, validating, or updating Tmall drinkware product exports, especially when links contain multiple capacities, duplicate product IDs, accessories, bundles, embedded images, payment-count heat metrics, Top N product image pools, or mother/spec-level analysis tables.
---

# Building Drinkware Product Pools

## Core Principle

Build an auditable full product pool first, then derive the analysis and image pools. Never replace missing evidence with guesses.

## Required Workflow

1. Preserve the full-store export and original image archive unchanged.
2. Inspect source columns and state whether price and heat are link-level, SKU-level, third-party, or inferred.
3. Exclude accessories, non-drinkware, bundles, gifts, and mixed packs before creating the effective pool.
4. Split each valid link into one row per effective capacity or structural specification. Do not split colors.
5. Merge identical structures into a mother product while retaining each row's source item ID, link, image, price, and heat evidence.
6. Treat mixed-mother links conservatively: keep valid specs, but do not allocate link-level payment counts across mothers without SKU evidence.
7. Create a full mother scatter table with one point per mother. Use the highest-heat valid link and a documented representative-capacity rule.
8. Build the final display pool using the user-approved Top N rule. Keep cumulative 80% as a concentration metric unless the user explicitly chooses it as the display rule.
9. Embed an image in every main-table row. Separately judge cutout suitability: front-facing, upright, unobstructed, no hand carrying/holding, single product, complete silhouette.
10. Produce missing-capacity, missing-material, price-review, and image-supplement lists only where evidence is genuinely absent.

Read [references/rules.md](references/rules.md) before classifying products or images.

## Verification

Run `scripts/validate_pool.py --help`, then validate each final analysis workbook. Confirm:

- expected Top N sheet and row count;
- cumulative heat share remains in the scatter sheet;
- every hot-pool row has an embedded image;
- item IDs remain text;
- no spreadsheet formula errors;
- facts, judgments, and unresolved fields are clearly separated.

## Stop Conditions

Do not finalize if link-level price is described as capacity-specific, mixed-link heat is duplicated across mothers, accessories remain in the effective pool, or images exist only in a folder and not in the workbook.
