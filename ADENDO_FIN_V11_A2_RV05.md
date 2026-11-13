# Lambda-Q D30K — Adendo A2: autorização financeira por sessão (FIN V1.1)

**Natureza:** adendo documental posterior ao pré-registro científico RV-05 e ao adendo de runtime A1. Não substitui as versões anteriores, nem altera retrospectivamente seus registros.

**Instituição:** Lambdainfo Tecnologia Ltda.  
**Protocolo original:** RV-05 — Rigetti Cepheus D30K  
**DOI RV-05:** https://doi.org/10.5281/zenodo.24171772  
**DOI RV-05-A1:** https://doi.org/10.5281/zenodo.24180603  
**Release original do GitHub:** https://github.com/LambdaInfo/lambda-q-cepheus-d30k/releases/tag/RV-05

## Objeto e escopo do adendo

O arquivo público `COMPROMISSO_PUBLICO_FIN_V11_A2.json` registra a identidade SHA-256 de uma versão **candidata**, separada, do controlador administrativo de submissão D30K, que exige autorização financeira por sessão. O protocolo científico RV-05, os circuitos QASM, os limiares, o log congelado e o pipeline científico não foram propostos para alteração neste adendo.

- **Controlador original V1 SHA-256:** `5bed16a97cd1838d80d34f07101c30b279bc7572e36ac201aa7784bc84e97755`
- **Controlador candidato FIN V1.1 SHA-256:** `fd86583c3f93a4beafc14a844ab837512b5c85de879425362111220e6367b12f`
- **Verificador sem alteração SHA-256:** `596c3b8d56b21b004c3f58f5b5963c0e45072d25ec9ccca0d28ef92d9c0dfe04`
- **Compromisso do runtime científico de 14 módulos:** `71e4417ac350228a29910aadba4d67b17aeccd3b797cfa880fd804866eef0f53`
- **SHA-256 dos bytes do JSON público A2:** `fa087ca7e01d91e253ba0c1b9f4de6883be42f0a36f0195bcb68a991781523e6`

A autorização foi segmentada em S01, S02 e S03: quatro tarefas e 10.000 shots por sessão, com custo **nominal histórico** de US$ 5,45 por sessão (total de US$ 16,35). A autorização de uma sessão não autoriza as seguintes. O mecanismo é um controle local do aplicativo, não um mecanismo de cobrança antecipada nem um limite financeiro garantido pela AWS.

## Evidência e limitações

Em 12/13 de novembro de 2026, conforme os registros locais fornecidos, foram aprovados **25 testes offline** no SageMaker: quatro testes internos, 17 testes específicos do controle financeiro e quatro testes de regressão. As tarefas simuladas com `MagicMock` não representam submissões reais. Nenhum shot D30K foi executado como parte da preparação deste adendo.

A timestamp `created_utc` dentro do JSON é de criação local do compromisso, **não** de publicação pública. A data/hora verificável de publicação A2 deverá ser obtida do novo commit GitHub e do novo depósito Zenodo, ambos posteriores ao arquivo original.

Os metadados `published: false` e `execution_authorized: false` no JSON original foram preservados byte a byte; refletem o estado declarado no momento da criação do arquivo, não uma autorização futura.

**Nenhuma autorização financeira foi concedida por este adendo.** A aplicação do novo controlador em uma sessão requer verificação do hash instalado, preflight de leitura, checagem de tarefas existentes, confirmação da tarifa efetivamente aplicável e autorização expressa do responsável para a sessão específica, antes de qualquer submissão paga.

## Conteúdo deste adendo

1. `COMPROMISSO_PUBLICO_FIN_V11_A2.json` — compromisso original, sem modificações.
2. `ADENDO_FIN_V11_A2_RV05.md` — nota documental e limites de interpretação.
3. `SHA256SUMS_ADENDO_A2.txt` — digests SHA-256 dos dois documentos acima.

**Exclusões:** o código-fonte proprietário, o diff de implementação, tokens, credenciais e arquivos de autorização financeira não integram esta publicação.
