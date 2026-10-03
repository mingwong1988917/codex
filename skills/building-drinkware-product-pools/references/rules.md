# Drinkware Product Pool Rules

## Data Layers

- Raw layer: full-store export and original images, unchanged.
- Specification layer: one row per effective capacity or structural specification.
- Mother layer: identical product structures merged across item IDs.
- Analysis layer: full scatter table, final Top N image pool, basic-sample list, exception lists.

## Exclusions

Exclude accessories, lids, straws, sleeves, bags, cleaning products, pet products, recharge links, multi-cup packs, cup-plus-accessory packs, gift boxes, gifts, and other combination SKUs. Preserve them only in the raw/link audit table with an exclusion reason.

## Capacity And Price

- Capacity evidence order: title, SKU text, archived detail evidence, otherwise blank.
- Split multiple capacities into multiple rows.
- Repeat a link-level page price across rows only when clearly labeled `链接级页面挂价，非容量SKU成交价`.
- Never infer a missing capacity from size adjectives, price, image proportion, or another product.

## Material

- Titanium keywords -> `钛`.
- PPSU, Tritan, PP, plastic -> `塑料`.
- Glass or borosilicate -> `玻璃`.
- Explicit ceramic cup -> `陶瓷`.
- Stainless steel, 304, 316 -> `不锈钢`.
- Insulated/thermal/cold-retention without a conflicting explicit material -> `不锈钢`.
- Ceramic coating/liner remains a coating field; the insulated body stays `不锈钢`.
- Conflicts remain blank and enter a review list.

## Heat And Display Pools

- Mother heat equals the sum of valid, uniquely attributable link-level payment counts.
- Count each link once regardless of specification rows.
- Do not allocate mixed-mother link heat without SKU-level evidence.
- Keep cumulative 80% in the full scatter table as a concentration metric.
- Use the approved display rule: fixed Top N, all mothers for very small brands, or cumulative 80% only when explicitly requested.
- Basic samples cover 3-5 important forms, materials, or capacity bands absent from Top N; do not supplement every long-tail mother.

## Scatter Point

Use one point per mother:

- X: representative link page price.
- Y: representative capacity.
- Bubble: mother payment count.
- Color: primary product form.

Select the highest-heat valid link. For multiple capacities without SKU heat, choose the lower median actual capacity and label it as a rule-based representative, not the best-selling SKU.

## Images

Every main-table row must contain an embedded image and retain its relative source path. A cutout-ready mother image must be single-product, front-facing, upright, unobstructed, not held or carried, and have a complete silhouette. Promotional text is acceptable. Exploded views, multiple cups, lifestyle hand-held images, and strong angles require replacement.
