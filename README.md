<p align="center">
<h1>FIAP - Faculdade Informática e Administração Paulista</h1>
</p>

<p align="center">
<a href= "https://www.fiap.com.br/"><img src="https://c5gwmsmjx1.execute-api.us-east-1.amazonaws.com/prod/dados_processo_seletivo/logo_empresa/124918/logo-420x100px.png_name_20221121-18288-5b9rii.png" alt="FIAP - Faculdade de Informática e Admnistração Paulista" border="0" width=70% height=70%></a>
</p>

<br>

# 👨🏼‍💻 Integrantes

1. [Levi Passos Silveira Marques](https://www.linkedin.com/in/raphael-dinelli-8a01b278/)
2. [Raphael da Silva](www.linkedin.com/in/raphaelsilva-phael)
3. [Jonas Tadeu V Fernandes]()
4. [Ranna Leslie]()
5. [Raphael Dinelli Neto]()

### GRUPO SP e Interior

---

# 📌 Introdução

## 📄 Descrição da Atividade

Nesta fase do projeto, a FarmTech Solutions avança na aplicação de sensores físicos integrados a um sistema de irrigação inteligente. O objetivo é desenvolver um sistema físico (simulado) que colete dados de sensores de umidade, nutrientes e pH e controle uma bomba de irrigação conforme os valores obtidos. Os dados também devem ser armazenados em um banco de dados SQL, com possibilidade de visualização e análises estatísticas.

## 🔍 Descrição Detalhada

### 💡 Descrição do Projeto
Este projeto tem como objetivo simular um sistema inteligente de monitoramento agrícola utilizando a plataforma Wokwi, que permite a prototipagem virtual de circuitos com microcontroladores, sensores e atuadores. O sistema é controlado por um ESP32, que coleta dados de sensores que representam condições do solo e decide automaticamente se ativa ou não a irrigação.

### 🔍 Sensores simulados:
- Sensor de Fósforo (P): representado por um botão (pressionado = ausência, solto = presença).

- Sensor de Potássio (K): também representado por um botão, com a mesma lógica binária.

- Sensor de pH do solo: representado por um sensor LDR (Light Dependent Resistor), cuja variação de luminosidade simula diferentes níveis de pH, entre 0.0 a 14.0.

- Sensor de umidade do solo: representado por um sensor DHT22, que fornece leituras reais de umidade.

### ⚙️ Funcionamento:
Levamos em consideração o plantio de tomates em estufas, logo essa hortaliça é necessário que o umidade esteja entre 50% e 80%. O ESP32 realiza a leitura dos sensores e aciona uma bomba de irrigação simulada por meio de um relé virtual. O relé funciona como um interruptor, e seu estado (ligado/desligado) é indicado por um LED embutido (aceso = irrigação ativa; apagado = irrigação inativa). A lógica de controle é definida com base nos valores lidos dos sensores, ou seja, **umidade menor 50%, aciona o relé.**

### 🗃️ Banco de Dados:
Os dados obtidos pelo ESP32 são exibidos no monitor serial da Wokwi e, posteriormente, inseridos manualmente em um banco de dados Oracle SQL simulado em Python, com suporte completo às operações CRUD (Create, Read, Update, Delete). Essa etapa visa exercitar a integração entre sistemas embarcados e bancos de dados para análise posterior.

---

## 💻 Código C/C++ ESP32

O projeto foi desenvolvido na <a href="https://wokwi.com">Wokwi</a> junto com extensão para Visual Studio Code, utilizando as extensões <a href="https://platformio.org">PlatformIO</a>, para executar o circuito e compilar o código dentro do VS Code.

#### 🔧 Etapa para executar o projeto

1. **Instalar as extensões no VS Code necessárias para execução** 
- [C/C++ (ms-vscode.cpptools)](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)
- [PlatformIO IDE (platformio.platformio-ide)](https://marketplace.visualstudio.com/items?itemName=platformio.platformio-ide)
- [Wokwi for VS Code (wokwi.wokwi-vscode)](https://marketplace.visualstudio.com/items?itemName=wokwi.wokwi-vscode)

<br>

```bash
code --install-extension ms-vscode.cpptools
code --install-extension platformio.platformio-ide
code --install-extension wokwi.wokwi-vscode
```

<br>

2. **Abra o PlatformIO IDE > Open Project > Seleciona a pasta disponibilizado no Github**

<br>
<img src="./assets/home-platformio.png">
<br>

- <a href="https://github.com/Phaeld/1TIAOA-CAP-01">Baixe no repositório arquivo zip e extraí o projeto</a>

<hr>

Após essa etapa, você pode analisar o código, fazer compilação e teste do circuito, pois dentro dos arquivos `wokwi.toml`, pasta `/.vscode` e a pasta `/.pio` tem os arquivos necessários para executar o programa.

<hr>

# 🚩 Conclusão

Detalhar a conclusão com o tempo

🌱 Projeto Agro: Armazenamento de Dados em Banco SQL com Python
📌 Descrição
Este projeto tem como objetivo armazenar dados de sensores lidos a partir de um ESP32 em um banco de dados Oracle, utilizando Python e SQLAlchemy. As operações CRUD (Create, Read, Update, Delete) são implementadas para gerenciar os dados de forma estruturada, segura e eficiente.

🗂️ Estrutura de Pastas
projeto-agro/
├── dados/
│   └── saida_serial.txt
├── models/
│   └── models.py
│   ├─_init_.py
│ 
│ 
├── scripts/
│   ├── database.py
│
│├── serial_reader.py
│├── crud.py
├── README.md
└── requirements.txt
🧠 Modelagem e Justificativa
A estrutura do banco foi baseada no MER da Fase 2, com as seguintes entidades principais:

UnidadeMedida: Representa o tipo de unidade (ex: Celsius, %).
AreaCapturada: Representa a área onde os dados foram coletados.
SensorMPX: Armazena os dados dos sensores, incluindo valor, data/hora, unidade e área.
Uma trigger e uma sequence no Oracle garantem que o campo id_area_capturada seja preenchido automaticamente, assegurando a integridade referencial.


⚙️ Funcionalidades CRUD
Create: Inserção de novos dados de sensores.
Read: Consulta de registros por ID.
Update: Atualização de valores e relacionamentos.
Delete: Remoção de registros existentes.


🧪 Exemplo de Uso

```py
from crud import create_sensor, read_sensor, update_sensor, delete_sensor
```

# Criar sensor
```py
sensor = create_sensor(30.5, 1, 1)
```

# Ler sensor
```py
sensor_lido = read_sensor(sensor.id_sensor_mpx)
```

# Atualizar sensor
```py
update_sensor(sensor.id_sensor_mpx, vlr_sensor_mpx=35.0)
```

# Deletar sensor
```py
delete_sensor(sensor.id_sensor_mpx)
```


🔌 Leitura Serial do ESP32
O script serial_reader.py realiza a leitura contínua da porta serial e insere os dados automaticamente no banco de dados:
```python
import serial
from crud import create_sensor

ser = serial.Serial('COM3', 9600)

while True:
    if ser.in_waiting > 0:
        line = ser.readline().decode('utf-8').strip()
        try:
            value = float(line)
            create_sensor(value, 1, 1)
        except ValueError:
            print("Valor inválido:", line)
```

🧾 Requisitos
Python 3.10+
cx_Oracle
SQLAlchemy
Oracle Database (ex: Oracle XE)