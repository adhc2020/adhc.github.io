“””Code to scrape news from afr.com and write it to HTML””” 
from bs4 import BeautifulSoup as bs
import requests
url = "https://www.afr.com/markets"
page = requests.get(url)
soup = bs(page.content, 'html.parser')
#k = soup.find_all(class_="f14_bold link")
quotes = [i.text for i in soup.find_all(class_="_20-Rx")]
quotes1 = [i.text for i in soup.find_all(class_="_48ktx")]
with open('mypage.html', 'w') as myFile:
   myFile.write('<html>')
   myFile.write('<body>')
   myFile.write('<table>')
   i=0
   while i < len(quotes):
       myFile.write('<tr><td>'+quotes[i]+'</td>' );
       myFile.write('<td>' + quotes1[i] + '</td>');
       i+=1
 
   myFile.write('</tr>')
   myFile.write('</table>')
   myFile.write('</body>')
   myFile.write('</html>')
