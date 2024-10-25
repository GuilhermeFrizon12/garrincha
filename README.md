# CRIAR UM NOVO BARALHO

.URL : [GET /api/deck/new/](https://deckofcardsapi.com/api/deck/new/)
.PARAMETRO : 'jokers_enabled' que adiciona curingas ao baralho( true ou false)
Exemplo de requisição para incluir curingas:
GET https://deckofcardsapi.com/api/deck/new/?jokers_enabled=true.
.DESCRIÇÃO : Cria um novo baralho padrão de 52 cartas.

# EMBARALHAR BARALHO

.URL : [GET /api/deck/new/shuffle/](https://deckofcardsapi.com/api/deck/new/shuffle/?deck_count=1)
.PARAMETROS : (COUNT) Números de cartas a desenhar.
.DESCRIÇÃO : Embaralha um novo baralho; Para definir multiplos baralhos, inclua 'deck_count'.

# CRIAR PILHAS E ADICIONAR CARTAS

.URL : [GET /api/deck/{deck_id}/pile/{pile_name}/add/?cards={cards}](https://deckofcardsapi.com/api/deck/<<deck_id>>/pile/<<pile_name>>/add/?cards=AS,2S)
.PARAMETROS : 'pile_name' que significa o nome da pilha; 'cards' que significa Lista de cartas para adicionar à pilha (ex: AS,10D)
.DESCRIÇÃO : Adiciona cartas a uma pilha específica dentro de um baralho.

# REMOVER E LISTAR CARTAS DE UMA PILHA

.URL : GET /api/deck/{deck_id}/pile/{pile_name}/list/
.PARAMETRO : 'cards' que significa cartas a remover, separadas por vírgula, ex: (AS,10D).
.DESCRIÇÃO: Lista cartas atualmente em uma pilha. 

# COMPRAR UMA CARTA

.METODO : GET
.URL [:/api/deck/{deck_id}/draw/](https://deckofcardsapi.com/api/deck/<<deck_id>>/draw/?count=2)
.PARAMETROS : 'deck_id' é necessário para saber o ID do baralho criado anteriormente; O 'count' é opcional que mostra o Número de cartas a comprar (padrão: 1).

# UM BARALHO PARCIAL

.METODO : GET
.URL :/api/deck/new/shuffle/
.PARAMETROS : 'cards' Lista de cartas a incluir, separadas por vírgula (ex: AS,10D).
EX: [GET https://deckofcardsapi.com/api/deck/new/shuffle/?cards=AS,10D.](https://deckofcardsapi.com/api/deck/new/shuffle/?cards=AS,2S,KS,AD,2D,KD,AC,2C,KC,AH,2H,KH)

# LISTAR CARTAS DE UMA PILHA

.METODO : GET
.URL : https://deckofcardsapi.com/api/deck/<<deck_id>>/pile/<<pile_name>>/list/
EX : GET https://deckofcardsapi.com/api/deck/{deck_id}/pile/{pile_name}/list/
Observação : isso não funcionará com vários decks.

# DESENHO DE PILHAS

.METODO : GET 
.URL : https://deckofcardsapi.com/api/deck/<<deck_id>>/pile/<<pile_name>>/draw/?cards=AS (Especifique as cartas que você quer tirar da pilha. O padrão é apenas tirar do topo da pilha (é uma pilha ). Adicione /bottom/ à URL para tirar do fundo ou /random/ para tirar cartas aleatórias - ambos também aceitam o parâmetro count .)
.PARAMETROS : 'cards'

# RETORNANDO AS CARTAS AO BARALHO 

.METODO : POST
.URL : https://deckofcardsapi.com/api/deck/<<deck_id>>/return/
(se esta chamada para retornar cartas que foram compradas ou cartas de uma pilha de volta ao baralho principal para reutilização. Ambas as versões podem receber o parâmetro cards para uma lista de cartas a serem retornadas (se válidas).)
.PARAMETROS : ' request body'  Um JSON contendo as cartas a serem retornadas. 
EX : POST https://deckofcardsapi.com/api/deck/{deck_id}/pile/{pile_name}/add/
Content-Type: application/json

{
    "cards": ["AS", "10D"]
} 

# IMAGEM DO VERSO DO CARTÃO

.URL : https://deckofcardsapi.com/static/img/back.png









