<template>
  <v-container class="d-flex flex-column align-center justify-center">
    <v-card
      v-for="(item, index) in items"
      :key="index"
      class="d-flex flex-column pa-4 mb-4"
      style="max-width: 90%; background-color:#0b1d3a;"
    >
      <img
        :src="item.image"
        :alt="item.alt"
        class="img-fluid"
      />
      <v-expansion-panels style="width: 100%;">
        <v-expansion-panel :title="item.title" :text="item.text">
        </v-expansion-panel>
      </v-expansion-panels>
    </v-card>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    items: [
      {
        image: '/public/imagens/personagens_sad.png',
        alt: 'Personagem triste',
        title: 'Como tudo começou...',
        text: 'Um belo dia, Letícia estava em reunião com Luiz quando ele lhe fez uma certa pergunta — "Você está bem?" — e ficou surpreso com a velocidade da resposta; depois disso, Letícia, que vivia uma fase de luto pós-término, acabou indo ao hospital, onde conversou com Henrique, surgindo ali uma preocupação que antes não existia, pois ele, por já ter vivido algo semelhante, sentiu a necessidade genuína de ajudar — e foi assim que essa história começou: Henrique cuidou de Letícia no seu pior momento.'
    },
      {
        image: '/public/imagens/personagens_jantar.png',
        alt: 'Personagens no restaurante',
        title: 'Dia 02/05/2025...',
        text: 'Henrique queria tirar Letícia daquele poço de depressão e, aproveitando o aniversário do irmão, a convidou para ir ao rodízio com eles — detalhe: ela só estava comendo salada na época por conta das restrições a glúten e lactose; foi uma briga interna até aceitar, e no caminho ela só pensava em voltar para casa, até que chegou lá... e, olha, não foi nenhum bicho de sete cabeças — ele estava lá, todo lindo, esperando ela descer do carro, visivelmente nervoso e perdido até para encontrar a mesa; conversaram sobre muitas coisas, ela conheceu a famosa cunhada e a amou de cara, e no fim, Henrique conseguiu transformar algo que ela passou a semana inteira dizendo que não ia em uma experiência leve e nova.',
      },
       {
        image: '/public/imagens/personagens_filmes.png',
        alt: 'Personagens assistindo filmes',
        title: 'Simplesmente acontece...',
        text: 'Após o jantar, ele disse que o próximo lugar seria Letícia quem escolheria — e mal sabia ele que ela havia gostado dessa estratégia; então, ela o convidou para assistir seus dois filmes favoritos, sem esperar que ele realmente fosse aceitar, mas estava sentindo uma saudade que só seria aliviada ao vê-lo; pois bem, ele foi, e ela preparou salada de frutas e algumas besteirinhas para acompanharem o filme que tanto havia comentado — foi muito engraçado ver a reação dele a cada cena que ela já sabia de cor; além disso, Letícia passou a semana toda bem doente, e ele fez questão de levar remédio, chocolate (porque ela estava com cólica) e, o mais importante: levou uma bolinha rosa para Mel, sua filha de quatro patas — esse foi o dia em que ele fez cafuné nela pela primeira vez, e mal sabia ele que Melzinha e a mãe estavam completamente viciadas naquele carinho.',
      },
      {
        image: '/public/imagens/personagens_noite_estrelada.png',
        alt: 'Personagens na exposição de Van Gogh',
        title: 'Exposição de Van Gogh...',
        text: 'Letícia e Luiz tinham algo em comum: a mesma capinha de celular, e isso acabou levando-os até Van Gogh; Henrique precisou escolher o lugar para o próximo encontro e, ao ver o anúncio da exposição de Van Gogh no Shopping Barra, já soube o que fazer; antes de irem, ele a deixou na estação de ônibus para que se arrumasse em casa, soltando a frase “Letty, já estou com saudades!”, momento que ela imprimiu com um print, sem que ele imaginasse que isso já tinha feito o dia valer a pena; ela se arrumou em casa, colocando um lindo laço branco para combinar com a blusa de girassóis, enquanto ele, que havia comprado roupa especialmente para o evento (informação que ela desconhecia), estava lindo; foram juntos, ele não se perdeu no caminho — detalhe importante —, mas infelizmente chegaram atrasados e não puderam ver a tão sonhada “Noite Estrelada” (literalmente sonhada, pois Letty tinha sonhado que ali seria o local do primeiro beijo dos dois); fora isso, tudo foi lindo, Letty se apaixonou ainda mais por Van Gogh e ficou feliz com o momento.',
      },
    {
        image: '/public/imagens/personagens_gostar.png',
        alt: 'Personagens em um carro',
        title: 'Gostar...',
        text: 'Ela tinha uma aula no mesmo dia e precisava chegar em casa logo, mas não contava que ele havia desejado ao universo conversar com ela justamente naquele dia; ela não conseguia chamar nem um Uber, e foi exatamente na hora em que ele chegou à estação que pôde dar carona até sua casa; ele estava nervoso, mas com aquele jeito calmo de sempre, e disse que estava gostando dela, embora tivesse medo da reação dela — mal sabia ele que ela também gostava e só precisava de tempo para deixar esse sentimento fluir.',
      },
       {
        image: '/public/imagens/personagens_praia_ensaio.png',
        alt: 'Personagens na praia',
        title: 'A"mar"...',
        text: 'Um ponto importante sobre eles é que o mar é o lugar para onde correm tanto quando as coisas não vão bem quanto para comemorar — é o lugar deles no mundo; o mais engraçado é que, antes de começarem a conversar, um marujo (entidade da religião dela) disse que mandaria um homem formoso para ela, e, veja só que coincidência, uma semana depois eles começaram a conversar, comprovando que o marujo estava certo; no dia “dessa foto”, estavam na praia, conversando e olhando o mar, quando apareceu um casal fazendo um ensaio fotográfico de gravidez — tenho certeza que Henrique tirou um print daquela cena do mesmo jeito que Letty fez; foi também o primeiro dia em que ele a abraçou para esquentar e o dia em que tiraram a primeira foto juntos.',
      },
      {
        image: '/public/imagens/personagens_casa_henrique.png',
        alt: 'Personagem conhecendo a casa de Henrique',
        title: 'Casa de Henrique...',
        text: 'Essa foi a primeira vez que ela conheceu a casa de Henrique e viu, pela primeira vez, “Zuil” na foto da portaria; ah, e como não poderia esquecer os famosos Leon e Morgana — Leo, um gato grande que lembra muito o Garfield, e Morg, toda desconfiada, parecida com o gatinho de pelúcia que Letty tem; ela ficou de assistir a um filme na casa dele e amou o sofá; ao entrar, sentiu aquela sensação de lar, sabe? Sabia que viveria muitas coisas naquele lugar; assistiram ao filme, comeram e, finalmente, ela tomou coragem e deu seu primeiro beijinho nele!',
      },
      {
        image: '/public/imagens/personagens_beijo.png',
        alt: 'Primeiro beijo',
        title: 'Beijo...',
        text: 'Letty disse a Henrique: "Eu dei o primeiro passo, agora pode deixar de ser lerdo, que a bola tá com você", e foi assim que aconteceu o primeiro beijo deles; claro que o texto não mostra o tempo que Henrique passou pensando nas probabilidades de não dar certo, mas ele esqueceu que era Letty de quem estava falando — aconteceu de forma natural, leve e do jeitinho deles, com ele morrendo de medo dela não gostar e ela se perguntando como passou tanto tempo sem vivenciar aquilo; um lindo beijo com gostinho de cereja que nem Van Gogh conseguiu expressar no céu estrelado!',
      },
      {
        image: '/public/imagens/personagens_endoscopia.png',
        alt: 'Personagens no hospital',
        title: 'Endoscopia...',
        text: 'Esse dia foi pra mim um dos mais especiais da minha vida e com toda certeza não foi por causa do polipo. Voce fez a musica "ter o coração no chão" ter sentido e por algo que pra voce foi o "minimo". Henrique simplesmente pegou folga pra acompanhar Letícia na endoscopia e ficar rindo com ela achando que tinham colocado droga na veia. Derrubou um indtintor de incendio na garagem, mas isso deixamos como nosso segredinho. Acho que nunca fui tão amada como nesse dia e sempre tentarei recompensar isso.',
      },
       {
        image: '/public/imagens/personagens_carro.png',
        alt: 'Personagens em um carro',
        title: 'Flores no carro...',
        text: 'Letícia infelizmente encontrou o ex para resolver um problema com Mel e, ao entrar no carro, deu de cara com um lubrificante; ela contou isso para Henrique, que, sem dizer nada, comprou um pé de rosas cor de rosa para ressignificar o que havia acontecido no dia anterior com ela; ela se sentiu tão acolhida que nada mais importava, o lubrificante já nem estava mais na sua cabeça — acho que ressignificar nunca fez tanto sentido!',
      },
      {
        image: '/public/imagens/personagens_doente.png',
        alt: 'Personagem doente e outro personagem cuidando',
        title: 'Na doença e na doença...',
        text: 'Nesse mesmo dia, eles tinham combinado que ela dormiria na casa dele, mas infelizmente ela acabou ficando doente e teve uma noite péssima; ele percebeu que ela não estava bem, cuidou dela, levantou até para pegar remédio e nem sabia que estava ressignificando outra coisa naquele momento; pela manhã, ela acordou com um café da manhã lindo e fofinho — ah, Henrique atencioso...',
      },
       {
        image: '/public/imagens/personagens_sushi.png',
        alt: 'Personagens comendo sushi',
        title: 'Dia 02/06/2025...',
        text: 'Eles estavam comemorando o primeiro mês que ela aceitou sair com ele e que eles começaram a conversar. O combinado foi apresentar sushi para Henrique, ele nunca tinha comido e é um dos pratos preferidos dela. Foi tão engraçado ver ele comendo parecendo que estava comendo arroz com feijão, destruiu o sushi todinho no prato, mas valeu a pena cada minuto! Ele deu flores e uma minnie pra ela, e ela deu um marcador de páginas de que fez em croche (ele ama croche)... Ahhh e eles estão comendo de garfo na foto porque essa foi a realidade do jantar 😂. Em um mês eles viveram mais do que anos com outras pessoas!',
      },
      {
        image: '/public/imagens/personagens_stitch.png',
        alt: 'Personagens no shopping',
        title: 'Stitch...',
        text: 'Letícia precisava comprar o remédio que o psiquiatra passou, mas era tão caro que dividiu em três vezes (e, claro, ela reclamou como uma vovó pig); quando já estava para sair do shopping, Henrique olhou para uma loja de brinquedos e pegou o maior ursinho de pelúcia que encontrou, o Stitch! Letícia ficou sem acreditar que ele fez isso apesar do valor que ela nem imaginava quanto foi; foi o presente mais lindo que já recebeu, e agora leva o Stitch para cima e para baixo, dormindo agarradinha nele — era para ser só um antidepressivo, mas, se tratando de Henrique, claro que ele daria um jeito de ressignificar tudo aquilo!',
      },
      {
        image: '/public/imagens/personagens_cozinhar.png',
        alt: 'Personagens cozinhando',
        title: 'Macarrão...',
        text: 'Fizemos nossa primeira comida juntos, e foi a coisa mais natural possível; você, como sempre, fazendo piadas aleatórias em momentos sérios, e eu rindo feito uma bobinha de tudo; tudo ficou uma delícia, inclusive a salada de frutas que você tinha feito no dia anterior (mesmo com um pedaço do seu dedo junto)!',
      },
      {
        image: '/public/imagens/personagens_dormindo.png',
        alt: 'Personagens dormindo',
        title: 'Conchinha...',
        text: 'Não sei se você sabe, mas no antigo relacionamento de Letícia ela sempre era a conchinha maior, não gostava de grude e jamais dormia perto da outra pessoa; mas Henrique chegou e mudou até isso — algo que Letícia nem achava que precisava se tornou uma das melhores coisas da vida; sinto muitíssimo pelas suas noites de sono e por ter um sono tão leve, porque ela chegou para deixar tudo mais agitado e com a cor de Letty.',
      },
      {
        image: '/public/imagens/personagens_atravessar.png',
        alt: 'Personagens atravessando a rua de mãos dadas',
        title: '"Preciosidade"...',
        text: 'Letty já estava para viajar, e Henrique fez questão de que ela fosse ao Beco (melhor restaurante do mundo) antes disso acontecer; ao atravessar a rua, ela disse que dava tempo de passar, e ele respondeu na hora: "Você acha mesmo que vou deixar a minha coisinha mais preciosa do mundo correr perigo? Você precisa entender que eu te amo muito e não vou deixar você em perigo, nem que seja só para atravessar". Ahhh, Henrique atencioso...',
      },
      {
        image: '/public/imagens/personagens_distancia.png',
        alt: 'Distancia',
        title: 'Saudades...',
        text: 'Letícia ficou bastante tempo em um relacionamento focado no São João, então, sem pensar duas vezes, sentiu a necessidade de se afastar nessa época do ano para refletir sobre a vida e se recuperar do estrago causado; sentiu falta de Henrique a cada minuto, e tenho certeza que o sentimento foi recíproco; não foi fácil, mas foi necessário — eles tentaram aliviar a distância por meio de ligações, filmes no Discord e escrevendo cada detalhe no caderno deles.',
      },
       {
        image: '/public/imagens/personagens_barbeiro.png',
        alt: 'Personagens no carro',
        title: '3 vezes...',
        text: 'Ahhh bobinho, tu achou mesmo que eu não ia colocar isso aqui? Sei que não está na ordem certa, mas foi pra causar esse tom de surpresa mesmo; pois bem, o bonito deixou o carro morrer 3 vezes enquanto estava numa fila de carros, e é óbvio que Letty só sabia rir — não sabia se era por nervoso ou pela situação, mas nunca vai esquecer desse dia, e nem vem com aquele papo “o cara nunca deixa o carro morrer, mas deixa morrer 3 vezes no mesmo dia pra ver se não vira piada pro resto da vida!". VIRA SIM!',
      },
       {
        image: '/public/imagens/personagens_site.png',
        alt: 'Personagens olhando o site',
        title: 'Pedido...',
        text: 'Durante toda minha vida, sempre esperei uma atitude da outra pessoa em todos os passos do relacionamento, mas desta vez decidi fazer diferente... e você achando que é quem vai pedir no dia 02 de agosto — oh, dó! Este site foi criado para continuar o que Henrique fez para Letícia, sobre o About Us; aqui está um pedacinho da nossa história, o pedido para uma vida juntos e uma playlist que certamente ainda vai crescer; sei que você não está acostumado a viver tudo isso, mas "lo mereces"!',
      },
    ],
  }),
}
</script>

<style scoped>
.v-icon {
  color: white;
  font-size: 32px;
}

.dancing-image {
  animation: dance 0.9s infinite alternate ease-in-out;
  filter: drop-shadow(0 0 10px white);
}

@keyframes dance {
  0% {
    transform: rotate(-5deg) translateY(0);
  }
  50% {
    transform: rotate(5deg) translateY(-10px);
  }
  100% {
    transform: rotate(-5deg) translateY(0);
  }
}

.v-expansion-panel {
  background-color: #0b1d3a;
}

.img-fluid {
  max-width: 100%;
  height: auto;
}
</style>

