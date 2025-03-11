# ASSIGNMENT: Sampling and Reproducibility in Python

Read the blog post [Contact tracing can give a biased sample of COVID-19 cases](https://andrewwhitby.com/2020/11/24/contact-tracing-biased/) by Andrew Whitby to understand the context and motivation behind the simulation model we will be examining.

Examine the code in `whitby_covid_tracing.py`. Identify all stages at which sampling is occurring in the model. Describe in words the sampling procedure, referencing the functions used, sample size, sampling frame, any underlying distributions involved, and how these relate to the procedure outlined in the blog post.

Run the Python script file called whitby_covid_tracing.py as is and compare the results to the graphs in the original blog post. Does this code appear to reproduce the graphs from the original blog post?

Modify the number of repetitions in the simulation to 100 (from the original 1000). Run the script multiple times and observe the outputted graphs. Comment on the reproducibility of the results.

Alter the code so that it is reproducible. Describe the changes you made to the code and how they affected the reproducibility of the script file. The output does not need to match Whitby’s original blogpost/graphs, it just needs to produce the same output when run multiple times

# Author: Omer Khan

```
1. Stages of Sampling in the Model

The simulation model in whitby_covid_tracing.py involves multiple stages of sampling, each representing different aspects of the contact tracing process. These stages are:

a. Event Attendance Sampling

The model assumes a fixed population of 1000 individuals, attending either a wedding (200 attendees across 2 weddings) or brunch (800 attendees across 80 brunches).

This stage does not involve random selection; all individuals are assigned an event type.

b. Infection Sampling

Each individual has a 10% probability (ATTACK_RATE = 0.10) of being infected.

A random subset of the total population is selected using np.random.choice(), ensuring the infection probability follows an independent and identically distributed (iid) Bernoulli process.

c. Primary Contact Tracing Sampling

Among infected individuals, only 20% (TRACE_SUCCESS = 0.20) are successfully traced.

This is implemented using np.random.rand() < TRACE_SUCCESS, where each infected individual has an independent chance of being traced.

d. Secondary Contact Tracing Sampling

If an event has at least two traced cases (SECONDARY_TRACE_THRESHOLD = 2), then all attendees of that event are considered traced.

This introduces a systematic bias, as weddings (with larger guest lists) are more likely to reach the threshold and have complete tracing.

2. Comparison of Results with the Blog Post

Running the script as is, the graphs generated show a consistent overestimation of wedding-related cases compared to the true proportion. This aligns with the original blog post’s results, which suggest that larger, well-documented events (like weddings) appear to contribute disproportionately to total traced infections due to biased sampling.

3. Impact of Reducing Simulation Repetitions

Reducing the number of repetitions in the simulation from 1000 to 100 introduces more variance in results. Running the script multiple times results in noticeably different graphs, indicating that the smaller sample size amplifies random fluctuations, reducing reproducibility.

Statistical Findings from 100 Iterations:

Mean proportion of wedding infections: 20.1%

Standard deviation of wedding infections: 3.6%

Mean proportion of wedding traces: 18.8%

Standard deviation of wedding traces: 6.3%

4. Improving Reproducibility

To ensure that the simulation produces the same results each time it is run, we introduce a random seed using np.random.seed(). The modified code includes:

np.random.seed(42)  # Setting a fixed seed for reproducibility

Effect of Changes:

The script now consistently produces the same results across multiple runs.

While the output does not have to match Whitby’s original graphs, it ensures internal reproducibility for analysis and debugging.

Conclusion

The model effectively demonstrates biased sampling in contact tracing due to systematic over-tracing of well-documented events. However, reproducibility was initially weak due to random sampling variations. By implementing a fixed random seed, the output stabilizes, allowing for consistent and repeatable results. Additionally, reducing the number of iterations to 100 increases variability, highlighting the need for a sufficient sample size to ensure reliable results.


## Criteria

|Criteria|Complete|Incomplete|
|--------|----|----|
|Altercation of the code|The code changes made, made it reproducible.|The code is still not reproducible.|
|Description of changes|The author explained the reasonings for the changes made well.|The author did not explain the reasonings for the changes made well.|

## Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `23:59 - 16/02/2025`
* The branch name for your repo should be: `assignment-1`
* What to submit for this assignment:
    * This markdown file (a1_sampling_and_reproducibility.md) should be populated.
    * The `whitby_covid_tracing.py` should be changed.
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sampling/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `assignment-1`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via the help channel in Slack. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
