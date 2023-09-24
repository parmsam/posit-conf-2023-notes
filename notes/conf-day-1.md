# Posit Conf Day 1 Notes

## From Data Confusion to Data Intelligence [KEY-1060]

- getting data science started in large and small orgs can be hard
- data science needs
    - analysis ready data
    - cross team support
    - space for uncertainty
- data science cycle
    - scan for opportunity
    - show don't tell
    - take the data and run
    - nail the landing
    - up the ante
- tips
    - maximize speed and autonomy
    - build foundation wherever possible along the way
- data science starts with data access
    - requires teams to set expectations
    - lots of coordination with IT
- knowledge architecture framework
- need an advocate to keep the sustainable pipeline going
    - management changes over time
    - need to be retold the story
- research the new technologies that are coming out
    - useful when leadership asks what's next

## A hackers guide to open source LLMs [KEY-1107]

- [nat.dev](https://github.com/nat/openplayground)
    - tokens are whole words or portions of words
- [ULMFiT 3-step approach](https://arxiv.org/abs/1801.06146)
    - 3 steps: LM pre-training, LM fine-tuning, classifier fine-tuning
    - Trained on Wikipedia
    - Model would have to guess what the next word is
        - rewarded if it correctly guesses the next word
    - in order to do this well, it needs to know alot about the world
    - meaning it has to be trained on alot of data to have the right capabilities
    - this is a form of compression
- instruction tuning
    - use datasets like OpenOrca
- in order to be really good at language modeling, you need to be really good at using languages models
    - use the best one which is currently GPT-4
- GPT 3/4 are not trained to give correct answers. 
- They were trained to predict next words first. Use custom instrucitons in ChatGPT to prepend text to the prompt.
- [GPT can't reason](https://arxiv.org/abs/2308.03762) good first place to start
- Functions in OpenAPI api tells them about functions you have (actually the JSON schema). The key is the docstring to programming this way. It is key to describig what the function does. The jsonschema object is the completion object.
- [GPTQ](https://arxiv.org/abs/2210.17323) on [HuggingFace(https://huggingface.co/models?search=gptq)
- Ton of these models are based on [Llama2](https://ai.meta.com/llama/)
- [h2oGPT](https://github.com/h2oai/h2ogpt)
- Concepts
    - Custom instructions in ChatGPT
    - ULMFIT (Universal Language Model Fine-tuning)
    - GPT 3/4
    - RLHF (Reinforcement Learning with Human Feedback)
    - Advanced Data Analysis in ChatGPT
    - Multi-stage conversations in ChatGPT
    - Function calling via OpenAI API
    - GPTQ
    - Instruction tuned model 
        - Prompt formats
    - Retrieval augmented generation

## {slushy}: A Bridge to the Future [TALK-1078]

[talk](https://events.conf.posit.co/widget/posit/positconf23/testsessioncatalog/session/1685040646577001G02e)

[package website](https://gsk-biostatistics.github.io/slushy/)

- the slushy R package developed on top of renv for users to quickly mimic a controlled environment
- slushy = renv + posit package manager for GSK
- penguin huddle analogy for users to feel confident about the environment in which they are coding
     - enables community to work off a common source of truth
- `config.yml` file allows community to be fixed on the 'agreed upon' set of packages
    - happens at an org or dept level
- slushy introduces a vetting step that kicks off a huddle
- posit package manager enabled CRAN snapshots
    - GSK hooks into those snapshots for slushy
    - appears that config yaml file has parameter for the snapshot date
    - communication happens around this snapshot date
- slushy's features
    - `slushy_init()` as replacement for `renv::init()` (built on top of that function)
        - developer have access to the packages from that snapshot date
        - this prevents unintended deviations
    - a team can change the agreed upon set of packages via `slushy_add()` which adds it to the renv lockfile and slushy config yaml
    - also enables time traveling via `slushy_update()` where users can pass a snapshot date which similar updates both
    - `slushy_update_preview()` gives users a peak ahead of what packages will change by changing the snapshot date
- in practice at gsk
    - one or two individual initialize or maintain the environment
    - rest of team just uses it
- the settings are put in the `config.yml` which is where the org or team can put the standard settings
    - includes info like rspm_url, snapshot date, packages
- takeaways
    - enables a way to coordinate renv and rspm use for teams who might need to be mobile
    - slushy enables a bridge to the future for teams
    - useful wrapper for orgs, depts and teams
- follow up
    - added [this issue](https://github.com/GSK-Biostatistics/slushy/issues/5) to consider grabbing default slushy_config.yml from global options #5 via `get_config()`

## Package Management for Data Scientists [TALK-1081]

- conflicting packages example
    - package a and b are needed
    - package a requires rcpp 1.0.6
    - package b requires rcpp 1.0.7
- solutions from stackoverflow included
    - `renv::install()`
    - something else
    - upgrade to r 4.0.2
- prevention solutions
    - use tools to create reproducible environments
    - use snapshots for package installs
        - miniCran, bandersnatch for python, posit package manager
- use of snapshot date benefits
    - pacakges at that date are more likely to be compatible with each other
    - safe guard in case package gets deleted which sometimes happens on package repositories
- follow up reading
    - [Challenges in Package Management blog post](https://posit.co/blog/challenges-in-package-management/)
    - every time you create a new R or Python script also create a lockfile or requirements.txt
    - consider tools like docker to handle environments
    - if you're a package author, define versions and system dependencies for others

## dbtplyr: Bringing Column-Name Contracts from R to dbt [TALK-1098]

## Getting the Most Out of Git [TALK-1091]

- talk is a follow up to Jenny Bryan's [Happy Git with R](https://happygitwithr.com/)
- git workflow
    - main branch
    - hotfix branch
    - release branch
    - dev branch
    - feature branch
    - feature 2 branch
- it can get chaotic quickly
- keep it simple (use the github workflow)
    - main branch
    - feature branch 
- recommendations 
    - main branch should be protected
    - use basic continuous integration
        - confirm that the apps runs, package builds, or quarto doc compiles
    - [codeowners file](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners)
        - offers a programmatic way to pull out ownership info within an org for a github org
    - scheduled CI
    - continuous development
        - for apps for example
    - pedantic ci
        - is news file properly formatted
        - is description tidy
        - are filenames lowercase
        - commit message style
- takeaways 
    - another thing you can do is create templates for alot of this CI stuff that you can use for projects later

## Documenting Things: Openly for Future Us [TALK-1092]

[slides](https://openscapes.github.io/documenting-things/#/title-slide)

- things is all of the things
    - code and analyses
    - teaching resources
    - onboarding and community
    - fieldwork and lab protocols
    - events
- the mindset is that you are doing this for yourself, teams, and communities in the next hours, week or decades
    - this is both intentional and inclusive so that others can benefit
- however, it doesn't have to be painful
- solutions
    - have a place
        - develop a habit of writing in that place
    - write in a modular way
        - write in small bits in a way that can be networked
        - this allows you to follow a DRY principle
    - have an audience in mind
        - can make it engaging
    - write in an inclusive tone
        - avoid words that trivialize things that might be complex for some people
        - meet folks where they are
    - narrate code in small chunks 
        - write them into documentation
        - important for teaching
        - quarto's code annotation feature can help with this  
    - share early
        - useful to iterate and recieve feedback
    - design for readaiblity and accessibility
        - use section headers
            - can use an anchored url to get to the section
        - use text formatting
        - use alt text

## Siuba and duckdb: Analyzing Everything Everywhere All at Once [TALK-1101]
