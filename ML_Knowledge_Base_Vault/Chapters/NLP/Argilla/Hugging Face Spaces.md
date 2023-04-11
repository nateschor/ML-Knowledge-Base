
#argilla 
#HuggingFace

## Deploying

Find a button to deploy on HF Spaces here:
https://huggingface.co/docs/hub/spaces-sdks-docker-argilla

Pick owner (user not org) and license (unknown).

# Setting password and API_key

There are two users, *team* and *argilla*

TEAM_API_KEY, ARGILLA_API_KEY, TEAM_PASSWORD and ARGILLA_PASSWORD need to be set as "Repository secrets" (in settings)

## Generate API-key and password

```r
library(uuid)
UUIDgenerate()

library(password)
password(8)

```


# Finding api_url
On the space website, click three vertical dots and "embed this Space"