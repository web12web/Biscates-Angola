# BISCATES ANGOLA — MVP inicial

Aplicação web responsiva em React + Vite, preparada para instalação PWA e integração com Supabase. Interface em português, com identidade azul/amarelo.

## Incluído nesta versão
- Página inicial, pesquisa e filtros por categoria/província.
- Registo e login por email/palavra-passe via Supabase Auth.
- Perfis de trabalhador/cliente e edição de dados básicos.
- Publicação e listagem persistente de biscates.
- Lista de trabalhadores e contacto por WhatsApp quando o telefone está disponível.
- Schema SQL com políticas RLS para perfis, anúncios e avaliações.

## O que ainda precisa de configuração/implementação
- Criar projeto Supabase e inserir URL/chave pública no `.env`.
- Executar `supabase/schema.sql` no SQL Editor.
- Configurar confirmação de email e URLs de redirecionamento no Supabase Auth.
- Upload de fotografias, fluxo completo de atribuição/conclusão de trabalhos, avaliações na interface, notificações e moderação são próximas etapas; a tabela de avaliações já está preparada.
- Para produção: rever políticas de privacidade, termos, denúncia/bloqueio, validação de telefones e proteção anti-spam.

## Executar localmente
Requer Node.js 20 ou superior.

```bash
npm install
cp .env.example .env
# Edite .env com as credenciais do seu projeto Supabase
npm run dev
```

Para validar a versão de produção: `npm run build`.

## Configuração gratuita do Supabase
1. Crie um projeto em https://supabase.com/.
2. Em Project Settings → API, copie Project URL e `anon`/publishable key.
3. Coloque os valores em `.env` como `VITE_SUPABASE_URL` e `VITE_SUPABASE_ANON_KEY`.
4. Abra SQL Editor e execute todo o conteúdo de `supabase/schema.sql`.
5. Em Authentication → URL Configuration, configure a URL local (por exemplo `http://localhost:5173`) e depois a URL do domínio publicado.
6. Não coloque `service_role` key no frontend. A chave pública anon é protegida pelas políticas RLS.

## Publicar
Pode publicar o repositório no GitHub e ligar à Vercel. Configure as mesmas variáveis de ambiente nas definições do projeto Vercel. Para instalar no Android, abra o endereço publicado no Chrome e use “Adicionar ao ecrã inicial”. Para uma PWA de produção, recomenda-se adicionar ícones próprios e um service worker com estratégia de cache testada.
