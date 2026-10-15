# Debug Log

This log documents the bugs I investigated, their root causes, the fixes I implemented, and the tests I performed to verify them.

### CC-02 — "Dish names and prices are nearly invisible in dark mode"

**Reproduced:** Switched to dark mode and observed that dish names and prices were difficult to read because their text color did not adapt to the active theme.

**Cause:** The `.dish-body` element used a hardcoded color (`#2b2118`), which remained dark in dark mode and reduced text visibility.

**Fix:** Replaced the hardcoded color with `color: var(--ink);`, using the existing theme-aware CSS variable so the text color adapts to light and dark modes.

**Checked:** Verified that dish names and prices became readable after the change. Tested both themes and initial page load.

**Time:** About 15 minutes, including debugging and testing.
