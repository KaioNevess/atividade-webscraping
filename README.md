import requests
from bs4 import BeautifulSoup


url = 'https://tribunademinas.com.br/noticias/cidade'


response = requests.get(url)


if response.status_code == 200:
       html_content = response.text
       soup = BeautifulSoup(html_content, 'html.parser')
       div_noticia =  soup.find_all('div', class_='col-sm-12')

       for noticia in div_noticia:
        manchete = noticia.find('h2')
        if manchete:
           print(manchete.text)
else:
       print('Falha na requisição: Status Code', response.status_code)
              
