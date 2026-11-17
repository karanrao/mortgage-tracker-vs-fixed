# Tracker vs Fixed Mortgage: what-if simulator

A single-file, mobile-friendly tool that compares the interest you'd pay on a UK **tracker** mortgage (Bank of England base rate + a premium) with a **fixed-rate** mortgage, and lets you simulate the base rate going up and down over time.

**Try it:** [agenticdirect.io/projects/mortgage-tracker-vs-fixed/simulator](https://agenticdirect.io/projects/mortgage-tracker-vs-fixed/simulator) · [project write-up](https://agenticdirect.io/projects/mortgage-tracker-vs-fixed)

No build step, no dependencies, no data leaves the browser. Open `index.html` in any browser, or host it on any static host (GitHub Pages works as-is).

## What it does

- **Inputs:** loan amount, remaining term, comparison period (e.g. a 2- or 5-year deal), repayment or interest-only, base rate today, tracker premium, fixed rate.
- **Base-rate scenarios:** start from a preset (Flat, Gradual cuts, Shock then ease, Steady rises, Rollercoaster) or build your own timeline of rate changes. Each change is "in year X, month Y, move base by ±0.25% steps". The base rate can't go below 0%.
- **Results:**
  - which option is cheaper over the period, and by how much
  - the **break-even base rate** (the tracker wins only if base averages below it)
  - starting and peak monthly payments, and the balance at the end
  - charts of the rate path, cumulative interest and monthly payments; touch and slide across a chart to read any month
  - a year-by-year table
- **Sharing:** the full scenario is saved in the URL (`#…`), so a hosted copy can be shared with the exact inputs.

## How it calculates

- Monthly amortisation over the remaining term; interest accrues monthly at annual rate ÷ 12.
- **Tracker:** each base-rate change takes effect from the start of the chosen month. The monthly payment is recalculated on the outstanding balance over the remaining months, as UK lenders do.
- **Fixed:** constant payment for the whole comparison period.
- **Break-even base rate:** the constant base rate at which both options pay the same interest over the period, found by bisection.

## Limitations

This is an illustration, not financial advice. Real products may have fees, collars, early repayment charges, reversion to a standard variable rate after the deal, and slightly different interest calculation methods (e.g. daily interest). None of these are modelled.

## Licence

MIT. See [LICENSE](LICENSE).
