# 🧒 Sistema de Vigilância do Desenvolvimento Infantil

[![Licença MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Python 3.8+](https://img.shields.io/badge/python-3.8%2B-blue)](https://www.python.org/)

Ferramenta para monitoramento de indicadores de saúde infantil na rede pública.

## 📋 Índice
- [Requisitos](#-requisitos)
- [Instalação](#-instalação)
- [Uso](#-uso)
- [Estrutura](#-estrutura)
- [Contribuição](#-contribuição)
- [Licença](#-licença)

## 📝 Requisitos
- Python 3.8+
- pip
- Bibliotecas listadas em `requirements.txt`

## 🛠️ Instalação
```bash
git clone https://github.com/Kedma-Montedori/vigilancia-infantil.git
cd vigilancia-infantil
pip install -r requirements.txt
🚀 Uso
bash
# Execução direta
python src/main.py
python
# Como módulo
from src.analise import processar_dados
processar_dados('dados.csv')
📂 Estrutura
vigilancia-infantil/
├── src/               # Código principal
│   ├── __init__.py
│   ├── main.py        # Ponto de entrada
│   └── core/          # Lógica principal
├── tests/             # Testes automatizados
├── data/              # Dados de exemplo
├── docs/              # Documentação
├── requirements.txt   # Dependências
└── LICENSE            # Licença MIT
🤝 Contribuição
Faça um fork do projeto

branch (git checkout -b feature/nova-feature)

Commit suas mudanças (git commit -m 'Adiciona feature')

Push para a branch (git push origin feature/nova-feature)

Pull Request

📜 Licença
Distribuído sob a licença MIT.
