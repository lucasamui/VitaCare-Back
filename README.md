# VitaCare — Back-end

Sistema de gestão de clínica médica. Este repositório contém o back-end em **Django** (telas com templates e uma API REST para o front-end em Vue.js).

## Tecnologias

| Tecnologia | Uso |
|---|---|
| Python 3.12+ | Linguagem |
| Django 5.2 | Framework web e ORM |
| Django REST Framework 3.17 | API REST |
| django-cors-headers | Libera o acesso do front-end Vue |
| oracledb | Driver do banco Oracle |
| python-decouple | Lê as variáveis do arquivo `.env` |

## Funcionalidades

- Cadastro de pacientes, com histórico médico criado automaticamente
- Cadastro de médicos com CRM e especialidade
- Consultas com um ou mais diagnósticos (CID-10)
- Solicitação e acompanhamento de exames
- Receitas com vários medicamentos
- API REST completa para o front-end

## Apps do projeto

| App | O que faz |
|-----|-----------|
| `core` | Página inicial |
| `persons` | Model base de pessoa (herdado por paciente e médico) |
| `patients` | Pacientes |
| `doctors` | Médicos |
| `consults` | Consultas |
| `exams` | Exames |
| `prescriptions` | Receitas |
| `prescriptionitems` | Itens de cada receita |
| `cids` | Códigos CID-10 |
| `medications` | Medicamentos |
| `medicalhistories` | Histórico médico dos pacientes |

O diagrama de classes está em `Diagrama-de-Classe.png`.

## Como rodar

```bash
# 1. criar e ativar o ambiente
python -m venv .venv
.venv\Scripts\activate        # Windows
source .venv/bin/activate     # macOS / Linux

# 2. instalar as dependências
pip install -r requirements.txt

# 3. configurar o .env (copie o modelo e preencha)
copy .env.example .env        # Windows
cp .env.example .env          # macOS / Linux

# 4. criar as tabelas e o usuário admin
python manage.py migrate
python manage.py createsuperuser

# 5. subir o servidor
python manage.py runserver
```

Acesse `http://localhost:8000`. O painel admin fica em `/admin/`.

### Variáveis do `.env`

| Variável | Exemplo |
|---|---|
| `SECRET_KEY` | chave secreta do Django |
| `DEBUG` | `True` |
| `DB_NAME` | `host:porta/service_name` |
| `DB_USER` | usuário do banco |
| `DB_PASSWORD` | senha do banco |

## API REST

Base: `http://localhost:8000/api/`

| Endpoint | Recurso |
|----------|---------|
| `/api/patients/` | Pacientes |
| `/api/doctors/` | Médicos |
| `/api/consults/` | Consultas |
| `/api/exams/` | Exames |
| `/api/prescriptions/` | Receitas |
| `/api/prescriptionitems/` | Itens de receita |
| `/api/cids/` | CIDs |
| `/api/medications/` | Medicamentos |
| `/api/medicalhistories/` | Históricos médicos |

Todos aceitam `GET`, `POST`, `PUT`, `PATCH` e `DELETE`.

## Integrantes

- Lucas Veras Amui
- Vitor Mateus Alves de Souza
