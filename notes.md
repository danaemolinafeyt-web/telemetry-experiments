## Oct 8, 2026: Build 1

**Done:** README (deliverable 1), simulator v2 in plain Python (deliverable 2).

**Built-in effect (my assumption):**
- Control (24 s wait): 40% cancel. Below Google's 53% web-page
  abandonment, because in-store demos showed customers are loyal and
  patient: they waited, but asked "why is it taking this long?"
- Treatment (8 s wait): 5% cancel. Only 2.5 s past the 5.5 s threshold,
  so most cancels would be for unrelated reasons.

**Result:** at 1,000 users, cancel rates came out near 40% and 5%. At
20 users they were way off (17% and 0%). Small samples are noisy.

**Idea for later:** Reframe times should vary per user and device, not be
fixed. And the longer someone waits, the more likely they cancel.