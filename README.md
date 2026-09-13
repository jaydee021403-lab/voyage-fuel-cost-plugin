# Voyage Cost Calculation for Drifting/Holding (by PDM)

Private GitHub marketplace for teammate testing of the Codex plugin `voyage-fuel-cost`.

## What the plugin does

It compares MAIN and every visible alternative route from PVP/AROS screenshots. It:

- calculates total fuel cost and total ME + AUX consumption for each route;
- detects every route-specific drifting/holding interval from red `DATE` rows, low speeds around 1 kt or below, or UTC intervals supplied in chat;
- deducts each interval only from the route where it occurs;
- shows the holding schedule and each consumption/cost deduction;
- shows signed ALT-minus-MAIN differences, where negative means cheaper and positive means more expensive;
- uses the latest exact-vessel RAS-411 workbook only when curve reconstruction or validation is necessary.

The repository intentionally contains no vessel screenshots, Excel workbooks, fuel prices, or voyage data.

## Install for teammate testing

Each teammate needs GitHub access to this private repository, working Git credentials for that account, and the Codex CLI installed. Do not share a password or personal access token with teammates; each person should authenticate their own GitHub account.

```text
codex plugin marketplace add jaydee021403-lab/voyage-fuel-cost-plugin
codex plugin add voyage-fuel-cost@pdm-voyage-plugins
```

Restart Codex and start a new conversation after installation. To receive later updates:

```text
codex plugin marketplace upgrade jaydee021403-lab/voyage-fuel-cost-plugin
codex plugin update voyage-fuel-cost@pdm-voyage-plugins
```

## Test case

Provide the plugin with:

1. a PVP screenshot showing MAIN and ALT cost summaries;
2. matching AROS screenshots showing route rows and any red `DATE` holding rows or low-speed intervals;
3. the exact UTC holding interval(s) when the screenshot does not show the complete interval;
4. the latest exact-vessel RAS-411 workbook when speed-curve validation is required.

Ask:

```text
Calculate MAIN and every ALT fuel cost excluding all route-specific drifting/holding periods. Show the colored side-by-side comparison, signed difference versus MAIN, total ME + AUX consumption excluding holding, and a complete holding deduction reconciliation.
```

Verify that every holding interval is listed, that MAIN is unchanged when it has no holding, and that a route's deduction is not copied to another route. Negative ALT differences must be labeled as savings; positive differences must be labeled as more expensive.

