# Posit Conf Day 2 Notes

## It's Abstractions All the Way Down ... [KEY-1161]

[link]()

[slides](https://github.com/CerebralMastication/Presentations/tree/master/2023_posit-conf)

- leaky abstractions first mentioned in [this blogpost](https://www.joelonsoftware.com/2002/11/11/the-law-of-leaky-abstractions/) and [this wiki](https://en.wikipedia.org/wiki/Leaky_abstraction)
- a leaky abstraction is one where the underlying implementation details are exposed to the user
    - the user is forced to understand the underlying implementation details to use the abstraction
- there are also organizational abstractions 
- bounded rationality is a concept that humans have limited capacity to understand things and make decisions originally coined by Herbert Simon
    - tldr: "head trunk only hold so much junk"
- abstractions shouldnt be used for gatekeeping
    - they commonly are
- abstractions are a tool to help us understand the world
- choose between learning the new abstraction or partnering with an expert
- constrain complexit and seperate concerns
- org abstraction leakage
    - siloed organization due to overly rigid abstraction
    - communication is the source of and solution to all problems
- JD's 80-60-14 rule 
    - started as 80-20 rule
    - 80% normal business users: apps, dashboards, and basic excel
    - 16% super users: sql, custom dashboards, advanced excel
    - 4% guru users: APIs and code based tooling
    - the definition of done now includes these three groups
        - however work from the principle not the implementation
        - use communication to get at the principle or actual need (keep the end problem in mind)
- to debug an abstarction you have to see below it
    - So you need to make it permeable
- JD's assertions
    - "The single biggest business value derived from the data science movement in the last 13 years is making it legitimate to code outside of IT roles" 
    - "Abstractions will leak.  Therefore, abstractions must be permeable to allow debugging."
    - "No single abstraction is right for everyone."
- user personas are nice but it's best to pick up the phone and talk to actual person you're targeting
- data lake vs data warehouse

## Towards the Next Generation of Shiny UI [TALK-1124]

[link](https://events.conf.posit.co/widget/posit/positconf23/testsessioncatalog/session/1685040655912001Gc4I)

- Lots of great new updates to bslib package. See [changelog](https://rstudio.github.io/bslib/news/index.html) for latest.
    - Now a dependency of Shiny and R Markdown.
- Bslib provides a modern Bootstrap 5 foundation to apps and Rmd docs with modern UI components, layouts, and themes. 
- This includes many very useful components for dashboards including value boxes, expandible cards, tooltips, accordians to group controls, popovers, closed by default collapsible sidebars, nightmode toggle, and more.
- [Example bslib enhanced app](https://bit.ly/bslib-flights) or t[this link](https://bslib.shinyapps.io/flights/)
- Expect similar components in Shiny for Python in future
    
## ShinyUiEditor: From Alpha to Powerful Shiny App Development Tool [TALK-1126]

[link](https://events.conf.posit.co/widget/posit/positconf23/testsessioncatalog/session/1685040656357001GRTj)

- Out of alpha now - ready for use and feedback
- [Changelog](https://rstudio.github.io/shinyuieditor/news/index.html)
- Markdown editing 
- Icon selection support
- Tooltip support
- Python version coming out soon (very limited now)

## Github Copilot integration with RStudio, it's finally here! [TALK-1117]

[link](https://events.conf.posit.co/widget/posit/positconf23/testsessioncatalog/session/1685040654470001GrdI)

[slides](https://colorado.posit.co/rsc/rstudio-copilot/#/TitleSlide)

- RStudio now supports Github Copilot generated Ghost Text
- Available [in daily build](https://dailies.rstudio.com/) on Desktop IDE 
    -  Will be available in stable version and on Workbench soon by end of September
- Solutions to getting stuck
    - Simple, specific, and use comments (S^2C)
        - break down complex tasks
    - Prompt again in a different way
    - Add more top level or inline comments
    - Build off of your own momentum (write some of your own code)

## It's a Great Time to be an R Package Developer! [TALK-1132]

[link](https://events.conf.posit.co/widget/posit/positconf23/testsessioncatalog/session/1685040657595001G6xE)

- [R pkgs book 2nd edition](https://r-pkgs.org/) includes new services like GitHub Actions, new tools like pkgdown, and emerging shared practices, such as principles that are helpful when testing a package. See R packages book for more info and the talk for an entertaining talk from Hadley Wickham filling in, on the fly, for Jenny Bryan.

## Diversify Your Career with Shiny for Python [TALK-1138]

## Thanks, I Made It with Quartodoc [TALK-1139]

## Running R-Shiny without a Server [TALK-1151]

[link](https://events.conf.posit.co/widget/posit/positconf23/testsessioncatalog/session/1685040661802001GsYF)

[slides](https://github.com/jcheng5/posit-conf-2023-shinylive)

- cost = k * (comp complexity * number of users)
- before wasm, JS was the native language of browsers
- WASM is designed ofr compilers to emit
    - in contrast to JS which is designed for humans to write
- write c/c++, compile to WASM, then run in browser
- alot of challenges porting R to WASM
- Shinylive for R is now available [here](https://shinylive.io/r/examples/)
- convert, fiddle or control
    - convert local shiny app to static html/css/js/wasm
    - fiddle by writing and deploying shiny apps directly in your browser
    - include by using shinylive quarto extension which provide static shiny apps as quarto code chunks
- use cases
    - next presentation
    - interactive lecture notes
    - interactive blog posts
- limitations
    - slower starttime and larger download size
    - not all of cran is available
    - some functions just dont work
    - can't connect to databases
    - code/data is fully visible to users

## Magic with WebAssembly and webR [TALK-1152]

[link]() 

[slides](https://gws.quarto.pub/magic-with-wasm-and-webr/#/title-slide)

[more slides](https://gws.quarto.pub/introduction-to-webr-2023/#/title-slide)

- web assembly (wasm) is a portable binary format
- webr is a version of the r interpreter built for web assembly
    - allows for r code to be run directly in browser without a supporting R server
- use cases
    - educational material
    - interactive presentations
    - notebook and literate programming
    - portable R apps, reproducibility

## AI and Shiny for Python: Unlocking New Possibilities [TALK-1153]

[link](https://reg.conf.posit.co/flow/posit/positconf23/attendee-portal/page/sessioncatalog/session/1685040662322001GbSB)

- LLM is a result of a neural network which is a result of matrix math. They're statistical models that make predictions.
- Give it text and it predicts the next word
- Winston wrote the [chatstream package](https://github.com/wch/chatstream) 
- request in JSON
    - system role content and user role content
- LLMs are good to unstructures to structured data conversion
- We can use a human to validate the output
    - Can use computer to make data easier for human consumption
- augmenting LLM knowledge
    - Can give shiny for python or other package documention to LLMs
    - can break up a document into text pieces and store them in a vector database
        - when human asks question about doc then computer can use vector DB to extract possibly relevant pieces of text
        - LLM ingests that subset of text to get something useful
        - need alot of tokens (16K or more)
- solution: posit document query
