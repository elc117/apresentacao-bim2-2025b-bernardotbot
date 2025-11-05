# Apresentação sobre o material do libDGX 

## Introdução
O material apresenta dois exemplos de jogos criados com o libDGX. Os dois têm o objetivo de usar um balde para capturar gotas de água que caem ao longo do tempo.

<img width="1322" height="858" alt="image" src="https://github.com/user-attachments/assets/1b77a313-4982-4b0f-a939-bc10b66d3db1" />
<img width="1015" height="816" alt="image" src="https://github.com/user-attachments/assets/e6bf796d-92b3-4975-bb4b-ec98c6b3eadf" />

## Identificação de herança e polimorfismo
O jogo possui três classes: Drop, MainMenuScreen e GameScreen.
Olhando para o início de cada uma das classes, temos:
<pre> public class Drop extends Game {  </pre>
<pre> public class MainMenuScreen implements Screen {  </pre>
<pre> public class GameScreen implements Screen {  </pre>

As palavras `extends` e `implements` identificam casos de herança.
Além disso, polimorfismo também está presente em métodos como:
`public void render()`, `public void dispose()` e `public void create()`

## Identificação de construtores, objetos e chamadas de métodos
Existem dois exemplos de construtores, um na classe GameScreen e outro na classe MainMenuScreen.
Na classe MainMenuScreen:
<pre>
  	public MainMenuScreen(final Drop passed_game) {
		game = passed_game;
		
		camera = new OrthographicCamera();
		camera.setToOrtho(false, WIDTH, HEIGHT);
	}
  </pre>

  Na classe GameScreen:
  <pre>
	  public GameScreen(final Drop passed_game) {
		game = passed_game; 
		
		// Load images, 64px each
		dropImage = new Texture(Gdx.files.internal("droplet.png"));
		bucketImage = new Texture(Gdx.files.internal("bucket.png"));

    	// resto do código

    	raindrops = new Array<Rectangle>();
			spawnRaindrop();
	}
  </pre>

Note que os dois exemplos possuem criação de objetos (identificados pela palavra `new`), como em `new Texture()` e `new OrthographicCamera()`.

## Criação de gotas aleatórias e colisão com o balde

No fim do último exemplo do tópico anterior, repare que tem uma chamada para outro método, `spawnRaindrop()`, responsável por criar uma nova gota de água e escolher uma posição aleatória no eixo x para ela aparecer na tela.
A escolha da posição aleatória é feita em `raindrop.x = MathUtils.random(0, 800-64);`.
Esse trecho escolhe uma posição entre 0 e 764 para a posição horizontal da gota.

Já para detectar a colisão com o balde, é usado o método `overlaps()`, disponibilizado pelo libGDX.
Mais especificamente, ele é usado no seguinte trecho:
  <pre>
			if (raindrop.overlaps(bucket)) {
				dropsGathered++;
				dropSound.play();
				iter.remove();
			}
  </pre>

  ## Impressões pessoais
  De maneira geral, identificar construtores, objetos e os outros conceitos pedidos foi a parte mais fácil do trabalho.
  
  Por outro lado, tive dificuldade para entender como as classes se relacionam entre si e o que cada método faz, além de não conseguir fazer outros exercícios do material. 
  Na seção "Prática no Codespaces", por exemplo, um dos exercícios pede para adicionar um contador de gotas na tela do jogo. Não consegui identificar como poderia fazer para adicionar o contador (em que parte do código e como fazer). Adicionar o contador no terminal também não funcionou, mas eu não sei o motivo.
  
  Outro exercício pedia para alterar a velocidade das gotas depois que algumas fossem coletadas. Consegui fazer, embora com mais dificuldade e de maneira mais lenta, após alguns testes e erros.


  ## Referências

  OPENAI. ChatGPT. Disponível em: https://chat.openai.com. Acesso em: 5. nov. 2025.
  Charão, Andrea. Programação Orientada a Objetos com libGDX. Universidade Federal de Santa Maria. Disponível em: https://liascript.github.io/course/https://raw.githubusercontent.com/AndreaInfUFSM/elc117-2025b/main/classes/24a/README.md#1. Acesso em: 5. nov. 2025.
  


  
