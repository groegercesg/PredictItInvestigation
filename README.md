# PredictItInvestigation

Investigating prediction markets; often correlated markets are considered to be inefficient (in the academic sense).

This repository will investigate whether this is the case and to what extent it is.

## Usage

### Getting market data

The file *predictit_all_markets.csv*, will download all the market data from the public API, it writes a csv file in the project root. To create this, first activate the virtual environment and then run the following commands:

```python
source pred_env/bin/activate
python3 get_market_data.py
```

### Determining if inefficient pricing exists

First, let's work through an example manually. The general theory is, we can buy an equal number of contracts from two different sides of a single issue and gain a profit regardless of which outcome occurs. There are a couple of assumptions, firstly we assume that the cases are mutually exclusive (that if _A_ happens then obviously _B_ cannot) and that there is no _C_ option that could happen. For instance, consider the field of candidates in the [2020 Democratic Presidential Primary](https://en.wikipedia.org/wiki/2020_Democratic_Party_presidential_primaries), up until Super Tuesday there were strong performances registered by > 2 candidates - hence this type of arbitrage wouldn't be possible.

Let's work through an example, using pricing from the [2024 US presidential election market](https://www.predictit.org/markets/detail/7456/Who-will-win-the-2024-US-presidential-election) (from 11th June 2023 16:54pm UTC+1). Consider the following:

Joe Biden Yes: $0.46

Donald Trump Yes: $0.29

**Joe Biden Wins:**
Gain: 1 - 0.46 = 0.54
Fee: 0.54 * 10% = 0.054
Profit: Gain - Fee - Loss(Donald Trump) = 0.54 - 0.054 - 0.29 = **0.196**

**Donald Trump Wins:**
Gain: 1 - 0.29 = 0.71
Fee: 0.71 * 10% = 0.071
Profit: Gain - Fee - Loss(Joe Biden) = 0.71 - 0.071 - 0.46 = **0.179**

As we can see from the worked example above, in either case a profit per contract is reached and a gain of about _26%_ and _23%_ respectively. Obviously, some fairly massively caveats apply:

- There is a non-negligible probability that Donald Trump won't end up being the Republican nominee, this example may not be an valid arbitrage opportunity.
- The above example includes PredictIts 10% fee on gains of trades however it doesn't factor in the 5% withdrawal fee.
- No one is (legally) going to get rich overnight, as an $850 investment limit applies as per [PredictIt rules](https://www.predictit.org/support/how-to-trade-on-predictit).

### Determining Algorithmically

Jupyter Notebooks to determine opportunities:
- ``dual_contracts.ipynb``, looks for contracts with discrepancies in the Yes/No prices.

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