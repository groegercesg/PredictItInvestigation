# PredictItInvestigation

Investigating prediction markets; often correlated markets are considered to be inefficient (in the academic sense).

This repository will investigate whether this is the case and to what extent it is.

## Setup

### Setup the Environment

We use Python 3.11.3, it should work with different more recent versions as well.

Create the virtual environment and source it.
Then install the packages required.

```bash
python3 -m venv "pred_env"
source pred_env/bin/activate
pip install -r requirements.txt
```

## Development stuff

### Update requirements

```bash
pip freeze > requirements.txt
```