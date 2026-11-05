# Política de segurança

Encontrou uma vulnerabilidade em algum projeto da WinNext? Obrigado por avisar.

- **Não abra uma issue pública.**
- Envie os detalhes para **<!-- TODO: seguranca@seu-dominio.com.br -->** ou use
  **Security → Report a vulnerability** no repositório afetado (quando disponível).
- Inclua: o que encontrou, como reproduzir, impacto possível e, se tiver, uma sugestão de correção.

Respondemos em até 3 dias úteis e mantemos você informado até a correção.

## Para o time

- Nunca commite segredos (`.env`, chaves, tokens). Use **Secrets** do GitHub Actions ou o cofre do provedor.
- Se um segredo vazar num commit: **revogue/rotacione primeiro**, depois limpe o histórico.
- Alertas do Dependabot de severidade alta/crítica têm prioridade sobre features.
