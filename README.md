# App POC Telemetria

Repositório consumidor usado para demonstrar a coleta reutilizável de telemetria dos workflows.

## Cenários

Em **Actions → Delivery pipeline → Run workflow**, execute cada cenário:

- `success`: qualidade, build Android, segurança e deploy aprovados;
- `quality_failure`: o gate de qualidade falha e os jobs dependentes não são executados;
- `build_failure`: a compilação Android falha; o deploy é bloqueado;
- `security_failure`: o scan de segurança falha; o deploy é bloqueado;
- `deploy_failure`: qualidade, build e segurança passam, mas a validação pós-deploy falha.

Ao encerrar, `Export workflow telemetry` é disparado por `workflow_run`, consulta os jobs e steps da execução e publica os sinais OTLP. Configure os secrets `OTLP_ENDPOINT` e, se necessário, `OTLP_HEADERS` para apontar para o Collector central.

O consumidor está fixado na versão `v1.0.0` da biblioteca para evitar dependência de uma branch mutável.
