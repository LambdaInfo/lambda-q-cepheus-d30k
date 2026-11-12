# Lambda-Q D30K — Adendo A1 de compromisso criptográfico do runtime

**Natureza:** adendo documental à pré-inscrição prospectiva **RV-05**; não é revisão do método científico, do limiar ou das fórmulas.

**Instituição:** Lambdainfo Tecnologia Ltda.  
**Protocolo original:** RV-05, Rigetti Cepheus D30K (30.000 shots planejados)  
**GitHub Release original:** https://github.com/LambdaInfo/lambda-q-cepheus-d30k/releases/tag/RV-05  
**Commit do protocolo original:** `5cde63c1a013a83faaa7df9879daa0137d500ca0`  
**DOI da versão original:** https://doi.org/10.5281/zenodo.24171772

## Objeto do adendo

O arquivo anexado `RUNTIME_COMPROMISSO_PUBLICO_D30K.json` registra um compromisso SHA-256 sobre **14 módulos Python privados** do runtime Lambda-Q. O material público não distribui o código-fonte, os coeficientes, os limiares internos nem o manifesto privado com nomes e hashes individuais.

- **SHA-256 agregado do manifesto privado canônico:** `71e4417ac350228a29910aadba4d67b17aeccd3b797cfa880fd804866eef0f53`
- **SHA-256 dos bytes exatos do JSON público:** `bfc2e2fdafb52e68da4768acde9a3a3ab75b31e1711c1479ddfb487c7d67d581`
- **Quantidade de módulos comprometidos:** 14
- **Data/hora de criação do compromisso informada no JSON:** `2026-11-12T22:40:44.711826+00:00`
- **Estado de autorização registrado no JSON:** `execution_authorized: false`

O valor `runtime_tree_sha256` corresponde ao SHA-256 de um **manifesto privado em JSON canônico**, contendo caminho relativo, tamanho em bytes e SHA-256 individual dos 14 módulos. **Não é** um hash direto do diretório nem dos bytes concatenados dos arquivos. A validação independente exige apresentação controlada desse manifesto e dos arquivos associados.

## Limites e cronologia

A data `created_utc` é a **data informada de criação local**, não a data de publicação pública. A data publicamente comprovável do adendo será a do commit e/ou depósito efetivo posterior à criação deste documento. O protocolo RV-05 original não é reescrito nem recebe uma data retroativa.

O compromisso demonstra identidade de arquivos somente quando comparado aos respectivos bytes. Não comprova, sozinho, o estado futuro do SageMaker nem qual implementação será de fato carregada na execução. Revalidar os hashes do runtime no ambiente de execução **antes do primeiro shot**, e registrar o resultado no log privado da campanha.

O adendo **não autoriza tarefas AWS, despesas, execução quântica ou alterações no protocolo**. Os critérios e as exclusões originais de RV-05 permanecem vigentes.

## Arquivos integrantes

- `RUNTIME_COMPROMISSO_PUBLICO_D30K.json` — compromisso público original, sem qualquer alteração.
- `ADENDO_RUNTIME_A1_RV05.md` — explicação e proveniência deste adendo.
- `SHA256SUMS_ADENDO_A1.txt` — digests dos dois arquivos acima.

Este documento destina-se a publicação **como adendo posterior**, sem substituir o registro RV-05 nem o DOI da sua versão original. Para incorporar novos arquivos no Zenodo recomenda-se criar uma **nova versão vinculada** ao registro anterior e importar os arquivos originais.
