# LUMITY — Loja de impressão 3D

Projeto pronto para abrir no VS Code. Stack: **Next.js 16, React 19, TypeScript e CSS responsivo**, sem necessidade de banco de dados para esta primeira versão.

## Rodar no Windows / VS Code

1. Instale **Node.js 20.9 ou superior**, se ainda não tiver.
2. Extraia o ZIP e abra a pasta `lumity-loja` no VS Code (`Arquivo > Abrir Pasta`).
3. No terminal do VS Code (PowerShell), rode:

```powershell
npm install
Copy-Item .env.example .env.local
npm run dev
```

4. Acesse **http://localhost:3000** no navegador.

Para parar: `Ctrl + C` no terminal.

## Configurar o WhatsApp

Abra `.env.local` e substitua por **seu número REAL**, só dígitos, sem +, parênteses ou hífen:

```env
NEXT_PUBLIC_WHATSAPP_NUMBER=5511999999999
```

O número acima é **exemplo**. Salve o arquivo e reinicie o servidor com `Ctrl + C` e `npm run dev`.

**Sem número configurado**, o carrinho permite copiar o texto do pedido, mas não abre a conversa. O pedido contém itens, subtotal, nome opcional e observações; o cliente confirma frete e disponibilidade diretamente com a loja. Não há pagamento automático.

## Editar produtos e preços

Arquivo: `src/data/products.ts`.

- `name`: título do produto
- `price`: preço em reais (número com ponto: `24.90`)
- `category`: Organização, Fitness ou Gamer
- `image`: caminho da imagem dentro de `public/images/`
- `description`: detalhes e especificações

**ATENÇÃO:** os preços iniciais são **demonstrativos**, não preços reais informados pela Lumity.

## Trocar banners e imagens

Coloque as imagens na pasta `public/images` e altere os caminhos correspondentes. O banner principal é `public/images/banner-lumity.png`.

## Funcionalidades desta versão

- Vitrine Lumity com identidade azul-marinho, dourado e mármore
- Imagens dos produtos fornecidas
- Layout adaptado a computador e celular
- Pesquisa, categorias, detalhes dos produtos
- Carrinho com quantidade, remoção e subtotal
- Carrinho salvo no navegador do cliente (`localStorage`)
- Nome e observações do cliente
- Resumo para WhatsApp ou cópia manual
- Seção para solicitar personalizações

## O que ainda NÃO está implementado

- Login/cadastro e área administrativa
- Banco de dados Neon ou gestão de estoque
- Cobrança por Pix/cartão, integração de frete
- Registro centralizado e histórico de pedidos

Para operar com checkout, pagamentos e pedidos persistentes, essas integrações precisam de implementação adicional. **O carrinho atual é local ao navegador e o WhatsApp é um fluxo de orçamento/confirmação**, não uma venda liquidada.

## Verificação e publicação

```powershell
npm run typecheck
npm run build
```

Para publicar na Vercel, envie este projeto a um repositório GitHub e importe-o como projeto Next.js na Vercel, configurando `NEXT_PUBLIC_WHATSAPP_NUMBER` em *Environment Variables*.

## Arquivos principais

```
lumity-loja/
├── public/images/               # imagens fornecidas
├── src/app/layout.tsx           # metadados da página
├── src/app/page.tsx             # página inicial
├── src/app/globals.css          # visual e responsividade
├── src/components/Storefront.tsx # vitrine e carrinho
├── src/data/products.ts         # catálogo e preços
├── .env.example                 # exemplo de configuração
└── package.json                 # scripts e dependências
```
