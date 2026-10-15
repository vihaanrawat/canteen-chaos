# Debug Log

This log documents the bugs I investigated, their root causes, the fixes I implemented, and the tests I performed to verify them.



### CC-02 — "Dish names and prices are nearly invisible in dark mode"

**Reproduced:** Switched to dark mode and observed that dish names and prices were difficult to read because their text color did not adapt to the active theme.

**Cause:** The `.dish-body` element used a hardcoded color (`#2b2118`), which remained dark in dark mode and reduced text visibility.

**Fix:** Replaced the hardcoded color with `color: var(--ink);`, using the existing theme-aware CSS variable so the text color adapts to light and dark modes.

**Checked:** Verified that dish names and prices became readable after the change. Tested both themes and initial page load.

**Time:** About 15 minutes, including debugging and testing.



### CC-01 — "Search suggestions appear behind other content"

**Reproduced:** Typed `pa` into the search bar and observed that the "Pav Bhaji" suggestion was hidden behind the category tabs, while another suggestion was partially covered.

**Cause:** The `.search-wrap` element had `position: relative` and `z-index: 1`, creating a stacking context. Although the suggestions had a higher `z-index`, they were constrained by their parent's stacking context. The category tabs had `z-index: 40`, allowing them to appear above the search wrapper.

**Fix:** Removed `z-index: 1` from `.search-wrap` while keeping `position: relative` for dropdown positioning. This removes the stacking context created by that `z-index` declaration and allows the suggestions to participate in the surrounding stacking order.

**Checked:** Verified that the search suggestions appear above the category tabs and that clicking "Pav Bhaji" opens its dish details.

**Time:** About 20 minutes, including investigation, fixing, and testing.


