## Garantir integridade visual em Desktop, Tablet e Celular

Antes de considerar qualquer alteração ou projeto como concluído, faça obrigatoriamente uma auditoria completa da interface em **desktop, tablet e celular**.

O objetivo é garantir que nenhuma alteração feita em uma resolução quebre, prejudique ou desconfigure as demais.

### Verifique no mínimo estas larguras

- Desktop grande: `1440px`
    
- Desktop/notebook: `1280px`
    
- Tablet horizontal: `1024px`
    
- Tablet vertical: `768px`
    
- Celular grande: `430px`
    
- Celular padrão: `390px`
    
- Celular pequeno: `360px`
    

Não desenvolva pensando apenas nesses breakpoints. Teste também larguras intermediárias para identificar quebras durante o redimensionamento.

### Audite

Verifique em todas as resoluções:

- Header e navegação
    
- Menus desktop e mobile
    
- Hero
    
- Títulos, subtítulos e textos
    
- Botões e CTAs
    
- Formulários
    
- Imagens
    
- Vídeos
    
- Cards
    
- Grids
    
- Flexbox
    
- Seções
    
- Modais e pop-ups
    
- Footer
    
- Elementos fixos ou sticky
    
- Elementos com `position: absolute`
    
- Margens e paddings
    
- Espaçamento entre seções
    
- Alinhamentos
    
- Bordas e border-radius
    
- Ícones
    
- Animações
    
- Estados hover, active e focus
    
- Scroll horizontal
    
- Overflow
    
- Quebras de texto
    

### Regras obrigatórias

1. **Nunca corrija o mobile quebrando o desktop.**
    
2. **Nunca corrija o desktop quebrando tablet ou mobile.**
    
3. Preserve a identidade visual, hierarquia, proporções e intenção original do layout.
    
4. Elementos não podem sair da viewport.
    
5. Não pode existir scroll horizontal acidental.
    
6. Textos não podem ficar cortados ou sobrepostos.
    
7. Botões não podem ultrapassar seus containers.
    
8. Imagens devem manter proporção correta e não deformar.
    
9. Cards e grids devem reorganizar-se naturalmente conforme a largura disponível.
    
10. Não esconda elementos importantes apenas para resolver problemas de responsividade.
    
11. Não use valores fixos desnecessários quando uma solução responsiva com `%`, `rem`, `clamp()`, `min()`, `max()`, `minmax()`, Flexbox ou Grid for mais adequada.
    
12. Evite criar vários media queries remendando o mesmo problema. Corrija a causa estrutural sempre que possível.
    
13. Não altere conteúdo, identidade visual ou comportamento funcional sem necessidade.
    
14. Certifique-se de que os elementos clicáveis tenham tamanho confortável no touch.
    
15. No mobile, não permita aqueles contornos/quadrados azuis indesejados ao tocar em botões, links ou campos, mantendo porém estados de foco acessíveis para navegação por teclado.
    

### Tipografia responsiva

Confirme que:

- títulos não fiquem gigantes no mobile;
    
- textos não fiquem pequenos demais;
    
- `line-height` continue confortável;
    
- não existam palavras cortadas;
    
- não existam linhas excessivamente longas no desktop;
    
- escalas tipográficas permaneçam coerentes entre dispositivos.
    

Prefira `clamp()` quando adequado.

### Teste de redimensionamento

Além dos tamanhos definidos, redimensione mentalmente ou tecnicamente a viewport continuamente de aproximadamente:

`320px → 1920px`

Observe se existe algum ponto intermediário em que:

- o layout quebra;
    
- elementos colidem;
    
- aparecem espaços excessivos;
    
- cards ficam estreitos demais;
    
- textos escapam;
    
- o menu quebra;
    
- surge scroll horizontal;
    
- elementos mudam abruptamente de posição.
    

Caso encontre, corrija.

## Galerias

Nunca devem ter sombras.

No mobile devem ser sempre um carrossel infinito com setas para indicar a passagem para o usuário.

Sempre que clicar na imagem elas se abrem em pop-up e permite a passagem também com setas.

Sempre coloque as tags dentro das imagens, centralizado, "Antes" a esquerda e "Depois" a direita.

### Antes de finalizar

Faça uma última rodada de auditoria:

**Desktop → Tablet → Mobile → Tablet → Desktop**

Isso é importante para garantir que media queries e alterações feitas posteriormente não tenham criado regressões.

Considere a tarefa concluída somente quando a página estiver visualmente íntegra e funcional em todos esses formatos.

Ao terminar, reporte de maneira curta:

- problemas encontrados;
    
- correções realizadas;
    
- arquivos modificados;
    
- confirmação de que Desktop, Tablet e Mobile foram revisados.

## Garantir validação e integridade dos formulários

Antes de considerar qualquer formulário concluído, faça uma auditoria completa de todos os campos e garanta que as validações funcionem tanto ao **digitar quanto ao colar conteúdo**.

As validações devem acontecer no front-end e impedir a entrada de caracteres inválidos sempre que possível.

### Nome

Campos de nome devem aceitar **somente letras e caracteres legítimos utilizados em nomes**.

Permitir:

* Letras de `A-Z` e `a-z`
* Letras acentuadas: `á`, `ã`, `ç`, `é`, `ô`, etc.
* Espaços
* Apóstrofos quando fizerem parte de nomes
* Hífens quando fizerem parte de nomes compostos

Não permitir:

* Números
* Caracteres especiais indevidos
* Emojis
* Símbolos

Exemplo:

`Eduardo Gonçalves` → válido

`Eduardo123` → inválido

`Edu@rdo` → inválido

### Comportamento obrigatório

Se o usuário tentar digitar um número ou caractere inválido no campo de nome, **o caractere não deve sequer aparecer no campo**.

A mesma sanitização deve ocorrer ao colar texto.

Exemplo:

Usuário cola:

`Eduardo123 Gonçalves`

Resultado no campo:

`Eduardo Gonçalves`

---

## Telefone / WhatsApp

Campos de telefone devem aceitar **exclusivamente números brasileiros no formato:**

`DDD + número`

O usuário NÃO deve informar código internacional.

### Deve aceitar

Celular:

`17999999999`

Telefone fixo:

`1732323232`

Aplicar máscara visual quando adequado:

`(17) 99999-9999`

ou

`(17) 3232-3232`

O valor pode ser formatado visualmente, mas internamente deve permanecer normalizado.

### Não permitir letras

Se o usuário digitar letras:

`17abc999999999`

As letras **não devem sequer aparecer no campo**.

Ao colar:

`17abc99999-9999`

Sanitize automaticamente e mantenha apenas o telefone válido.

---

## Código nacional +55

O formulário trabalha somente com números brasileiros, portanto o código nacional:

`+55`

ou um `55` utilizado como prefixo internacional

**não deve permanecer no campo.**

Se o usuário colar:

`+55 17 99999-9999`

normalize automaticamente para:

`17 99999-9999`

Se colar:

`5517999999999`

normalize para:

`17999999999`

Ou seja:

**remova o código de país 55 e mantenha somente DDD + telefone.**

### ATENÇÃO: DDD 55 existe

Não confunda o código internacional `55` com o **DDD brasileiro 55**, que é válido.

Por exemplo:

`55999999999`

pode representar:

`DDD 55 + 99999-9999`

e portanto deve ser aceito.

A remoção do `55` deve acontecer somente quando for possível identificar que ele está sendo utilizado como **código de país adicional**, por exemplo pela presença de `+55` ou pela quantidade de dígitos indicando:

`55 + DDD + telefone`

Nunca remova automaticamente um `55` que seja o próprio DDD.

---

## Digitação

Durante a digitação do telefone:

* Não permitir letras.
* Não permitir `+`.
* Não permitir caracteres especiais digitados manualmente, exceto os utilizados pela própria máscara.
* Não permitir mais dígitos do que um telefone brasileiro válido.
* Aplicar máscara progressivamente.
* Manter somente os números necessários internamente.

Não espere o submit para descobrir que o conteúdo é inválido.

**Impeça ou normalize durante a própria entrada.**

---

## Colagem

Nunca confie no conteúdo vindo do clipboard.

Ao executar `paste`:

1. Capture o conteúdo.
2. Remova letras e caracteres inválidos.
3. Detecte e remova `+55` quando existir.
4. Detecte código nacional `55` adicional quando inequivocamente for código do país.
5. Preserve DDD `55` quando ele for realmente o DDD.
6. Remova espaços, parênteses e hífens antes da validação interna.
7. Limite ao tamanho de um telefone brasileiro válido.
8. Reaplique a máscara visual.

---

## Todos os campos são obrigatórios

**Todos os campos existentes no formulário devem ser obrigatórios.**

Não deve ser possível realizar o submit caso qualquer campo esteja:

* vazio;
* preenchido somente com espaços;
* incompleto;
* inválido;
* fora do formato esperado.

Não dependa somente do atributo HTML `required`.

Faça também validação via JavaScript.

---

## Submit

Antes de permitir o envio:

1. Execute uma validação completa novamente.
2. Verifique todos os campos obrigatórios.
3. Valide nome.
4. Valide telefone.
5. Normalize os valores.
6. Bloqueie o submit caso exista qualquer erro.
7. Mostre uma mensagem clara próxima ao campo problemático.
8. Coloque o foco no primeiro campo inválido.
9. Só envie os dados após todas as validações serem aprovadas.

---

## Não fazer

Não aceite soluções em que:

* o usuário consegue digitar números no campo Nome;
* o usuário consegue digitar letras no telefone;
* caracteres inválidos aparecem e só são rejeitados depois;
* `+55` permanece no telefone;
* código nacional `55` adicional permanece no telefone;
* DDD `55` válido é removido por engano;
* colar conteúdo ignora as validações;
* campos opcionais são deixados no formulário;
* formulário vazio consegue ser enviado;
* validação existe somente visualmente;
* validação depende apenas de HTML.

---

## Auditoria final obrigatória

Teste manualmente pelo menos:

**Nome**

`Eduardo Gonçalves` → aceitar

`Eduardo123` → impedir `123`

`123Eduardo` → impedir `123`

`Edu@rdo` → impedir `@`

`João da Silva` → aceitar

**Telefone**

`17999999999` → aceitar

`(17) 99999-9999` colado → aceitar e normalizar

`abc17999999999` → remover/impedir letras

`+55 17 99999-9999` → remover `+55`

`5517999999999` → remover código nacional e resultar em `17999999999`

Um telefone cujo DDD seja realmente `55` → **aceitar normalmente**

Telefone incompleto → impedir envio

**Formulário**

Teste submit com cada campo vazio individualmente.

Teste submit completamente vazio.

Teste digitação e colagem.

Teste também no desktop e no mobile.

Considere o formulário concluído somente depois que todos esses testes passarem.

## Replicar exatamente a integração de Meta Pixel + CAPI da Letícia Nunes

Sempre que houver necessidade de instalar ou corrigir **Meta Pixel + API de Conversões da Meta (CAPI)** em uma Landing Page, use obrigatoriamente como implementação de referência:

`/home/eduardo/www/2-Feitos/Letícia Nunes/Leticia - Imersão VIP`

Essa pasta é a **fonte da verdade da implementação**.

Antes de alterar o projeto atual, leia e analise completamente como o rastreamento foi implementado na Landing Page da Letícia Nunes.

Você deve identificar:

- arquivos envolvidos;
    
- scripts utilizados;
    
- implementação do Meta Pixel;
    
- implementação da API de Conversões;
    
- lógica de disparo;
    
- evento `Lead`;
    
- funcionamento do submit;
    
- comunicação entre front-end e CAPI;
    
- parâmetros enviados;
    
- identificação dos eventos;
    
- lógica de deduplicação, caso existente;
    
- tratamento dos dados;
    
- endpoints;
    
- variáveis utilizadas;
    
- estrutura dos requests;
    
- qualquer código relacionado ao rastreamento.
    

Depois disso, **replique a mesma arquitetura e o mesmo comportamento no projeto atual**.

---

# REGRA PRINCIPAL

**NÃO INVENTE UMA NOVA IMPLEMENTAÇÃO.**

Não pesquise outra forma de fazer.

Não substitua por outra biblioteca.

Não reorganize a arquitetura sem necessidade.

Não adicione novos eventos.

Não adicione Google Analytics.

Não adicione Google Tag Manager.

Não adicione scripts de rastreamento adicionais.

Não adicione ferramentas de terceiros.

Não "melhore" a implementação utilizando outra abordagem.

Não crie uma integração paralela.

A implementação da Letícia já funciona e deve ser utilizada como padrão.

**Copie o método existente e adapte somente o que for específico da Landing Page atual.**

---

# Meta Pixel

O Meta Pixel deve funcionar seguindo exatamente o padrão existente em:

`/home/eduardo/www/2-Feitos/Letícia Nunes/Leticia - Imersão VIP`

Mantenha:

- mesma estrutura;
    
- mesma forma de inicialização;
    
- mesma lógica de eventos;
    
- mesma lógica relacionada ao formulário;
    
- mesmo fluxo de rastreamento.
    

Naturalmente, dados específicos do projeto atual, como:

- Pixel ID;
    
- credenciais;
    
- tokens;
    
- informações específicas da cliente;
    

devem utilizar os valores correspondentes ao projeto atual quando estes estiverem disponíveis.

**Nunca reutilize por engano credenciais, Pixel ID ou tokens pessoais da Letícia em outra cliente.**

O que deve ser copiado é **a implementação**, não os identificadores particulares da cliente.

---

# API de Conversões da Meta — CAPI

A API de Conversões deve seguir **exatamente a mesma implementação utilizada na Letícia**.

Não crie uma nova arquitetura de CAPI.

Não altere:

- forma de envio;
    
- fluxo;
    
- estrutura;
    
- endpoint;
    
- lógica;
    
- tratamento;
    
- deduplicação;
    
- parâmetros;
    

a menos que seja estritamente necessário para adaptar os dados específicos da nova cliente.

Se existir no projeto da Letícia algum mecanismo compartilhado entre Pixel e CAPI, preserve-o exatamente.

Se houver `event_id`, deduplicação entre browser/server ou qualquer lógica equivalente, **copie a implementação existente em vez de recriá-la.**

---

# Evento Lead

O evento:

`Lead`

deve ser disparado **somente quando houver submit válido e efetivo do formulário**.

Ou seja:

Usuário preenche formulário corretamente  
↓  
Formulário é validado  
↓  
Submit realmente ocorre  
↓  
Evento `Lead` é disparado  
↓  
Pixel + CAPI processam o evento conforme implementação da Letícia

---

# PROIBIDO disparar Lead em página de obrigado

Não utilize:

- carregamento da página de obrigado;
    
- `PageView` da página de obrigado;
    
- acesso direto à URL;
    
- redirecionamento;
    
- abertura da página;
    

como gatilho para o evento `Lead`.

O usuário acessar uma página de obrigado **não significa automaticamente que houve um novo Lead**.

Isso evita leads falsos causados por:

- reload;
    
- acesso direto à URL;
    
- voltar/avançar no navegador;
    
- reabertura da página;
    
- cache;
    
- compartilhamento do endereço.
    

O `Lead` deve nascer do **submit do formulário**, conforme já implementado na Letícia.

---

# Pixel + CAPI

O rastreamento de Lead deve seguir o padrão da Letícia utilizando:

**Meta Pixel**  
+  
**Meta Conversions API**

O objetivo é manter rastreamento browser + server exatamente como já foi configurado no projeto de referência.

Não implemente apenas Pixel se a referência utiliza Pixel + CAPI.

Não implemente apenas CAPI.

Não substitua um pelo outro.

---

# Unificação do rastreamento

Faça também uma auditoria completa do projeto atual procurando qualquer outro sistema de tracking que possa duplicar ou interferir nos eventos.

Procure por:

- Google Tag Manager
    
- GTM
    
- Google Analytics
    
- GA
    
- GA4
    
- Meta Pixel duplicado
    
- Facebook Pixel duplicado
    
- PixelYourSite
    
- scripts antigos de tracking
    
- scripts de conversão
    
- plugins ou códigos antigos
    
- eventos `Lead` duplicados
    
- chamadas `fbq` duplicadas
    
- integrações anteriores
    
- snippets inseridos diretamente no HTML
    
- scripts carregados externamente
    

Se existirem rastreadores antigos ou conflitantes que não fazem parte da implementação padrão definida pela Letícia, remova-os.

O projeto deve ficar com **uma única implementação coerente de rastreamento**.

---

# Cuidado antes de remover

Antes de remover qualquer script, confirme que ele realmente pertence a um sistema de rastreamento concorrente ou duplicado.

Não remova:

- scripts funcionais da página;
    
- bibliotecas da interface;
    
- integrações do formulário;
    
- Make;
    
- CRM;
    
- WhatsApp;
    
- scripts necessários para funcionalidades da LP;
    

simplesmente porque possuem JavaScript.

A limpeza é especificamente relacionada a **tracking conflitante ou duplicado**.

---

# NÃO ALTERAR O RESTANTE DA LANDING PAGE

Esta tarefa é de rastreamento.

Portanto, não altere desnecessariamente:

- layout;
    
- responsividade;
    
- copy;
    
- cores;
    
- fontes;
    
- imagens;
    
- animações;
    
- formulário visual;
    
- CSS;
    
- estrutura das seções;
    
- redirecionamentos existentes;
    
- integrações de CRM/Make;
    

salvo quando uma alteração for estritamente necessária para conectar corretamente o evento ao submit.

---

# Processo obrigatório

Antes de começar:

### 1. Analise a referência

Leia:

`/home/eduardo/www/2-Feitos/Letícia Nunes/Leticia - Imersão VIP`

Identifique exatamente como Pixel + CAPI foram feitos.

### 2. Analise o projeto atual

Localize:

- formulário;
    
- submit;
    
- scripts existentes;
    
- Pixel existente;
    
- CAPI existente;
    
- GTM;
    
- Analytics;
    
- rastreadores conflitantes.
    

### 3. Compare os dois projetos

Determine o que precisa ser:

- mantido;
    
- removido;
    
- substituído;
    
- adaptado.
    

### 4. Replique a implementação

Copie o padrão técnico da Letícia.

### 5. Troque apenas dados específicos

Utilize os dados da cliente atual quando aplicável.

### 6. Remova rastreamento conflitante

Deixe somente a estrutura padronizada.

### 7. Teste

Confirme que tudo funciona antes de concluir.

---

# Auditoria obrigatória

Antes de considerar concluído, confirme:

-  Meta Pixel instalado conforme padrão da Letícia
    
-  CAPI instalada conforme padrão da Letícia
    
-  Pixel + CAPI funcionando em conjunto
    
-  Evento `Lead` ligado ao submit válido do formulário
    
-  `Lead` NÃO dispara simplesmente ao entrar em página de obrigado
    
-  Reload da página de obrigado NÃO cria novo Lead
    
-  Acesso direto à página de obrigado NÃO cria Lead
    
-  Não existem eventos `Lead` duplicados
    
-  Não existem Pixels duplicados
    
-  Não existe GTM interferindo
    
-  Não existe Analytics interferindo
    
-  Não existe PixelYourSite interferindo
    
-  Não existem scripts antigos de tracking interferindo
    
-  A implementação segue a arquitetura da Letícia
    
-  Nenhuma nova solução foi inventada
    
-  Credenciais da Letícia não foram reutilizadas em outra cliente
    
-  Formulário continua funcionando normalmente
    
-  Integrações existentes de Make/CRM continuam funcionando
    
-  Redirecionamento pós-submit continua funcionando, quando existente
    

---

# Regra final

Se existir dúvida sobre como implementar alguma parte:

**NÃO INVENTE.**

Volte para:

`/home/eduardo/www/2-Feitos/Letícia Nunes/Leticia - Imersão VIP`

e verifique como aquilo foi feito.

A implementação da Letícia é o padrão técnico deste projeto.

**Reproduza o que já funciona. Não crie uma alternativa.**

Ao finalizar, informe de maneira curta:

- quais arquivos foram alterados;
    
- qual tracking antigo foi removido, caso exista;
    
- confirmação de Pixel;
    
- confirmação de CAPI;
    
- confirmação do evento Lead no submit;
    
- confirmação de que não há Lead na página de obrigado;
    
- confirmação de que não foram adicionadas novas tecnologias de rastreamento.