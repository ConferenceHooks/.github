# ConferenceHooks #

This is a webservice for conferences to rung webhooks to automate the workflow of event organisers.  
At present we are targeting Pretalx and Prereg/Pretix to automate schedule building and speaker registration.  
For now this is still __work in progress__, there are several parts that are working and available, other require still some more work.

## DevOpsDays ##

- Schedule page creation
- Speaker page creation
- Automated schedule release creation [WIP]
- Speaker registration [WIP]

### Manual creation ###

As mentioned this is still _work in progress_, therefor the automated hook to have pretalx create a speaker page or schedule page on release isn't available now.  
Currently you need to use `curl` or any other such tool to generate this.
Here are the two current working endpoints :

1. Speaker page

```
curl -iv \
	-X POST \
	-H 'Accept: application/json"' \
	-d '{
		"year": "<dod year here>",
		"city": "<dod city here>",
	"api_url": "https://<pretalx url>/api/events/<pretalx eventcode>/submissions/",
	"api_token": "<pretalx api token>",
	"github_user": "<github username or conferencehooks>",
	"github_token": "<github token>"
	}' \
https://conferencehooks.vantosh.com/devopsdays/speakers/website
```
As you can see, you need to add your DevOpsDays City, Year, Pretalx URL, Pretalx EventCode, Pretalx API Token. GitHub User or use this repo, GitHub Token.
Once launched it can take up to 10 minutes to create the actual PR against the DevOpsDays upstream repository.


2. Schedule page

```
curl -i \
	-X POST \
	-H 'Accept: application/json"' \
	-d '{
		"year": "<dod year here>",
		"city": "<dod city here>",
		"api_url": "https://<pretalx url>/api/events/<pretalx eventcode>/talks/",
		"api_token": "<pretalx api token>",
		"github_user": "<github username or conferencehooks>",
		"github_token": "<github token>"
	}' \
https://conferencehooks.vantosh.com/devopsdays/schedule/website
```

As you can see, you need to add your DevOpsDays City, Year, Pretalx URL, Pretalx EventCode, Pretalx API Token. GitHub User or use this repo, GitHub Token.
Once launched it can take up to 15 minutes to create the actual PR against the DevOpsDays upstream repository.


## CfgMgmtCamp ##

- Speaker registration [WIP]

