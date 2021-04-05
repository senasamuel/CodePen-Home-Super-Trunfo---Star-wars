<html>

<head>
    <title>
        Imersão Dev - Aula 08
    </title>
</head>

<body>
    <div class="container">
        <img src="https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/ca771e2d-d3f0-4d76-8bef-37b9e59a857f/d4v8493-fd471753-1025-47e1-823a-1e13334911bc.jpg?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOiIsImlzcyI6InVybjphcHA6Iiwib2JqIjpbW3sicGF0aCI6IlwvZlwvY2E3NzFlMmQtZDNmMC00ZDc2LThiZWYtMzdiOWU1OWE4NTdmXC9kNHY4NDkzLWZkNDcxNzUzLTEwMjUtNDdlMS04MjNhLTFlMTMzMzQ5MTFiYy5qcGcifV1dLCJhdWQiOlsidXJuOnNlcnZpY2U6ZmlsZS5kb3dubG9hZCJdfQ.wjG3pqkihak5JPbCDA45vb6O3cmS1XaEqNABC2ZIPbY" class="page-logo"
            alt="">
        <h1 class="page-title">Super Trunfo</h1>
        <button onclick="sortearCarta()" id="btnSortear">Sortear carta</button>
        <form id="form">
            <h2>Escolha o seu atributo</h2>
            <div class="wrapper">
                <div>
                    <div id="carta-jogador">
                        <img src="https://www.alura.com.br/assets/img/imersoes/dev-2021/card-super-trunfo-transparent-ajustado.png"
                            style=" width: inherit; height: inherit; position: absolute;">
                        <h3></h3>
                    </div>
                </div>
                <div>
                    <div id="carta-maquina" class="carta"><img
                            src="https://www.alura.com.br/assets/img/imersoes/dev-2021/card-super-trunfo-transparent-ajustado.png"
                            style=" width: inherit; height: inherit; position: absolute;"></div>
                </div>
            </div>
            <button class="button-jogar" type="button" id="btnJogar" onclick="jogar()" disabled="false">Jogar</button>
            <div id="resultado"></div>
        </form>
    </div>
</body>

</html>
body {
    font-family: 'Roboto Mono', monospace;
    min-height: 854px;
    background-image: url('https://www.alura.com.br/assets/img/imersoes/dev-2021/dia-07-super-trunfo-bg.png');
    background-color: #000000;
    background-size: cover;
    background-position: center top;
    background-repeat: no-repeat;
    padding-bottom: 20vh;
}

.container {
    text-align: center;
    padding: 20px;
}

.page-title {
    color: #ffffff;
    margin: 5px 0;
}

button, .button-jogar {
    padding: .8rem 1.5rem;
    margin: 1rem 0;
    border-radius: 5px;
    border: none;
    font-size: 1rem;
}

h2 {
    color: white;
}

#carta-jogador, #carta-maquina {
    width: 360px;
    height: 500px;
    overflow: auto;
    border-radius: 10px;
    margin-bottom: 20px;
    margin: 0 auto;
    display: flex;
    align-items: flex-end;
    position: relative;
    background-size: 350px 300px;
    background-repeat: no-repeat;
    background-position-x: 5px;
    background-position-y: 10px;
    border-radius: 33px;
}

#carta-jogador h3 {
    text-align: center;
}

.carta-imagem {
    border: 1px solid black;
    height: 100px;
    margin: 10px;
}

.carta-imagem img {
    width: 100%;
    height: 100%;
}

.carta-status {
    height: 160px;
    margin: 2rem;
    color: white;
    z-index: 2;
}

.carta-status input {
    margin: 20px 10px;
}

.resultado-final {
    color: white;
    font-size: 2rem;
    text-transform: uppercase;
    font-weigth: bolder;
    padding: 1rem;
    border: 2px solid black;
    background-color: black;
}

.--spacing {
    margin-left: 2.5rem;
}

form {
    display: flex;
    flex-direction: column;
}

.wrapper {
    display: flex;
    justify-content: space-between;
    width: 100%;
}

.carta-subtitle {
    z-index: 2;
    position: absolute;
    top: 16px;
    left: 37px;
    font-weight: 800;
    text-transform: uppercase;
}

#cartas {
    width: 100%;
    display: flex;
    justify-content: space-between;
}

.carta-status p {
    margin-bottom: 2rem;
}
var cartaYoda = {
    nome: "Mestre Yoda",                
      imagem:"https://static1.purebreak.com.br/articles/3/22/68/3/@/114420-nem-e-preciso-ser-o-mestre-yoda-de-sta-950x0-1.jpg",
     atributos: {
        ataque: 98,
        defesa: 80,
        magia: 90
    }
}

var cartaKenobi = {
    nome: "Obi Wan Kenobi",
      imagem:"data:image/jpeg;base64,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",                        
       atributos:{           
        ataque: 80,
        defesa: 75,
        magia: 75
       }
}

var cartaVader = {
    nome: "Lorde Darth Vader",
    imagem:"https://www.nerdsite.com.br/wp-content/uploads/2020/01/darth.jpg",
    atributos: {
        ataque: 98,
        defesa: 92,
        magia: 90
    }
}

var cartaDookan = {
    nome: "Conde Dookan",
    imagem:"https://pm1.narvii.com/6336/06fef0c261478ef68a26f572706fa0486d1d9048_hq.jpg",
    atributos: {
        ataque: 99,
        defesa: 90,
        magia: 97
    }
}

var cartaSkywalker = {
    nome: "Luke Skywalker",
    imagem:"",
    atributos: {
        ataque: 99,https:"https://i.pinimg.com/originals/70/62/f8/7062f8ace037f344cad1d568ea72cbbe.jpg",
        defesa: 90,
        magia: 97
    }
}

var cartaWindu = {
    nome: "Mace Windu",
    imagem:"https://observatoriodocinema.uol.com.br/wp-content/uploads/2019/01/Mace-Windu.jpg",
    atributos: {
        ataque: 79,
        defesa: 60,
        magia: 87
    }
}

var cartaTano = {
    nome: "Ahsoka Tano",
    imagem:"https://ovicio.com.br/wp-content/uploads/2020/11/20201127-rosario-dawson-ahsoka-tano-the-mandalorian-2.jpg",
    atributos: {
        ataque: 59,
        defesa: 60,
        magia: 47
    }
}

var cartaMaquina
var cartaJogador
var cartas = [cartaYoda, cartaKenobi, cartaVader , cartaDookan, cartaSkywalker, cartaWindu, cartaTano]
// 0          1           2

function sortearCarta() {
    var numeroCartaMaquina = parseInt(Math.random() * 5)
    cartaMaquina = cartas[numeroCartaMaquina]

    var numeroCartaJogador = parseInt(Math.random() * 5)
    while (numeroCartaJogador == numeroCartaMaquina) {
        numeroCartaJogador = parseInt(Math.random() * 5)
    }
    cartaJogador = cartas[numeroCartaJogador]
    console.log(cartaJogador)

    document.getElementById('btnSortear').disabled = true
    document.getElementById('btnJogar').disabled = false
    exibirCartaJogador()
    
}

function exibirCartaJogador(){
  var divCartaJogador = document.getElementById("carta-jogador")
  var moldura = '<img src="https://www.alura.com.br/assets/img/imersoes/dev-2021/card-super-trunfo-transparent.png" style=" width: inherit; height: inherit; position: absolute;">';
  divCartaJogador.style.backgroundImage=`url(${cartaJogador.imagem})`
  var nome = `<p class="carta-subtitle">${cartaJogador.nome}</p>`
  var opcoesTexto = ""
  for (var atributo in cartaJogador.atributos) {
        opcoesTexto += "<input type='radio' name='atributo' value='" + atributo + "'>" + atributo + " " + cartaJogador.atributos[atributo] + "<br>"
    }
    
  var html = "<div id='opcoes' class='carta-status'>"
  divCartaJogador.innerHTML = moldura+nome+html+opcoesTexto+'</div>'
}

function obtemAtributoSelecionado() {
    var radioAtributo = document.getElementsByName('atributo')
    for (var i = 0; i < radioAtributo.length; i++) {
        if (radioAtributo[i].checked) {
            return radioAtributo[i].value
        }
    }
}

function jogar() {
    var divResultado = document.getElementById("resultado")
    var atributoSelecionado = obtemAtributoSelecionado()

    if (cartaJogador.atributos[atributoSelecionado] > cartaMaquina.atributos[atributoSelecionado]) {
        htmlResultado = '<p class="resultado-final">Venceu</p>'
    } else if (cartaJogador.atributos[atributoSelecionado] < cartaMaquina.atributos[atributoSelecionado]) {
        htmlResultado = '<p class="resultado-final">Perdeu</p>'
    } else {
        htmlResultado = '<p class="resultado-final">Empatou</p>'
    }
  
 divResultado.innerHTML = htmlResultado
 exibeCartaMaquina() 
}

function exibeCartaMaquina(){
  var divCartaMaquina = document.getElementById("carta-maquina")
  var moldura = '<img src="https://www.alura.com.br/assets/img/imersoes/dev-2021/card-super-trunfo-transparent.png" style=" width: inherit; height: inherit; position: absolute;">';
  divCartaMaquina.style.backgroundImage=`url(${cartaMaquina.imagem})`
  var nome = `<p class="carta-subtitle">${cartaMaquina.nome}</p>`
  var opcoesTexto = ""
  for (var atributo in cartaMaquina.atributos) {
        opcoesTexto += "<p type='text' name='atributo' value='" + atributo + "'>" + atributo + " " + cartaMaquina.atributos[atributo] + "<br>"
  
    var html = "<div id='opcoes' class='carta-status'>"
    divCartaMaquina.style.backgroundImage=`url(${cartaMaquina.imagem})`
    divCartaMaquina.innerHTML = moldura+nome+html+opcoesTexto+'</div>'
    }
  }
