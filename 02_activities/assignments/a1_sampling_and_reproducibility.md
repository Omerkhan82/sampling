# ASSIGNMENT: Sampling and Reproducibility in Python

Read the blog post [Contact tracing can give a biased sample of COVID-19 cases](https://andrewwhitby.com/2020/11/24/contact-tracing-biased/) by Andrew Whitby to understand the context and motivation behind the simulation model we will be examining.

Examine the code in `whitby_covid_tracing.py`. Identify all stages at which sampling is occurring in the model. Describe in words the sampling procedure, referencing the functions used, sample size, sampling frame, any underlying distributions involved, and how these relate to the procedure outlined in the blog post.

Run the Python script file called whitby_covid_tracing.py as is and compare the results to the graphs in the original blog post. Does this code appear to reproduce the graphs from the original blog post?

Modify the number of repetitions in the simulation to 100 (from the original 1000). Run the script multiple times and observe the outputted graphs. Comment on the reproducibility of the results.

Alter the code so that it is reproducible. Describe the changes you made to the code and how they affected the reproducibility of the script file. The output does not need to match Whitby’s original blogpost/graphs, it just needs to produce the same output when run multiple times

# Author: Omer Khan

```
Please write your explanation here...

Understanding the Simulation and Sampling Process

This simulation models how infections spread and are traced among individuals attending two types of events: weddings and brunches. It follows a multi-stage sampling approach to assign infections, trace primary contacts, and implement secondary tracing.

1. Infection Assignment (Random Sampling Without Replacement)
The population consists of 1000 individuals, with 200 attending weddings and 800 attending brunches.

10% of the population (100 individuals) is randomly infected.
Every individual has an equal chance of being infected, but once selected, they cannot be chosen again.
This step represents the initial spread of infection in a randomized way.
2. Primary Contact Tracing (Probability-Based Selection)
Once infections are assigned, the tracing process begins:

Each infected person has a 20% chance of being successfully traced.
This probability-based selection mirrors real-world contact tracing efforts, where only some infected individuals are identified.
The outcome of this stage varies due to randomness, meaning different runs of the simulation may produce slightly different results.
3. Secondary Contact Tracing (Rule-Based Selection)
Secondary contact tracing follows a deterministic approach rather than random selection:

The number of traced infections is counted per event type (wedding/brunch).
If at least two infections were traced in a specific event, all infected individuals at that event are automatically traced.
This step introduces bias, as it disproportionately increases the number of infections traced to weddings, making them appear more infectious than they actually are.
Comparing with the Blog’s Approach

The methodology in the blog and this simulation are almost identical, except for the number of iterations.
The blog runs 50,000 iterations, producing a smoother and more precise distribution, while this simulation runs 1000 iterations.
Despite this difference, both methods highlight the same bias in tracing results.
Effect of Reducing Runs from 1000 to 100

Running the simulation only 100 times increases variability in results.
Fewer runs mean each trial has more influence on the overall distribution, making patterns less stable and noisier.
A higher number of iterations produces more reliable and consistent results.
The Role of Random Seed in Reproducibility

Without a fixed random seed, results will vary each time the code runs, as different random numbers are generated.
Setting a random seed ensures consistency, making it possible to reproduce the same results across multiple runs.
This is particularly useful for debugging and comparing outcomes.
Key Takeaways

Multi-Stage Sampling: The simulation involves random infection assignment, probability-based primary tracing, and rule-based secondary tracing.
Tracing Bias: Secondary contact tracing overestimates infections from weddings, creating a misleading impression.
Effect of Iterations: More iterations produce a smoother and more accurate representation of trends.
Reproducibility: A fixed random seed ensures consistent results across different runs.


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
