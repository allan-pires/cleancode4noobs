# Capítulo 2: Nomes significantes
<img src="https://miro.medium.com/max/1236/1*rmH00qhA-aFVKxX2vEAGPA.jpeg" width="380">

Nomes estão em todos os lugares em um software. A gente dá nome pra variáveis, funções, argumentos, classes, pacotes, etc. E justamente por a gente dar nome a tudo, temos que fazer isso **bem feito**. Um bom nome pode salvar economizar um tempo precioso na leitura do código, por isso não seja se importe em demorar um pouco mais pensando num bom nome.

Tendo isso em mente, aqui algumas das dicas que o Clean Code dá para pensar em bons nomes:

## 1. O nome deve ser explicativo
O nome de uma variável, função, ou classe, deve responder algumas questões, como: Por que isso existe? O que isso faz? Como faz?
Se um nome precisa de um comentário para detalhes, então o nome não revela seu objetivo. Veja por exemplo essas duas variáveis que servem para o mesmo propósito:

```java
int d; //Tempo decorrido em dias

int elapsedTimeInDays;
```

O nome ```d``` não revela nada, não responde nenhuma pergunta. Enquanto isso, analisando o nome ```elapsedTimeInDays```, podemos notar que:

- Existe para manter um registro de tempo decorrido.

- A unidade de tempo utilizada é dias.

## 2. Nomes deves ser explícitos
Vou deixar outro exemplo do livro aqui, você consegue entender o que o seguinte código faz?

```java
public List<int[]> getThem() {
  List<int[]> list1 = new ArrayList<int[]>();
  
  for (int[] x : theList)
    if (x[0] == 4)
      list1.add(x);
    
  return list1;
}
```

Por mais que não hajam expressões difíceis, grandes problemas de identação ou inúmeras variáveis, é difícil entender o que o código faz. O problema não é que o código não seja simples, é que ele não é **explícito**. Não sabemos que tipo de coisas tem na variável theList, não sabemos qual a significância do número mágico 4 e também não sabemos como será usada a lista que vai ser retornada.
Agora imagine que esse código é de um jogo de campo minado, onde cada campo do array é um espaço no campo minado, e que o valor de status 4 significa que aquele espaço tem uma mina:

```java
public List<int[]> getFlaggedCells() {
  List<int[]> flaggedCells = new ArrayList<int[]>();
  
  for (int[] cell : gameBoard)
    if (cell[STATUS_VALUE] == FLAGGED)
      flaggedCells.add(cell);
  
  return flaggedCells;
}
```

Observe que a simplicidade do código não foi modificada, mas o código ficou muito mais explícito apenas usando nomes mais significantes.

## 3. Nomes devem ter significados distintos
Outra coisa que costuma acontecer com frequência é colocar duas variáveis com objetivos diferentes, mas com nomes quase iguais, uma pequena diferença apenas para fazer o programa rodar, como por exemplo os nomes ```var1``` e ```var2```. Isso faz com que os nomes sejam totalmente não informativos e sem nenhuma pista sobre suas diferenças. Se as variáveis tem significados diferentes, os seus nomes precisam ser distintos, como ‘source’ e ‘destination’.

## 4. Nomes devem ser fáceis de buscar
Use nomes fáceis de serem procurados no código. Se eu definir uma variável com nome ```e```, dá pra perceber teremos um certo trabalho pra procurá-la pelo código.

## 5. Nomes de uma classe devem ser substantivos
Classes e objetos devem ter um substantivo ou uma frase + substantivo como nome, como por exemplo ```Customer```, ```Client```, ```User``` ou ```AdressParser```.
## 6. Nomes de um método devem ser verbos
Métodos devem ter um verbo ou um verbo + frase como nome, como por exemplo ```save```, ```deletePage``` ou ```sendEmail```.

---

Ao longo do capítulo o autor dá várias outras dicas, mas preferi não me alongar muito e escolhi apenas os pontos que considerei mais importantes. Para um entendimento mais profundo e detalhado, não deixe de ler o livro!

[<< Capitulo anterior: Código Limpo](https://github.com/allan-pires/cleancode4noobs/blob/master/capitulo-3/funcoes.md)

[Próximo capítulo: Funções >>](https://github.com/allan-pires/cleancode4noobs/blob/master/capitulo-3/funcoes.md)
