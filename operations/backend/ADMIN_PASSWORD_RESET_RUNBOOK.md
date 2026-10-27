# Runbook — redefinição emergencial de senha administrativa

Este procedimento é para recuperação controlada de uma conta administrativa quando o fluxo autenticado de troca de senha não pode ser usado. Ele exige acesso autorizado ao PostgreSQL e deve ser executado com backup recente e janela de manutenção aprovada.

## Procedimento

1. Identifique a conta pelo login normalizado em minúsculas. Nunca registre a senha temporária em Git, ticket público ou chat.
2. Gere um hash bcrypt fora do banco usando o mesmo custo da aplicação:

```bash
cd backend
node --input-type=module -e "import bcrypt from 'bcrypt'; const senha=process.env.TEMP_ADMIN_PASSWORD; if (!senha || senha.length < 16) throw new Error('TEMP_ADMIN_PASSWORD deve ter pelo menos 16 caracteres'); console.log(await bcrypt.hash(senha, 12))"
```

3. Execute um `UPDATE` preparado usando parâmetros vinculados para o hash e o login normalizado no cliente PostgreSQL aprovado. A forma abaixo é apenas o formato da instrução; não substitua valores por interpolação manual de strings. O `sessionVersion` revoga todos os JWTs existentes:

```sql
UPDATE "Usuario"
SET "passwordHash" = $1,
    "sessionVersion" = "sessionVersion" + 1
WHERE "login" = LOWER($2)
  AND "nivelAcesso" = 'ADMINISTRADOR';
```

4. Confirme que exatamente uma linha foi atualizada. Se o resultado for zero ou mais de uma linha, pare e investigue; não repita às cegas.
5. Remova imediatamente `TEMP_ADMIN_PASSWORD` do ambiente. Confirme login com a senha temporária, altere-a pelo fluxo autenticado `PATCH /auth/senha` e confirme que uma sessão/token anterior é rejeitada; não registre senha, hash ou token. Confirme também que a variável temporária não permanece no processo/shell.
6. Registre apenas a execução e o identificador da conta, nunca a senha ou o hash.

## Limites

Este é um procedimento de emergência, não um substituto para uma UI de gestão de usuários. Não use `prisma migrate reset`, `prisma db push`, exclusão de usuários ou atualização sem a condição de administrador. A implementação futura deve oferecer reset administrativo auditável, exigir confirmação forte e revogar sessões com `sessionVersion`.
