# Association Rule Analysis: Online Retail Market Basket

Minor Applied Data Science — Week 1 assignment applying the Apriori algorithm to online retail transaction data.

## What this does

Performs a Market Basket Analysis on transaction data from a UK-based online retailer to uncover which items are frequently bought together, identify strong association rules, and explore antecedent/consequent and substitute relationships between items.

## Data

- **`Online Retail BIM.dat`** — a binary incidence matrix with 20,511 transactions (invoices) and 4,175 distinct items, covering transactions between 01/12/2010 and 09/12/2011. The first column is the invoice number; remaining columns indicate whether each item was present in that transaction.
- **`Online Retail Items.docx`** — reference document mapping item codes to item names/descriptions.

Both files are expected in the working directory when knitting.

## Analysis steps

1. **Import the data** — read `Online Retail BIM.dat` into R
2. **Build the incidence matrix** — drop the invoice number column and convert to a matrix (`BIM`)
3. **Convert to transactions** — coerce `BIM` into an `arules` `transactions` object for analysis
4. **Item frequency** — plot relative item frequencies to identify the top-selling items
5. **Two-item rules** — mine association rules restricted to exactly two items and find the highest-support pairs
6. **Highest-confidence rule** — mine rules across a wider length range and identify the rule with the highest confidence
7. **Antecedents of a target item** — find which items are the strongest antecedents (predictors) of a specific item (item 4050)
8. **Consequents of a target item** — find which items are the strongest consequents (outcomes) of a specific item (item 1655)
9. **Substitute items** — check for item pairs with lift below 1, indicating a substitute relationship
10. **Rule visualization** — produce a scatter plot (support vs. confidence, shaded by lift) and a two-key plot for rules with minimum support 0.01 and minimum confidence 0.5

## Requirements

- R
- R packages: `arules`, `arulesViz`
- RStudio (or another environment that can knit `.Rmd` files)

## Usage

Place `Online Retail BIM.dat` (and `Online Retail Items.docx` for item names) in the same directory as `Apriori_Algorithm.Rmd`, then knit to HTML:

```r
rmarkdown::render("Apriori_Algorithm.Rmd", output_format = "html_document")
```

Output must be submitted as **HTML**.

## Questions answered

1. The three most frequently sold items, based on relative item frequency
2. The two-item association rule(s) with the highest support
3. The number of items in the association rule with the highest confidence
4. The most important antecedents of item 4050, and what this means
5. The most important consequents of item 1655, and what this means
6. Whether any two items act as substitutes for each other, and why
7. A scatter plot and two-key plot of association rules (min support 0.01, min confidence 0.5)
