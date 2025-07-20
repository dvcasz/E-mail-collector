# E-mail Collector 📧

Este projeto é um script em Python que funciona como um **coletor de e-mails** (ou *email scraper*). Ele foi desenvolvido com o objetivo de demonstrar técnicas de **web crawling** e extração de dados com expressões regulares (Regex).

**⚠️ AVISO SOBRE USO RESPONSÁVEL E ÉTICA**
Web scraping é uma ferramenta poderosa, mas deve ser usada com responsabilidade.

* **Respeite os Termos de Serviço**: Antes de executar este script em um site, verifique seus Termos de Serviço e o arquivo `robots.txt` para saber se a extração automatizada de dados é permitida.
* **Não sobrecarregue servidores**: Scripts agressivos podem causar lentidão ou até mesmo derrubar sites pequenos.
* **Uso de Dados**: A coleta e o uso de endereços de e-mail para envio de spam ou marketing não solicitado são antiéticos e, em muitos lugares (como sob a LGPD no Brasil e a GDPR na Europa), **ilegais**.
* Este script foi criado para **fins educacionais**. O autor não se responsabiliza por qualquer uso indevido.

---

## O que o script faz?

O script é um *crawler* que navega por páginas da web para encontrar e extrair endereços de e-mail. O processo funciona da seguinte forma:

1.  **Ponto de Partida**: O script solicita ao usuário uma URL inicial para começar a busca.
2.  **Navegação (Crawling)**: Ele baixa o conteúdo HTML da página e, usando a biblioteca **BeautifulSoup**, encontra todos os links (`<a>` tags) contidos nela.
3.  **Extração de E-mails**: Usando uma **expressão regular (Regex)**, ele varre o texto da página em busca de padrões que correspondam a endereços de e-mail.
4.  **Fila de URLs**: Os links encontrados são adicionados a uma fila para serem visitados posteriormente. O script mantém um registro das páginas já visitadas para não entrar em loops infinitos.
5.  **Repetição**: O processo se repete, pegando a próxima URL da fila, até que a fila se esvazie ou um limite de profundidade (20 páginas) seja atingido.
6.  **Armazenamento**: Todos os e-mails únicos encontrados são armazenados e exibidos na tela.

---

## Como Funciona o Código

* **`requests`**: Biblioteca usada para fazer as requisições HTTP e obter o conteúdo das páginas web.
* **`collections.deque`**: Uma fila otimizada, usada para gerenciar a lista de URLs a serem visitadas. Isso implementa uma busca em largura (*Breadth-First Search*).
* **`BeautifulSoup`**: A principal ferramenta para fazer o *parsing* do HTML, facilitando a busca por tags e atributos, como os links.
* **`re`**: O módulo de expressões regulares do Python, utilizado para identificar e extrair os e-mails do texto.

---

## Requisitos

Para rodar o script, você precisa ter as seguintes bibliotecas instaladas:

```bash
pip install requests beautifulsoup4 lxml
