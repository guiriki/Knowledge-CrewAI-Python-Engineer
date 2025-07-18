## Página 31

Agents de IA com Python e LangChain
É uma aplicação prática exatamente dos conhecimentos que abordamos nesta aula, e sugiro que vocês
deem uma conferida!
Graças ao tagging, podemos desenvolver aplicações que entendem o contexto dos dados e os organi-
zam de maneira que façam sentido.
Além disso, existem diversas atividades de categorização que podemos realizar com os modelos de
linguagem, assim como o Rodrigo fez. Esses modelos são grandes ferramentas para estruturar
dados não estruturados, transformando uma vasta gama de informações que, de outra forma, seriam
difíceis de processar, em dados acessíveis e prontos para análise.
Essa capacidade de categorizar e interpretar dados é uma verdadeira revolução na área de análise
de dados. Com o uso de tagging, podemos trabalhar cada vez mais com dados em texto, o que abre
um leque de possibilidades para aplicações em diferentes setores. Seja na análise de sentimentos, no
direcionamento de dúvidas em um chatbot ou na organização de feedbacks de clientes, o tagging se
mostra uma ferramenta poderosa que pode mudar a forma como lidamos com informações.
Portanto, não deixem de conferir o vídeo do Rodrigo e se inspirar nas diversas maneiras de aplicar o
tagging em suas próprias soluções.
Asimov Academy
30


---
## Página 32

Agents de IA com Python e LangChain
06. Extraction - Extraindo e Estruturando Informações de Textos
Olá, pessoal! Bem-vindos a mais um capítulo do nosso curso de Agents de IA com Python e LangChain.
Hoje vamos explorar mais uma aplicação muito interessante e prática ao utilizarmos funções com
modelos de linguagem: a extração de informações de textos. Essa técnica é extremamente útil quando
precisamos lidar com grandes volumes de dados textuais e queremos extrair informações específicas
de forma estruturada. Nosso objetivo hoje será:
• Entender o conceito de extração de informações de textos.
• Aprender a utilizar funções externas para extrair dados específicos.
• Implementar um exemplo prático de extração de datas e acontecimentos de um texto.
• Explorar a aplicação de extração de informações da web utilizando WebScraping.
Vamos começar com um exemplo simples, extraindo datas e acontecimentos de um texto.
Extraindo de Dados de Textos
Vamos supor que temos o seguinte texto e queremos extrair as datas e os acontecimentos mencionados.
Aqui temos um texto que utilizarmos como exemplo:
texto = '''A Apple foi fundada em 1 de abril de 1976 por Steve Wozniak, Steve Jobs e Ronald
Wayne com o nome de Apple Computers, na Califórnia. O nome foi escolhido por Jobs após a
visita do pomar de maçãs da fazenda de Robert Friedland, também pelo fato do nome soar bem
e ficar antes da Atari
�→
�→
�→
nas listas telefônicas.
O primeiro protótipo da empresa foi o Apple I que foi demonstrado na Homebrew Computer Club em
1975, as vendas começaram em julho de 1976 com o preço de US$ 666,66, aproximadamente 200
unidades foram vendidas,[21] em 1977 a empresa conseguiu o aporte de Mike Markkula e um
empréstimo do Bank of America.'''
�→
�→
�→
Para extrair essas informações, vamos criar uma estrutura de dados que represente um acontecimento
com uma data e uma descrição:
from pydantic import BaseModel, Field
from typing import List
from langchain_core.utils.function_calling import convert_to_openai_function
class Acontecimento(BaseModel):
'''Informação sobre um acontecimento'''
data: str = Field(description='Data do acontecimento no formato YYYY-MM-DD')
acontecimento: str = Field(description='Acontecimento extraído do texto')
class ListaAcontecimentos(BaseModel):
"""Acontecimentos para extração"""
acontecimentos: List[Acontecimento] = Field(description='Lista de acontecimentos presentes
no texto informado')
�→
Asimov Academy
31


---