Tec. Informática -- 1° ano E 

**O projeto em questão tem como objetivo desenvolver um sistema de webscraping, uma técnica de coleta de dados na web, para extrair informações relevantes de diferentes fontes online. A implementação do webscraping permitirá a automação da coleta de dados, proporcionando uma abordagem eficiente e escalável para a obtenção de informações específicas da web.**

**Foi desenvolvido na disciplina de algoritmos por mim Kaio Neves e pela minha dupla Fábio Quintão**
Aqui está o código:

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
              
