# 🧒 Sistema de Vigilância do Desenvolvimento Infantil (IVD + M-CHAT)

[![Licença MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Python 3.10+](https://img.shields.io/badge/python-3.10%2B-blue)](https://www.python.org/)

## 📌 Introdução
Ferramenta digital para aplicação dos protocolos **IVD** (Instrumento de Vigilância do Desenvolvimento) e **M-CHAT** (Modified Checklist for Autism in Toddlers), conforme padronizados na **Caderneta da Criança (Ministério da Saúde, 2023)**. Automatiza a triagem de riscos no desenvolvimento infantil, possibilidade de gerar relatórios para:

- Unidades Básicas de Saúde (UBS)
- Programas de Atenção Primária
- Ações diretivas em Educação Permanente
- Equipes multiprofissionais (pediatras, fonoaudiólogos, e-Mult, etc.)


## 📋 Funcionalidades
- **Avaliação IVD**: Identificação de atrasos no desenvolvimento por faixa etária (0-24 meses)
- **Triagem M-CHAT**: Detecção de riscos para TEA (Transtorno do Espectro Autista)
- **Relatório Automático**: Geração de resultados para profissionais de saúde


## 🎯 Objetivos
1. **Triagem eficiente**  
   Reduzir em 50% o tempo de aplicação manual dos instrumentos
   

3. **Padronização**  
   Garantir adesão estrita aos critérios do Ministério da Saúde

4. **Rastreamento precoce**  
   Identificar sinais de alerta antes dos 24 meses

5. **Integração**  
   Gerar dados compatíveis com o SISVAN Web

## 📋 Estrutura

vigilancia-infantil/
├── data/
│   ├── ivd_indicadores.json  # Critérios do IVD
│   └── mchat_questions.csv  # Perguntas do M-CHAT
├── src/
│   ├── ivd.py               # Lógica do IVD
│   ├── mchat.py             # Lógica do M-CHAT
│   └── main.py              # Interface
└── requirements.txt
📝 Passo 2: Arquivo de Critérios (IVD)
Crie data/ivd_indicadores.json:

json
{
  "0-6 meses": {
    "motor_grosso": ["Sustenta a cabeça", "Rola na cama"],
    "linguagem": ["Balbucio", "Gritos emocionais"]
  },
  "7-12 meses": {
    "motor_grosso": ["Senta sem apoio", "Engatinha"],
    "linguagem": ["Diz 'mama'/'papa'", "Imita sons"]
  }
}
🧮 Passo 3: Código do IVD (src/ivd.py)
python
import json

class IVD:
    def __init__(self):
        with open('data/ivd_indicadores.json') as f:
            self.criterios = json.load(f)
    
    def avaliar(self, idade_meses, habilidades):
        """Retorna atrasos detectados"""
        faixa = self._determinar_faixa(idade_meses)
        atrasos = []
        
        for dominio, marcos in self.criterios[faixa].items():
            if not any(h in habilidades for h in marcos):
                atrasos.append(dominio)
                
        return atrasos

    def _determinar_faixa(self, idade):
        if idade <= 6: return "0-6 meses"
        elif idade <= 12: return "7-12 meses"
        else: return "12-24 meses"  # Adicione mais faixas
✨ Passo 4: Interface Principal (src/main.py)
python
from ivd import IVD

def main():
    print("Sistema IVD/M-CHAT - Caderneta da Criança\n")
    
    # Exemplo de uso
    ivd = IVD()
    idade = 8  # meses
    habilidades = ["Senta sem apoio", "Diz 'mama'"]  # Dados da consulta
    
    resultados = ivd.avaliar(idade, habilidades)
    
    if resultados:
        print(f"⚠️ Atrasos detectados: {', '.join(resultados)}")
    else:
        print("✅ Desenvolvimento dentro do esperado")

if __name__ == "__main__":
    main()
🔍 Passo 5: Implementando M-CHAT (src/mchat.py)
python
import pandas as pd

class MCHAT:
    def __init__(self):
        self.questions = pd.read_csv('data/mchat_questions.csv')
    
    def aplicar(self, respostas):
        """respostas: dict {pergunta_id: True/False}"""
        score = 0
        for id, resposta in respostas.items():
            if resposta == self.questions.loc[id, 'resposta_risco']:
                score += 1
        return score >= 3  # Critério de risco
Exemplo de data/mchat_questions.csv:

csv
id,pergunta,resposta_risco
1,"O bebê olha quando você chama?",False
2,"O bebê imita sons?",True
🚀 Como Executar
Instale dependências:

bash
pip install pandas
Rode o sistema:

bash
python src/main.py
💡 Próximas Melhorias (Quando Quiser)
Integrar com dados reais da caderneta da criança

Gerar relatórios em PDF automáticos

Criar interface gráfica simples


Exemplo de saída esperada:

Sistema IVD/M-CHAT - Caderneta da Criança

⚠️ Atrasos detectados: linguagem
Posso te enviar os arquivos completos prontos para copiar se preferir!

-----------------------------------------------------

## 🚀 Começando

### Pré-requisitos
- Python 3.10+
- Pacotes: `pandas`, `numpy`

```bash
git clone https://github.com/Kedma-Montedori/vigilancia-infantil.git
cd vigilancia-infantil
pip install -r requirements.txt
📊 Como Usar
1. Avaliação IVD
python
from src.ivd import IVD

ivd = IVD()
resultados = ivd.avaliar(
    idade_meses=8,
    habilidades=["Senta sem apoio", "Diz 'mama'"]
)
2. Triagem M-CHAT
python
from src.mchat import MCHAT

mchat = MCHAT()
respostas = {1: True, 2: False}  # IDs das perguntas
risco_tea = mchat.aplicar(respostas)
🏗️ Estrutura
data/
├── ivd_criterios.json    # Critérios por faixa etária
├── mchat_questions.csv   # Questionário M-CHAT
src/
├── ivd.py               # Lógica do IVD
├── mchat.py             # Lógica M-CHAT
└── main.py              # Interface
📌 Roadmap
Integração com SISVAN

Exportação para PDF

Versão web simplificada

🤝 Contribuição
Contribuições são bem-vindas! Siga o modelo:

Abra uma issue descrevendo a melhoria

Faça um fork e envie seu PR

📜 Licença
Distribuído sob a licença MIT - veja LICENSE para detalhes.
