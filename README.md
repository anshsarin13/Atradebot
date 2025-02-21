## Atradebot

![image](img/Atradebot.jpg)

Bot to help you choose what to invest using AI 

### Install

Requirement:

```
pip install -r requirements.txt
```

Install using pip
```
pip install -e .

if errors do:
```
pip install --upgrade pip
```


## Run 
Go to folder `src/atradebot`

start by setting your plan using .yaml file like in  `default.yaml`: 


Then run `python3 main.py -c default.yaml -m run`
This will get news and suggest what stocks to buy during that time and update the profile `.xlsx` files

## Test strategies
Go to folder `src/atradebot`

Use this to test different strategies using past historical data
```
python backtest.py
```
more params:

```
python src/atradebot/backtest.py --mode simple --init_capital 10000 --start_date 2022-01-31 --end_date 2023-05-20 --stocks "AAPL ABBV AMZN MSFT NVDA TSLA"
```

## Set to run everyday
Go to folder `src/atradebot`

run: `crontab -e`

And add this line to run everyday 8am: 
`0 8 * * * python main.py -c default.yaml -m run`


## Run App

Use the following command to run this bot as an app

```
streamlit run app.py
```

## Train model to predict news 
Go to folder `src/atradebot`

Use this to create a hugginface dataset to train a model
```
python fin_data.py
```
Then run this to train a model
```
python fin_train.py
```


## Sentiment analysis and database

To setup a server to scrape news.

TODO:

- modify script to take in a list of stocks
- main function to run as program
- cron job info


Run with:

```
python news2db.py
```

To set up a cron job on a Unix server you can follow [these instructions](https://www.geeksforgeeks.org/how-to-setup-cron-jobs-in-ubuntu/). 

Add cron job with: 

`
crontab -e
`

Add line:
`
0 4 * * * cd /home/your_dir/Atradebot/src/atradebot/ && python news2db.py
`

This will run the script on your server every day at 4 am. It will collect data every day and store it in the database.




# License

Atradebot is open-source software released under the [Apache 2.0 license](https://github.com/Superalgos/Superalgos/blob/master/LICENSE)