# Reframe Speed Experiment

## The problem

When demoing Reframe in the Photos app to customers, I've noticed it takes about 24 seconds to finish. Customers often ask questions like, "Is it going to take this long for me too? Why is it taking this long?"

## Hypothesis

Because of the long wait, users lose patience and cancel before Reframe finishes. Over time, they may also come to see it as a flawed feature and stop using it.

## Background research

A classic usability guideline holds that 10 seconds is about the limit for keeping a user's attention focused on a task (Nielsen, 1993). A 2020 experiment on mobile apps found that user experience drops below average once response times pass about 5.5 seconds, and that users tolerate waits longer than they are satisfied with them (Yu et al., 2020). An earlier Google study found that 53% of mobile website visitors leave if a page takes longer than three seconds to load (Marketing Dive, 2016).

That research covers web pages and routine app tasks rather than AI editing tools, where users may expect to wait longer. Still, I'd expect similar impatience here: users are used to features on their phone responding quickly, so a 24-second wait may stand out. My experiment tests whether that holds for an AI editing feature.

## The experiment

- **Control group:** the current Reframe (about 24 seconds).
- **Treatment group:** the improved Reframe targets about 8 seconds, down from the current 24, which is about 67% faster. I chose 8 because it's under the 10-second attention limit (Nielsen, 1993) and in line with similar tools on competing phones.
- **Random assignment:** users are randomly assigned to a group. This shows that if there is a change in behavior, it's due to the feature itself, not to users who were eager to opt in or to be part of an experiment.

## How I'll measure it

- **Primary metric:** Of users who start a Reframe, the percentage who cancel after waiting at least 5.5 seconds (yes/no, per Reframe).
- **Why this metric:** It measures the moment a user loses patience with the wait, which is exactly what the faster version changes. Users who cancel for other reasons, like being busy, are spread evenly across both groups by random assignment, so they don't affect the comparison. I set the threshold at 5.5 seconds, the point where a 2020 study found mobile app experience drops below average (Yu et al., 2020). This metric was refined with feedback from my mentor, a software engineer.
- **Secondary metrics:**
  - **Secondary 1:** Did the user use Reframe again, on any photo? (yes/no), within 7 days. Because users tolerate waits longer than they are satisfied with them, this catches people who waited but were still unhappy and quietly stopped using it.
  - **Secondary 2:** Did the user retry Reframe on the same photo after canceling? (yes/no), within 24 hours.
  - **Secondary 3:** Did the user use Reframe again, on any photo? (yes/no), within 30 days.
- **Guardrail:** Undo rate after a Reframe must not increase in the treatment group compared to control.

## Why simulated data

Real usage data for features like Reframe isn't public. Companies measure it internally, but it's probably not a number any company wants floating around. So I built a simulator that creates users and builds in an effect of a known size. Because I know the true effect, I can check whether my analysis actually finds it. If it does, I can trust the method; if it doesn't, I know there's a mistake to fix. It also lets me test at large scale, like a million users.

## Status

- [x] Experiment design: feature, metrics, guardrail (this README)
- [X] Users randomly assigned to control or treatment
- [X] Each user gets a Reframe time and outcomes (canceled, repeat use)
- [X] Treatment gets a built-in effect of known size
- [ ] Loop vs. NumPy speed comparison at 1 million users
- [ ] First comparison between groups

## What's next

**By our next meeting (October 15):**

- Each simulated user gets a Reframe time, a yes/no outcome for canceling after 5.5 seconds, and a yes/no outcome for repeat use within 7 days.
- The treatment group gets the built-in effect: faster times (about 8 seconds instead of 24), fewer cancels, and a higher chance of repeat use.
- The simulation runs at 1 million users, with a speed comparison between a plain Python loop and NumPy.
- A first look at the results: cancel rate and repeat-use rate in each group, and whether the mean or median better describes Reframe times.

**After that:** As I learn SQL joins and grouping, I'll load the data into a database and calculate each group's rates. Then, with Practical Statistics Chapter 3, I'll test whether the difference between groups is real or just noise.


## References

Marketing Dive. (2016, September 12). *Google: 53% of mobile users abandon sites that take over 3 seconds to load.* https://www.marketingdive.com/news/google-53-of-mobile-users-abandon-sites-that-take-over-3-seconds-to-load/426070/

Nielsen, J. (1993, January 1). *Response times: The 3 important limits.* Nielsen Norman Group. https://www.nngroup.com/articles/response-times-3-important-limits/

Yu, M., Zhou, R., Cai, Z., Tan, C. W., & Wang, H. (2020). Unravelling the relationship between response time and user experience in mobile applications. *Internet Research.* https://research-api.cbs.dk/ws/portalfiles/portal/66651668/chee_wee_tan_et_al_unravelling_the_relationship_between_response_time_and_user_experience_in_mobile_applications_acceptedversion.pdf
