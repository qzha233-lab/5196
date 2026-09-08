# Group050 EDA Report Sections

## 1. Context and Data-Preparation Assurance

### Problem context and data scope

This report examines completed-order e-commerce activity in an Australian setting, with order values recorded in AUD. It supports decisions about transaction value, basket composition, customer patterns, delivery reliability and product-review outcomes. The six canonical tables contain 5,000 completed orders placed from 1 January to 31 December 2018, 15,711 order items, 500 Australian customers, 5,000 delivered shipments with outcomes through 10 January 2019, 1,000 products in ten categories and 7,000 reviews recorded through 20 February 2019. Each analysis states its observation unit, denominator and join logic. The EDA loads only these submitted standardised CSVs and does not rerun the cleaning workflow.

### Data-preparation assurance

Four material transformation decisions underpin the analytical data:

1. JSON and XML records were parsed structurally and reconciled by business key at the canonical grain (`MAP-orders-01`, `MAP-product_reviews-01`).
2. Item revenue, order price, included GST and final total were derived using the published calculation order (`MAP-order_items-06`, `MAP-orders-10`, `MAP-orders-14`, `MAP-orders-15`).
3. Source-specific dates, monetary formats and boolean alternatives were converted to published representations (`MAP-deliveries-03`–`MAP-deliveries-05`, `MAP-deliveries-10`, `MAP-deliveries-12`).
4. Text was cleaned after structured extraction; multilingual content was preserved and Latin analysis and bounded references were derived separately (`MAP-product_reviews-10`–`MAP-product_reviews-18`).

The consolidated validation register contains 66 unique checks, all of which passed. Five results are especially material to this report:

- All six outputs match the published schema, field order and types, with no empty or pandas-missing output values (`VAL-SCHEMA-01`–`VAL-SCHEMA-06`, `VAL-TYPE-01`–`VAL-TYPE-06`, `VAL-MISSING-01`–`VAL-MISSING-06`).
- Primary keys are complete and unique, and the tested foreign keys have no orphans (`VAL-PK-ORDERS-01`, `VAL-PK-ORDER-ITEMS-01`, `VAL-PROD-PK-01`, `VAL-REV-PK-01`, `VAL-DEL-01`, `VAL-FK-ORDER-ITEMS-01`, `VAL-FK-CUSTOMERS-01`, `VAL-REV-FK-01`, `VAL-DEL-02`).
- All 15,711 item revenues and 5,000 order prices and totals reconcile within A$0.01, with no double-counted GST (`VAL-ARITH-01`–`VAL-ARITH-05`).
- No delivery sequence or derived timing mismatch was found, and all 7,000 reviews follow their linked delivery (`VAL-TIME-01`–`VAL-TIME-04`).
- Text processing passed 18/18 public, 21/21 additional and 6/6 interface cases; none of 287 non-Latin-script reviews was erased (`VAL-TEXT-TEST-01`, `VAL-TEXT-MULTI-01`).

## 5. Limitations and Conclusion

### Limitations

The results are descriptive and cannot establish that segment, carrier, service level, order value or category causes an outcome. The data cover one order year and completed, delivered transactions only, excluding cancelled, abandoned and returned transactions; they therefore cannot represent the complete demand funnel or establish recurring seasonality. Delivery comparisons are uncertain because only 196 of 5,000 deliveries were late, with just five to nine late events in some Express-by-value cells. Carrier and service rates are also unadjusted for route, warehouse, season and product mix.

Reviews represent reviewers rather than all purchasers or all 15,711 items, so self-selection may bias comparisons. English reviews dominate (6,311/7,000), while 689 non-English reviews combine several languages and scripts; character length is not fully comparable, and helpful votes lack exposure time. Order total measures transaction value rather than profit, and not every subgroup difference has an uncertainty interval. Stronger decisions require multiple years of full-funnel data, cancellations and returns, margin and promotion information, review-exposure data, and time-aware adjusted or controlled analyses.

### Conclusion

The six validated tables provide a reproducible baseline across orders, customers, fulfilment, products and reviews. Order value is right-skewed and moderately associated with basket units, while segment medians differ only modestly. Segment revenue peaks vary by month, but one year cannot establish seasonality. Overall, 96.08% of shipments were not late; carrier late rates differ by less than one percentage point, and Express and Standard rates are similar, so unadjusted rates alone do not justify reallocation. Review ratings vary materially by category and review length varies with rating, but product mix, language and reviewer selection remain plausible explanations. The findings should prioritise investigation and the proposed time-aware ML questions, with adjusted analysis, uncertainty reporting and human review before operational action.
