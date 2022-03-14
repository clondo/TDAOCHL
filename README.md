import requests
import pandas as pd
import numpy as np
import csv

key ='input key'
def get_price_history(**kwargs):

    url = 'https://api.tdameritrade.com/v1/marketdata/{}/pricehistory'.format(kwargs.get('symbol'))

    params = {}
    params.update({'apikey' : key})

    for arg in kwargs:
        parameter = {arg: kwargs.get(arg)}
        params.update(parameter)

    return requests.get(url, params=params).json()

df = pd.DataFrame(get_price_history(symbol='MMM', period=1, periodType='day', frequencyType='minute'))

print (df)

