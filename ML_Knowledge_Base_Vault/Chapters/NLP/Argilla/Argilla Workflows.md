## What is Argilla?
Argilla is an open-source platform that empowers data annotation and curation. It consists of a powerful Python library called Argilla Client for reading and writing data into Argilla using popular libraries such as transformers, spaCy, and datasets. [The platform also includes an API and UI for data annotation and curation called Argilla Server and UI](https://pypi.org/project/argilla/)[1](https://pypi.org/project/argilla/)[2](https://docs.argilla.io/en/latest/getting_started/quickstart.html)[3](https://github.com/argilla-io/argilla).

We use Argilla from Hugging Face Spaces. 

## Setting up Argilla for new project
If you're setting up Argilla for a new project, follow these steps: [[Hugging Face Spaces]]

## Using argilla for existing project 
In Hugging Face Spaces, Argilla has two users: `team` and `argilla`. The username `team` is the root user who can upload datasets and access any workspace within your Argilla Space. On the other hand, the username `argilla` is a standard user with access to the team workspace and its own workspace called `argilla`[1](https://huggingface.co/docs/hub/spaces-sdks-docker-argilla)[2](https://huggingface.co/docs/hub/spaces-sdks-docker-argilla).

You need to know the URL and password set up when the space was created (see [[Hugging Face Spaces]]). 

Here is code that will get you started with creating a dataset (including embedding vectors for similarity search and logging it to argilla) [[Argilla example of creating dataset]]


