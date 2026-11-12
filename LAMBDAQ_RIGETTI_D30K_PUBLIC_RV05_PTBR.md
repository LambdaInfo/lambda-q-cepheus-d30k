# Lambda-Q — Protocolo Prospectivo de Reprodutibilidade na Rigetti Cepheus (D30K)

**Lambdainfo Tecnologia Ltda. · Texto público RV-05 · 12 de novembro de 2026**

**Finalidade:** pré-registrar a coleta e a avaliação de 30.000 shots completos futuros. A marca temporal pública será a data efetiva do release no GitHub e do arquivamento no Zenodo, não as datas históricas indicadas adiante. Não se promete resultado positivo nem acerto mínimo.

## 1. Pergunta científica e escopo

A configuração já utilizada do Lambda-Q consegue reproduzir seu comportamento anteriormente relatado de inferência de erro lógico e qualificação seletiva em três novas sessões, separadas temporalmente, na mesma cadeia física da Rigetti Cepheus com código de repetição? O estudo mede reprodutibilidade; não demonstra, por si só, tolerância universal a falhas, vantagem comercial quântica ou transferência para outros aparelhos.

A implementação principal avaliada será **o pipeline histórico utilizado na D10K (09/11/2026) e na D16K (10/11/2026)**, preservando suas regras originais de decisão e seleção. **Não será substituída por parametrizações alternativas**, e nenhuma fórmula ou valor de limiar será alterado para a D30K. O procedimento existente pode calcular estatísticas *sem rótulos* dependentes das medições de detectores do próprio bloco. Portanto, congela-se o procedimento, mas nem todo peso numérico intermediário permanece constante entre blocos. Nenhum novo gabarito de acerto poderá ser usado para reajustar ou escolher o modelo.

### Descrição pública da arquitetura Lambda-Q

O Lambda-Q é uma arquitetura proprietária de processamento clássico, organizada em múltiplas camadas integradas, desenvolvida para análise, recuperação e qualificação de informações lógicas provenientes de processadores quânticos. Ela utiliza medições experimentais disponíveis para produzir decisões lógicas, cujo desempenho é avaliado por contagens inteiras de erros, cobertura realizada e comparações pareadas nos mesmos shots físicos. Este pré-registro avalia o **sistema de processamento completo**, sem divulgar sequência interna das camadas, atribuições dos módulos, métodos de decodificação, regras de decisão, coeficientes proprietários ou código-fonte. Os compromissos SHA-256 da §3 preservam as identidades dos artefatos; verificar toda a execução proprietária exige acesso controlado sob confidencialidade acordada.

## 2. Equipamento e desenho de aquisição

| Parâmetro | Especificação pré-registrada |
|---|---|
| QPU | Rigetti Cepheus-1-108Q via Amazon Braket (`us-west-1`) |
| ARN | `arn:aws:braket:us-west-1::device/qpu/rigetti/Cepheus-1-108Q` |
| Código quântico | Repetição, `d=5`, `R=1`, convenção de detector final |
| Qubits físicos de dados | `74, 82, 90, 100, 102` |
| Ancillas físicas | `73, 81, 99, 101` |
| Preparações | `00000`, `01010`, `10101`, `11111` |
| Sessões | `S01`, `S02`, `S03`; intervalo mínimo de 24 horas entre a última submissão de uma sessão e a primeira da seguinte |
| Cada sessão | 4 QASM idênticos × 2.500 shots = **10.000 shots** |
| Campanha | **12 tarefas e 30.000 shots** |

Os quatro circuitos originais serão reutilizados byte a byte em todas as sessões. Serão registrados horários reais, tempo de fila, situação da tarefa, proveniência de calibração disponível e identificadores AWS. Não se declara intervalo máximo nem se presume que datas distintas impliquem novas calibrações. Se a QPU estiver indisponível, o atraso ou a sessão não realizada e sua causa serão informados; nenhuma preparação ou sessão poderá ser omitida para favorecer um resultado. Uma nova tentativa após falha preservará sua identidade, com histórico de ARN/estado e divulgação de todas as tentativas. Reenvios pagos não serão automáticos.

Custo nominal histórico: 12 × US$ 0,30 + 30.000 × US$ 0,000425 = **US$ 16,35**; não representa cotação atual nem autorização para gastos. A execução na QPU requer autorização expressa separada.

## 3. Identificação criptográfica de artefatos privados existentes

A tabela registra os identificadores SHA-256 completos. Valores privados, módulos internos e estado da memória **não integram** esta publicação. Os controles indicados como candidatos devem ser verificados byte a byte no ambiente executor antes da coleta; se o executável aprovado for diferente, o registro deverá ser atualizado *antes* dos novos shots.

| Artefato | SHA-256 |
|---|---|
| `LAMBDA3_CAMPO_CONGELADO_20261031.json` | `cec4b9d9957bacffffe6c9fb8f89ab2ecbc74819b4065ef4a7431eaadbd7fcbf` |
| `LIMIAR_CONGELADO_20261108.json` | `5811c3db3cce3426ba0e58e06f23035ff2a0cbb45e062ee139e8f2a82f04b11c` |
| `LOG_L8_CONGELADO_20261108.json` | `c43cba708013e1dee0ed7e2f0dfaba68d9d038f336dee66a87c4b232135e58fb` |
| `QASM 00000` | `f46c7930d032e7ec5b2a13f69989d3be393f646028d0d8814898de68e205240c` |
| `QASM 01010` | `c4ea78bb5fcbd1e33fe067a29bf8a17208f38920c8a4c682915db48cd251bbd7` |
| `QASM 10101` | `a9b29d7f34414992b8dafb1e2a90592a969b0550f67ee0b823740980f35f1cf7` |
| `QASM 11111` | `f602234065fe3d4821c8f37b31e9e1a7fcc7b090dc5640c88cb2cf2b337b6670` |
| `LAMBDAQ_ORIGINAIS_CADEIA_D_20261109.zip (historical private package)` | `abb8b62c96563c2113fcf02909c2beecece7809536b14220db344f889d0a60cf` |
| `controle_d30k.py (candidate)` | `5bed16a97cd1838d80d34f07101c30b279bc7572e36ac201aa7784bc84e97755` |
| `verificar_d30k.py (candidate)` | `596c3b8d56b21b004c3f58f5b5963c0e45072d25ec9ccca0d28ef92d9c0dfe04` |


O campo histórico tem congelamento declarado em 31/10/2026; o arquivo de limiares e a memória histórica, em 08/11/2026. O corpus informado para derivação dos limiares compreendia 24.200 observações até 05/11/2026: 1.200 de 24/10, 3.000 de 26/10, 5.000 de 30/10 e 15.000 de 05/11. A procedência por tarefa e a inexistência de sobreposição exigem conferência independente. D10K e D16K não integram a pontuação prospectiva da D30K.

Os hashes permitem verificar identidade byte a byte **quando os arquivos privados forem apresentados a auditor autorizado**; sozinhos não provam datas de criação anteriores nem reproduzem o algoritmo proprietário.

## 4. Definição pública da medição

Para cada shot, `p[0..4]` são os cinco bits preparados conhecidos, `d[0..4]` os bits de dados medidos ao final e `S[0..3]` os quatro resultados das ancillas, conforme a ordem registrada. O mapeamento de detectores e observável é:

```text
T[c]       = p[c] XOR p[c+1]                c = 0..3
D[c]       = S[c] XOR T[c]                  c = 0..3
D[4+c]     = S[c] XOR d[c] XOR d[c+1]      c = 0..3
L_observed = XOR(d[0..4]) XOR XOR(p[0..4])
```

A *contagem integral de erros lógicos* é o número inteiro de shots em que a previsão de inversão da paridade lógica difere de `L_observed`. O gabarito será utilizado na avaliação **após** o registro da previsão/seleção, não para escolhê-la. Todo shot válido adquirido permanece no denominador de shots completos. A abstenção é contabilizada, jamais apagada do registro bruto.

## 5. Configurações seletivas preservadas, sem promessa de desempenho

As modalidades já usadas são **100%**, **90% nominal** e **66,7% nominal**. Os limiares privados originais e bandas históricas estão comprometidos pelo arquivo indicado na §3; os coeficientes numéricos não serão divulgados. **Não serão ajustados** para forçar cobertura ou erro observado dentro da faixa. A memória e as regras congeladas não serão treinadas usando os gabaritos dos novos shots.

*Cobertura nominal* é o nome de uma configuração previamente fixada; *cobertura realizada* é a contagem efetiva de aceitos dividida pela quantidade de shots completos. Podem ser diferentes, inclusive porque a versão histórica executa processamento não supervisionado dependente do próprio bloco. A compatibilidade com bandas históricas será informada, inclusive `FORA` quando ocorrer. Um valor `FORA` **não será reinterpretado depois** como sucesso ou fracasso. A taxa seletiva sempre terá denominador de aceitos, diferente da taxa integral a 100%.

Este pré-registro **não exige nem prevê** taxa máxima de erro, cobertura exata realizada, ganho garantido ou resultado favorável. Trata-se de **estudo prospectivo de reprodutibilidade e estimação**, não de promessa de desempenho com aprovação/reprovação binária.

## 6. Métodos de referência e comparações

Os mesmos shots físicos serão avaliados com três classes de referência predefinidas: (a) ausência de correção, prevendo nenhuma inversão lógica; (b) MWPM de pesos uniformes sobre os oito detectores; e (c) máxima verossimilhança lógica exata em modelo uniforme, usando os mesmos detectores e uma probabilidade de falha fixa conforme sua implementação de referência. Nenhum comparador poderá usar o observável lógico absoluto como entrada de previsão, nem será ajustado pelos gabaritos da D30K. Comparações que dependam de parâmetro ainda não comprovadamente congelado antes da aquisição serão identificadas como **secundárias/exploratórias**, não declaradas confirmatórias por conveniência.

A diferença no número de erros integrais será relatada como contagem inteira em shots pareados, com os números de casos em que o Lambda-Q acertou e a referência errou, e vice-versa. Nenhuma diferença positiva é exigida. Resumos estatísticos deverão respeitar as subdivisões por preparação e sessão; significância exploratória será identificada como tal se não houver regra completa de testes e multiplicidade publicada antes dos shots.

## 7. Divulgação obrigatória dos resultados

Serão divulgadas **12 linhas**, três sessões × quatro preparações, e os resumos por sessão antes do agregado: número de shots, erros lógicos integrais por método, contagem de aceitos e de erros entre aceitos em cada modalidade, cobertura realizada, erro condicional, hash do QASM e do RAW, identificador da tarefa e horário UTC. Falhas, interrupções, tentativas repetidas e exceções serão registradas; dados ausentes não serão preenchidos. Todos os resultados, inclusive pioras ou desvios de bandas, serão preservados. As células individuais de 2.500 shots documentam heterogeneidade, mas não são apresentadas como comprovação isolada de diferenças pequenas.

Os 30.000 shots futuros serão exclusivamente de avaliação. Cada derivação deverá ser rastreável ao RAW. As decisões preditas deverão ter rastro lacrado antes de diagnósticos posteriores ou revisões de parâmetros. A verificação dessa exigência poderá ser feita em auditoria independente controlada, sem publicação dos módulos proprietários.

## 8. Evidências anteriores, separadas da nova campanha

As contagens históricas abaixo foram **relatadas anteriormente, sem reprocessamento independente nesta preparação editorial**, e não são resultados da D30K:

| Conjunto anterior | Data | Shots completos | Erros integrais | Aceitos (modalidade histórica nominal 2/3) | Erros entre aceitos |
|---|---|---:|---:|---:|---:|
| D10K | 09/11/2026 | 10.000 | 260 | 6.877 | 50 |
| D16K | 10/11/2026 | 16.000 | 330 | 10.909 | 69 |
| Soma descritiva | — | 26.000 | 590 | 17.786 | 119 |

A taxa integral descritiva corresponde a **590/26.000 = 2,2692%**. Entre os aceitos é **119/17.786 = 0,6690%**, com **17.786/26.000 = 68,4077%** de cobertura realizada. São medidas históricas condicionais, não fidelidade do hardware nem previsão garantida para a D30K. A auditoria histórica D16K registrou ocorrências `FORA` das bandas. Análises posteriores com configuração de processamento alternativa devem ser identificadas como **retrospectivas e separadas**, sem confusão com a execução histórica.

## 9. Propriedade intelectual, proveniência e sequência de publicação

A versão pública contém apenas este protocolo, manifesto criptográfico e apresentação breve. Não divulga implementação privada do decoder, interfaces internas, coeficientes numéricos, campo físico, log proprietário, credenciais ou RAW não autorizado. A reprodução integral por terceiro exige acesso controlado sob confidencialidade e autorizações aplicáveis.

O protocolo aprovado e seus hashes serão lançados como release do GitHub e arquivados no Zenodo com DOI **antes da primeira tarefa D30K**. Após a coleta, uma segunda publicação citará o DOI anterior e divulgará resultados, hashes, procedência e desvios ao protocolo. Mudanças posteriores à publicação que afetem o compromisso resultarão em **nova versão explícita, antes da aquisição**, nunca em substituição silenciosa.

**Situação:** protocolo público preparado para publicação. Data do depósito, endereço do release GitHub e DOI Zenodo serão registrados somente após a publicação efetiva. Não se declara tarefa D30K autorizada ou executada; a execução paga exige aprovação separada.
