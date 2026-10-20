# Infoweb 2026 — chat de publicações (protótipo)

## Arquivos
- `index.html`: início com carrossel de avisos e cartões de próximas datas.
- `turma.html`: diretório de alunos.
- `diario.html`: publicações do diário.
- `estudos.html`: materiais dos professores e extras.
- `calendario.html`: calendário mensal e próximas datas.
- `admin.html`: chat de publicação em modo de teste sem login.

## Testar
Extraia o ZIP e abra `index.html`. Para publicar conteúdo de teste, abra `admin.html`, escolha o destino, escreva uma mensagem, anexe arquivos pequenos se quiser e clique na seta de envio. Depois visite a página correspondente.

## Botões + por página
- O botão `+` de alunos, diário, estudos, avisos e datas aparece quando o modo de teste admin está ativo.
- Abrir `admin.html` ativa o modo admin de teste neste navegador; ao voltar às páginas, os botões `+` aparecem.
- Em páginas públicas há um aviso “Só adms podem falar”, sem caixa de digitação/anexos para visitantes.

## Limitações IMPORTANTES
- **Modo admin sem login NÃO É SEGURO para publicar na internet.** Qualquer visitante pode abrir `admin.html`, ativar o modo admin de teste e publicar/apagar conteúdo no próprio navegador.
- Os posts são salvos no `localStorage`: só aparecem no mesmo navegador e dispositivo; não sincronizam entre alunos.
- Os anexos são limitados a cerca de 800 KB cada para reduzir problemas no navegador.
- O botão de áudio permite selecionar/gravar um áudio se o navegador/dispositivo oferecer essa opção; não é um gravador universal.
- A navegação pública é apenas de leitura. O único composer de publicação está em `admin.html`.
- A versão final precisa de Supabase Auth, tabela de administradores, Row Level Security e Supabase Storage. A regra “somente administradores podem publicar” deve ser validada pelo backend. O limite de 3 admins também deve ser imposto no backend.
- O APK não está incluído; será uma etapa posterior.

## Netlify
O site pode ser hospedado como arquivos estáticos, mas **não publique a versão de teste sem login** se não quiser que qualquer pessoa acesse a área administrativa. Antes de disponibilizar publicamente, proteja a área admin com autenticação real.

## Correções desta versão
- `turma.html` agora carrega `app.js`, então o botão ＋ de adicionar aluno aparece no modo admin.
- Setas ‹ › das datas funcionam (páginas de 3 em 3) e dias com data importante ganham um pontinho no calendário.
- Admin: campo de categoria (aula/evento/projeto) e data do registro para o diário; os filtros agora funcionam e o diário é ordenado pela data.
- Mês das datas do diário agora mostra o nome (ex.: OUT) em vez do número.

## Popup de publicação (novo)
- Os botões ＋ de cada página agora abrem um popup na própria página (aluno, diário, estudos, aviso, data), sem ir para `admin.html`.
- Ao clicar em **Publicar**, o conteúdo é salvo e a página atualiza na hora, sem recarregar. Fechar no ✕, clicando fora ou com Esc cancela.
- Em Estudos, o popup publica na aba que estiver selecionada (Professores ou Extras).
- `admin.html` continua existindo para gerenciar/excluir publicações.

## Foto, descrição e áudio (novo)
- Alunos: o popup agora pede descrição (até 200 caracteres) e foto (recortada em quadrado e reduzida automaticamente).
- Gravação de áudio estilo WhatsApp no popup (🎤): toque para gravar, toque de novo para parar, ouça antes de publicar e remova no ✕. Limite de 2 min. Nas páginas, os áudios aparecem com player.
- O gravador precisa de permissão do microfone e funciona em `localhost`/HTTPS (ou abrindo o arquivo direto no Chrome).

## Perfil próprio, ordem alfabética e ajuste de foto (novo)
- Na aba Turma, qualquer visitante vê **＋ Criar meu perfil** (nome, apelido, descrição e foto). O aluno entra na lista na hora.
- A lista de alunos agora é sempre ordenada por ordem alfabética (ignora maiúsculas e acentos).
- Foto: depois de escolher a imagem dá para dar zoom (barra) e arrastar para enquadrar antes de publicar.
- Atenção: sem backend, o perfil só aparece no navegador de quem criou. A sincronização entre alunos virá com o Supabase.
