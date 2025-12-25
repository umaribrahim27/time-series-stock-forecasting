# Global Active Power Forecasting

This repository performs time-series forecasting on the feature:

Global_active_power

The dataset is downloaded automatically from the UCI Machine Learning Repository using ucimlrepo.

Example:

from ucimlrepo import fetch_ucirepo
dataset = fetch_ucirepo(id=235)

## Installation

Install dependencies using the requirements file:

pip install -r requirements.txt

## What this repo does

- fetches the dataset from UCI
- extracts Global_active_power
- prepares the time-series
- runs forecasting models

No manual dataset download is required. Everything loads automatically.

Feel free to extend the notebook or try different models if needed.
