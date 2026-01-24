# umd-ta

## How to Use This Repository

1. **Browse existing discussions** before posting - your question might already be answered!
2. **Use GitHub Discussions** (not Issues) for questions
3. **Select the appropriate category** when posting
4. **Include your code/materials** - link to your GitHub repo or attach relevant files
5. **Be specific** - include error messages, what you've tried, and expected vs actual behavior

## Sharing Your Work

When asking for help, please:
- Create a **public GitHub repository** for your experiment code
- Link to the specific file or line where the problem occurs
- Include relevant data files (anonymized!) or notes
- Example: "Here's my analysis script: https://github.com/yourname/exp1-stroop/blob/main/analysis.R"

## Getting Started with Git/GitHub

New to Git? Check out:
- [GitHub's Hello World Guide](https://guides.github.com/activities/hello-world/) (You probably only need Step1)
- [Git Basics Tutorial](https://git-scm.com/video/what-is-git)

---

# Example Questions

Below are examples of well-formatted questions for each category. Good questions include:
- Clear description of the problem
- Links to your code repository
- What you've tried
- Expected vs actual behavior
- Relevant code/output


If you do not care about water consumption, you can paste the relevant example below into ChatGPT, give details about your specific problem, and tell it to create a question for you. It will ask you clarifying questions to get all the details needed.

---

## PCIbex Questions

**Title: "Randomization not working across trials"**

I'm trying to randomize the order of stimuli in my Stroop task, but the same 
order appears every time I run the experiment. 

**My repo:** https://github.com/student123/stroop-experiment  
**Problem file:** https://github.com/student123/stroop-experiment/blob/main/experiment.js

Here's the relevant code:

```javascript
newTrial("stroop",
    newText("word", row.word).print(),
    newKey("response").wait()
)
```

I've tried using newTrial() with .shuffle() but it still presents in the 
same order. Has anyone encountered this? Am I missing something in the 
sequence setup?

**My notes on what I've tried:** https://github.com/student123/stroop-experiment/blob/main/debugging-notes.txt

Expected: Random order each run
Actual: Same order (red, blue, green, yellow...)

---

## Prolific Related

**Title: "How do I counterbalance 4 lists/conditions in Prolific?"**

I have an experiment with 4 between-subjects conditions (4 different stimulus lists). 
I need 20 participants per condition (80 total participants).

**My repo:** https://github.com/jdoe89/lexical-decision-study  
**Experiment design notes:** https://github.com/jdoe89/lexical-decision-study/blob/main/counterbalancing-plan.txt

How do I ensure equal numbers of participants get assigned to each list in Prolific?

Options I'm considering:
1. Use Prolific's "Taskflow" feature to split participants into 4 groups?
2. Create 4 separate studies on Prolific (one per condition)?
3. Let PCIbex randomize participants and just collect extra data?
4. Use Prolific's custom screener somehow?

Questions:
- Does Taskflow guarantee equal distribution across conditions?
- If I create separate studies, can I prevent the same person from doing multiple?
- What's the standard way to handle this for between-subjects designs?

---

## Python Coding

**Title: "pandas KeyError when merging dataframes"**

I'm trying to merge my experimental data with participant demographics:

**My repo:** https://github.com/labstudent/exp2-analysis  
**Analysis script:** https://github.com/labstudent/exp2-analysis/blob/main/merge_data.py (lines 45-47)  
**Data files:** https://github.com/labstudent/exp2-analysis/tree/main/data

```python
df_merged = pd.merge(exp_data, demographics, on='participant_id')
KeyError: 'participant_id'
```

I've checked both dataframes with .columns and the column exists. 
Could this be a whitespace issue? How do I debug this?

**Screenshot of error:** https://github.com/labstudent/exp2-analysis/blob/main/error-screenshot.png

---

## R Coding/Modeling

**Title: "How do I calculate marginal means and compare conditions in brms?"**

I ran a Bayesian model on my semantic priming experiment with two factors:

**My repo:** https://github.com/cogstudent/semantic-priming  
**Analysis script:** https://github.com/cogstudent/semantic-priming/blob/main/analysis.R  
**Model output:** https://github.com/cogstudent/semantic-priming/blob/main/model-summary.txt  
**Notes on what I need:** https://github.com/cogstudent/semantic-priming/blob/main/analysis-todo.txt

```r
model <- brm(RT ~ prime_type * target_type + (1 + prime_type|participant) + (1|item), 
             data = df, 
             family = lognormal(),
             prior = c(prior(normal(6, 1), class = Intercept),
                      prior(normal(0, 0.5), class = b)))

summary(model):
Population-Level Effects: 
                              Estimate Est.Error l-95% CI u-95% CI Rhat
Intercept                         6.18      0.05     6.09     6.28 1.00
prime_typeUnrelated               0.15      0.03     0.09     0.21 1.00
target_typeNonword                0.22      0.03     0.16     0.28 1.00
prime_typeUnrelated:target_typeNonword  -0.08  0.04  -0.16    0.01 1.00
```

Questions:
1. How do I get marginal means for each condition (Related-Word, Related-Nonword, 
   Unrelated-Word, Unrelated-Nonword)? Should I use emmeans or marginal_effects?
2. I want to compare: "Related-Word vs Unrelated-Word" and "Related-Nonword vs 
   Unrelated-Nonword" - how do I extract these contrasts?
3. Since I used lognormal(), do I need to exponentiate the estimates to get 
   actual RT differences in milliseconds?
4. How do I report the interaction? Is the negative estimate for the interaction 
   meaningful given the CI crosses zero?

---

## SONA Related

**Title: "How many timeslots should I create?"**

Running my first study - need 60 participants for a 30-minute study. 

**Study details:** https://github.com/newresearcher/sona-study-setup/blob/main/study-plan.md

Should I:
- Create 60 individual timeslots?
- Batch them (e.g., 10 slots with 6 spaces each)?
- Overbook slightly in case of no-shows?

What do you typically do?

---

## Stats Related

**Title: "How should I code children's age in my developmental study?"**

I collected data from kids aged 36-72 months. For my analysis predicting 
vocabulary scores, I'm not sure how to include age in the model:

**My repo:** https://github.com/devpsych/vocab-study  
**Current analysis:** https://github.com/devpsych/vocab-study/blob/main/analysis.R  
**Data structure:** https://github.com/devpsych/vocab-study/blob/main/data-overview.txt  
**Questions notes:** https://github.com/devpsych/vocab-study/blob/main/coding-questions.txt

Option 1: Age in months (36, 37, 38, ..., 72)
Option 2: Age in years (3.0, 3.08, 3.17, ..., 6.0)  
Option 3: Log(months)
Option 4: Log(years)
Option 5: Mean-centered months (months - 54) 

Concerns:
- If I use raw months, will the intercept be weird (age = 0)?
- Should I log-transform because development isn't linear?
- Does centering make interpretation easier?

What's standard practice in developmental psychology? I want to interpret 
"for each month/year older, vocabulary score increases by X"
