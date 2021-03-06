# Get-Exchange-Rate-Programatically
Gives currencies upto the previous day <br/>

# Installing using pip
pip install curr_get_exchange==1.0.0<br/>


# Using it in your Python Code

from curr_get_exchange import get_exchange<br/>

''' METHOD 1 '''<br/>
history_check = get_exchange.beginCheck(from_date="2021-01-01", to_date=False, from_currency='EUR', to_currency='KES')<br/>
history = history_check.gotten_currency<br/>
print(history) #Returns a dictionary<br/>

>>Output{'2021-02-25': {'value': 133.4787, 'details': ['Thursday', '2021-02-25', '1 EUR =133.4787 KES']}, '2021-02-24': {'value': 133.6242, 'details': ['Wednesday', '2021-02-24', '1 EUR =133.6242 KES']}, '2021-02-23': {'value': 133.2971, 'details': ['Tuesday', '2021-02-23', '1 EUR =133.2971 KES']}, '2021-02-22': {'value': 133.3624, 'details': ['Monday', '2021-02-22', '1 EUR =133.3624 KES']}, '2021-02-21': {'value': 133.1358, 'details': ['Sunday', '2021-02-21', '1 EUR =133.1358 KES']}}

yesterday_exchange = history[history_check.correctKey('2021-02-25')] #correctKey formarts dd-mm-yyyy or yyyy-mm-dd to required key /Use any formart<br/>
yersterday_value = yesterday_exchange['value']<br/>
yersterday_details = yesterday_exchange['details']<br/>

print(yesterday_exchange)<br/>
print("Values>> ", yersterday_value)<br/>
print("Details>> ", yersterday_details)<br/>

>>Output <br/>
{'value': 133.4787, 'details': ['Thursday', '2021-02-25', '1 EUR =133.4787 KES']}<br/>
Values:   133.4787<br/>
Details:   ['Thursday', '2021-02-25', '1 EUR =133.4787 KES']<br/>


''' METHOD 2 '''<br/>
history_checktWO = get_exchange.beginCheck(from_currency='EUR', to_currency='USD') #correctKey formarts dd-mm-yyyy or yyyy-mm-dd to required key /Use any formart<br/>
usdValue = history_checktWO.gotten_currency[history_checktWO.correctKey('2021-02-05')]['value']<br/>
print("USD value: %s"%(usdValue))<br/>


>>Output
{'value': 133.4787, 'details': ['Thursday', '2021-02-25', '1 EUR =133.4787 KES']}<br/>
Values:   133.4787<br/>
Details:   ['Thursday', '2021-02-25', '1 EUR =133.4787 KES']<br/>
USD value: 1.2048<br/>


# OTHER IMPORTANT METHODS<br/>

''' OTHER METHODS '''<br/>
check = get_exchange.beginCheck()<br/>
#Reformarts date to how keys in dictioray are passed, use these and you won't find errors with your date<br/>
print(check.correctKey('1-1-2020'),' | ', check.correctKey('01-01-2020'),' | ', check.correctKey('2020-01-01'))<br/>
a = check.returnDateSysFormart('01-02-2021')<br/>
print("retrun date in system formart: ", a)<br/>
b = check.returnDateHumanFormart(a)<br/>
print("return date string in human formart: ", b)<br/>
c = check.returnDateString(b)<br/>
print("return date (string) in system formart: ", c)<br/>
f = {'eur': 5, 'kes': 6, "usd": 7}<br/>
print("\nDictionary %s returns keys to list: %s"%(f, check.keysToList(f)))<br/>

>>Output
2020-01-01  |  2020-01-01  |  2020-01-01 <br/>
retrun date in system formart:  2021-02-01 00:00:00 <br/>
return date string in human formart:  01-02-2021 <br/>
return date (string) in system formart:  2021-02-01 <br/>
Dictionary {'eur': 5, 'kes': 6, 'usd': 7} returns keys to list: ['eur', 'kes', 'usd'] <br/>




