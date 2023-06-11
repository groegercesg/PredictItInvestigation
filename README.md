# PredictItInvestigation

Investigating prediction markets; often correlated markets are considered to be inefficient (in the academic sense).

This repository will investigate whether this is the case and to what extent it is.

## Usage

The file *predictit_all_markets.csv*, will download all the market data from the public API, it writes a csv file in the project root. To create this, first activate the virtual environment and then run the following commands:

```python
source pred_env/bin/activate
python3 get_market_data.py
```

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