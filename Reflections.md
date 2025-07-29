🧠 Project Reflection
This reflection outlines the challenges, choices, and learning from my solo mini-project. It is intended to document my critical thinking and guide improvements in future work.

🎯 Project Aim
The project aimed to explore how different contextual and socioemotional factors relate to student performance outcomes using a subset of PISA data. The analysis focused on identifying potential predictors but also served as a learning opportunity in working with real-world data and basic modeling techniques.

✅ What Was Included
The dataset I worked with contained a reasonably wide range of contextual and attitudinal features, such as:

Socioeconomic status & home environment:
SES, has_computer, has_books, num_sib, family_stat, food_sec, life_sat

School experience and support:
teacher_help, qual_math_instruct, teacher_equality, safe_student, safe_class, schl_belong

Social experience and wellbeing:
make_friends, feel_included, no_mock

Learning effort & attitudes:
math_hwork, life_sat

Geography:
region_england, region_scotland, region_wales, region_n_ireland

Despite this range, there were important limitations and missed opportunities.

🧱 Feature Engineering: A Missed Opportunity
Feature engineering in this project was very basic:

No composite variables were created, although many features could have been grouped (e.g., socioemotional wellbeing, safety, or academic support).

No interaction terms were included, despite likely synergistic effects (e.g., how teacher_help and SES together influence outcomes).

No nonlinear transformations were explored — all variables were treated as linear inputs.

If I had more time or experience, I would have:

Created index scores for emotional safety, school support, and peer relations.

Explored clustering or dimensionality reduction (e.g., PCA) for feature grouping.

Applied nonlinear models (e.g., random forests, XGBoost) with tuning and cross-validation.

🔍 What Was Missing
While many useful variables were present, I now recognize several important gaps:

No baseline academic performance, which would be key for understanding growth or change.

No detailed school-level data (e.g., school size, resources, teacher experience).

Limited demographic granularity beyond gender and region.

These omissions limited both predictive power and the ability to explain why outcomes varied.

🧠 Analytical Framing: Predictive or Explanatory?
This was a helpful learning moment: I didn’t fully define whether my goal was to predict student outcomes or explain them. These require different modeling approaches:

Predictive models focus on accuracy and generalization.

Explanatory models focus on interpretability and causal structure.

In future projects, I would clarify this upfront and align my modeling choices accordingly.

🌍 What I’d Do Differently
If I were to redo this project, I would:

Pull in richer data from the full PISA dataset, especially country-level data and baseline academic indicators.

Include composite indicators and test interactions between variables.

Explore nonlinear and ensemble models, as well as feature selection techniques.

Consider running separate contextual analyses by country, especially given regional education differences across the UK.

Clearly define whether the goal is explanation or prediction — and choose methods to suit that goal.

💬 Final Thoughts
This project was a valuable learning experience. While the final model had clear limitations, I developed a deeper understanding of:

What makes a good feature set

The importance of analytical framing

The need for clarity, consistency, and thoughtful modeling

It also highlighted the value of combining data science techniques with critical reflection, especially in education contexts.

