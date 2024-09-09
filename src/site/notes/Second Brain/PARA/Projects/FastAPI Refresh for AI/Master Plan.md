---
{"dg-publish":true,"dg-path":"Projects/FastAPI Refresh for AI/Master Plan.md","permalink":"/projects/fast-api-refresh-for-ai/master-plan/","noteIcon":"","updated":"2024-09-04T21:20:54.432-07:00"}
---


- ! Create a new streamlit project for youtube to mp3 web client
## Youtube to AI Summary
---

>[!calendar] Status - 09-04-2024
>1. Create POC with StreamLit and backend with FastAPI.
>2. send to Nate and post on discord servers for feedback 
>3. if valid idea
	>1. Create React + Tailwind frontend for better aesthetics

### Ideas
- review and look at old fastAPI project
	- understand how it works again
	- integrate with pytest
	- deploy it as an API on that one API website where you make money after X many requests.


- @ Once I am finished with the basic development version of the obsidian plugin, and the website:  *add the ability to scrap the youtube comments for insights too.*
    - maybe filter importance by the number of likes of reply's to the comment.

- @ as well as scrape the description of the youtube video for links/resources that can be added to the summary.

- ! also re-work the youtube to AI summary script to have a "--detailed" flag
that allows for an in-depth breakdown of the transcript.

eventually just build like a gradio project to share on hugging face, that is youtube client where you can type a topic or an idea 


>[!attention] Feasible idea (matched with stuff from above) => "YouTube Search Summary"
> 1. searches for the idea
> 2. grabs top 5 videos
> 3. makes and compares the youtube summaries
> 4. use ML or DL to judge how good the summary is
> 5. returns a write-up about the search query and gives recommendations for the best videos to watch for the most context.


>[!sparkles]- Breakdown
> Update and get the fastapi project running again on Ubuntu
>
 postman
 Docker
 PostgreSQL
 Alembic
 Pydantic
 Etc
>
>Breakdown the just code in obsidian so the concepts stick and can be referenced, 
>
>~~Finish the tutorial and add unit testing and stuff with pytest or unit test~~ 
	>instead of restarting the tutorial or continuing, because it is outdated. **follow along with the fastapi documentation and try to reimplement all the features this project has**
>

### Use videos as a guide but use documentation first
---
[[Second Brain/PARA/Projects/FastAPI Refresh for AI/Youtube Resources\|Youtube Resources]]
[FastAPI Documentation](https://fastapi.tiangolo.com/tutorial/)

## Done
---
 
- [x] ! make a new git branch of the project, that I can do my re-implementation so I don't lose my progress
- [x] Create a new branch of the git repo once it’s updated and understood for YouTube summary custom gpt API
	- branch name is: *update-project*
