# desafioOnebitcode
[Desafio #1] Automatize a marcação de aulas e ganhe r$100
1. Pré-requisitos
Python instalado na sua máquina.
Gerenciador de pacotes pip.
O navegador Google Chrome (recomendado) e o ChromeDriver correspondente à versão do Chrome instalada.
2. Instalar as dependências
No terminal, rode o seguinte comando para instalar o Selenium:

pip install selenium

Também será necessário baixar o ChromeDriver. Baixe-o aqui, selecione a versão compatível com o seu navegador e adicione o caminho do chromedriver ao PATH do sistema ou inclua no código diretamente.

3. Criar o Script
Aqui está um exemplo básico para marcar as aulas como concluídas. O script seleciona o curso e o módulo e então começa a marcar cada aula com um delay de 5 segundos.

python
Copiar código
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

# Configurar o ChromeDriver
driver = webdriver.Chrome(executable_path='/caminho/para/chromedriver')

# URL de login e cursos
url_login = 'https://exemplo.com/login'
url_curso = 'https://exemplo.com/cursos/nome-do-curso'  # Troque para a URL do curso

# Credenciais de login
email = 'seuemail@exemplo.com'
senha = 'suasenha'

# Acessa a página de login
driver.get(url_login)

# Realizar login
driver.find_element(By.ID, 'email').send_keys(email)
driver.find_element(By.ID, 'password').send_keys(senha)
driver.find_element(By.ID, 'submit-button').click()

# Espera o login ser processado
time.sleep(5)

# Vai para a página do curso escolhido
driver.get(url_curso)

# A partir daqui, o script começa a marcar as aulas como concluídas
# Exemplo para selecionar um módulo específico:
driver.find_element(By.XPATH, '//button[contains(text(), "Nome do Módulo")]').click()
time.sleep(2)

# Lista todas as aulas do módulo
aulas = driver.find_elements(By.XPATH, '//button[contains(text(), "Concluir Aula")]')

# Marcando cada aula com delay de 5 segundos
for aula in aulas:
    aula.click()
    time.sleep(5)

# Fechar o navegador ao final
driver.quit()
4. Personalizações
Escolha do curso e módulo: O script pode ser adaptado para aceitar inputs do usuário sobre o curso e módulos.
Delay personalizável: O delay entre as aulas pode ser ajustado de acordo com a necessidade.
5. Rodando o Script
Salve o script como marcar_aulas.py.
No terminal, vá até o diretório onde o script foi salvo e execute:
bash
Copiar código
python marcar_aulas.py
