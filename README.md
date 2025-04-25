# 🧒 Vigilância do Desenvolvimento Infantil

[![Licença MIT](https://img.shields.io/badge/Licença-MIT-green.svg)](LICENSE)

Ferramenta para monitoramento e análise do desenvolvimento infantil na saúde pública.

## 🚀 Começando

### Pré-requisitos
- Python 3.8+
- pip

### Instalação
```bash
git clone https://github.com/Kedma-Montedori/vigilancia-infantil.git
cd vigilancia-infantil
pip install -r requirements.txt
📦 Estrutura do Projeto
vigilancia-infantil/
├── src/               # Código fonte principal
├── tests/             # Testes automatizados
├── data/              # Dados de exemplo
├── docs/              # Documentação
├── requirements.txt   # Dependências
└── README.md
🤝 Como Contribuir
Faça um fork do projeto

Crie uma branch (git checkout -b feature/nova-feature)

Commit suas mudanças (git commit -m 'Adiciona nova feature')

Push para a branch (git push origin feature/nova-feature)

Abra um Pull Request


### 📂 2. Vamos criar a estrutura de pastas básica
Execute no terminal:

```bash
cd vigilancia-infantil
mkdir src tests data docs
touch src/__init__.py tests/__init__.py
📝 3. Vamos criar um requirements.txt básico
Crie um arquivo requirements.txt com:

pandas>=1.3.0
numpy>=1.21.0
python-dotenv>=0.19.0
💻 4. Vamos adicionar um script inicial
Crie src/main.py com:

python
def main():
    print("Sistema de Vigilância do Desenvolvimento Infantil")
    print("Versão 0.1")
    
if __name__ == "__main__":
    main()
🔒 5. Configurar o GitHub (opcional mas útil)
Vá em Settings > Branches

Adicione uma regra para a branch main:

Exigir pull request antes de merge

Exigir aprovações

Exigir checagens de status

