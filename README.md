# Using-GeoJson-API/ Coursera


import urllib.request, urllib.parse, urllib.error
import json
import ssl

ctx = ssl.create_default_context()
ctx.check_hostname = False
ctx.verify_mode = ssl.CERT_NONE

api_key = 42

serviceurl = 'http://py4e-data.dr-chuck.net/json?'

address = input('Enter Location')

parms = dict()
parms['address'] = address
if api_key is not False: parms['key'] = api_key
url = serviceurl + urllib.parse.urlencode(parms)

print('Retrieving', url)
uh = urllib.request.urlopen(url)
data = uh.read().decode(encoding = 'UTF-8',errors = 'strict')
print ('Retrieved', len(data), 'characters')

info = json.loads(data)

print(info['results'][0]['place_id'])
