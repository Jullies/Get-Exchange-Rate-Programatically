# Get-Exchange-Rate-Programatically
Gives currencies upto the previous day. For instance am using 

# Installing using pip
pip install curr-exchange==1.0.0


# Using it in your Python Code

from curr_exchange import get_exchange

''' METHOD 1 '''
history_check = get_exchange.beginCheck(from_date="2021-01-01", to_date=False, from_currency='EUR', to_currency='KES')
history = history_check.gotten_currency
print(history) #Returns a dictionary

Output >> {'2021-02-25': {'value': 133.4787, 'details': ['Thursday', '2021-02-25', '1 EUR =133.4787 KES']}, '2021-02-24': {'value': 133.6242, 'details': ['Wednesday', '2021-02-24', '1 EUR =133.6242 KES']}, '2021-02-23': {'value': 133.2971, 'details': ['Tuesday', '2021-02-23', '1 EUR =133.2971 KES']}, '2021-02-22': {'value': 133.3624, 'details': ['Monday', '2021-02-22', '1 EUR =133.3624 KES']}, '2021-02-21': {'value': 133.1358, 'details': ['Sunday', '2021-02-21', '1 EUR =133.1358 KES']}}

yesterday_exchange = history[history_check.correctKey('2021-02-25')] #correctKey formarts dd-mm-yyyy or yyyy-mm-dd to required key /Use any formart
yersterday_value = yesterday_exchange['value']
yersterday_details = yesterday_exchange['details']

print(yesterday_exchange)
print("Values>> ", yersterday_value)
print("Details>> ", yersterday_details)

Output >> 
{'value': 133.4787, 'details': ['Thursday', '2021-02-25', '1 EUR =133.4787 KES']}
Values:   133.4787
Details:   ['Thursday', '2021-02-25', '1 EUR =133.4787 KES']


''' METHOD 2 '''
history_checktWO = get_exchange.beginCheck(from_currency='EUR', to_currency='USD') #correctKey formarts dd-mm-yyyy or yyyy-mm-dd to required key /Use any formart
usdValue = history_checktWO.gotten_currency[history_checktWO.correctKey('2021-02-05')]['value']
print("USD value: %s"%(usdValue))


Output >> 
{'value': 133.4787, 'details': ['Thursday', '2021-02-25', '1 EUR =133.4787 KES']}
Values:   133.4787
Details:   ['Thursday', '2021-02-25', '1 EUR =133.4787 KES']
USD value: 1.2048


# OTHER IMPORTANT METHODS

''' OTHER METHODS '''
check = get_exchange.beginCheck()
#Reformarts date to how keys in dictioray are passed, use these and you won't find errors with your date
print(check.correctKey('1-1-2020'),' | ', check.correctKey('01-01-2020'),' | ', check.correctKey('2020-01-01'))
a = check.returnDateSysFormart('01-02-2021')
print("retrun date in system formart: ", a)
b = check.returnDateHumanFormart(a)
print("return date string in human formart: ", b)
c = check.returnDateString(b)
print("return date (string) in system formart: ", c)
f = {'eur': 5, 'kes': 6, "usd": 7}
print("\nDictionary %s returns keys to list: %s"%(f, check.keysToList(f)))

>>Output
2020-01-01  |  2020-01-01  |  2020-01-01 \n
retrun date in system formart:  2021-02-01 00:00:00 \n
return date string in human formart:  01-02-2021 \n
return date (string) in system formart:  2021-02-01 \n
Dictionary {'eur': 5, 'kes': 6, 'usd': 7} returns keys to list: ['eur', 'kes', 'usd'] \n




