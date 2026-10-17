# 📊 Ferramenta de Simulação e Alocação de Investimentos em FIIs

Ferramenta desenvolvida no Microsoft Excel para automatizar a simulação de acúmulo de patrimônio, projeção de renda passiva mensal (dividendos) e distribuição de aportes em Fundos Imobiliários (FIIs) de acordo com o perfil do investidor.

---

## ❓ As 5 Perguntas que a Ferramenta Responde

1. **Qual a sugestão de valor para investir com base no meu salário atual?**
   - **Onde aparece:** Célula `D14` (*Sugestão de Investimento (30%)*), calculando 30% do salário informado na célula `D12`.
2. **Qual será o patrimônio acumulado ao final do período de investimento selecionado?**
   - **Onde aparece:** Célula `D20` (*Patrimônio acumulado ?*), calculando o valor acumulado ao final dos anos definidos.
3. **Qual será a renda mensal aproximada de dividendos gerada por esse patrimônio?**
   - **Onde aparece:** Célula `D21` (*Dividendos Mensais ?*), aplicando a taxa de rendimento da carteira sobre o patrimônio acumulado.
4. **Como o meu patrimônio e os dividendos mensais evoluirão em diferentes horizontes de tempo (2, 5, 10, 20 e 30 anos)?**
   - **Onde aparece:** Tabela de **Cenários** no intervalo `A23:D28` (Patrimônio na coluna `C` e Dividendos na coluna `D`).
5. **Como devo dividir o meu aporte mensal entre as categorias de FIIs de acordo com o meu Perfil de Investidor?**
   - **Onde aparece:** Tabela de alocação por **Tipo de FII** no intervalo `B35:D41` (Percentuais sugeridos na coluna `C` e Valores em Reais `R$` na coluna `D`).

---

## 🧮 Lógica de Fórmulas e Cálculos (`VF` e `PROCV`)

### 1. Função `VF` (`FV` - Valor Futuro)
A função `VF` é utilizada para calcular o acúmulo de capital ao longo do tempo com juros compostos e aportes mensais constantes.
- **Cálculo do Patrimônio Principal (`D20`):**
  ```excel
  =VF(taxa_mensal; qtd_anos*12; aporte*-1)
  ----
 #### O que foi Mudado/Melhorado em Relação à Ferramenta do Expert
Uso de Intervalos Nomeados: Substituição de referências de células diretas por nomes amigáveis em fórmulas chave (ex: uso de =patrimonio*rendimento_carteira e =VF(taxa_mensal; qtd_anos*12; aporte*-1)).

Matriz de Busca por Chave Composta: Criação da chave unificada (PERFIL-TIPO) na Planilha_Apoio para permitir que o PROCV altere dinamicamente a divisão do aporte entre 6 categorias detalhadas de FIIs ao trocar a lista suspensa.

Tabela de Projeção de Cenários Temporais: Adição de simulações automáticas de patrimônio e renda passiva para prazos de 2, 5, 10, 20 e 30 anos sem necessidade de alterar as entradas principais.

Cálculo Automático de Dividendos Mensais: Integração direta entre o patrimônio acumulado e a projeção de renda passiva recorrente estimada.

🖼️ Evidências de Funcionamento
Simulação 1 — Perfil Agressivo
Simulação 2 — Perfil Conservador (Mesmos parâmetros de entrada)
