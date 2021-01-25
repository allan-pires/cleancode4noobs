# Capítulo 5: Formatação
<img src="https://pbs.twimg.com/media/EsR-0o-U0AAZeju?format=jpg&name=900x900" width="380">

Imagine o seguinte cenário: Você acabou de ser contratado em uma empresa e está dando uma olhada nos repositórios e códigos. Você espera encontrar atenção aos detalhes, consistência, coisas que mostrem que profissionais e pessoas comprometidas trabalharam nesse projeto. No entando você encontra um amontoado de código completamente desordenado e sem padrão algum, que parece que foi escrito pela carreta furacão. Naturalmente sua primeira impressão é que a mesma falta de atenção a detalhes vai estar presente em todos os outros aspectos do projeto.

<img src="https://i.imgur.com/2MyLPgU.png" width="380">

## O Objetivo da Formatação
Só pra deixar bem claro: formatação de código é **muito importante**. É uma questão de comunicação, e comunicação é essencial para desenvolvedores.
A funcionalidade que você adicionou hoje no seu projeto tem uma boa chance de ser modificada na próxima release, mas a formatação e legibilidade do seu código vai continuar afetando manutenções e refatorações por anos. O estilo e  a disciplina do seu código continuam, mesmo que o seu código não exista mais.

## Formatação Vertical

Uma boa ideia é tentar manter arquivos com aproximadamente 200 linhas de código, e no máximo até 500 linhas. Arquivos curtos normalmente são mais fáceis de entender do que arquivos longos. 

Quase todos os códigos são lidos de cima pra baixo, sequencialmente, como um capítulo de um livro ou uma manchete de jornal. No topo temos conceitos e algoritmos de mais alto nível, e a medida que continuamos navegando no arquivo mais detalhes vão surgindo incrementalmente, até chegarmos no fim do arquivo, onde temos as funções e detalhes mais baixo nível. O nome do arquivo deve ser simples e claro, suficiente pra sabermos se estamos no módulo correto ou não.

Separe conceitos com linhas em branco:

👍👍👍
```java
package sample.package;

import java.util.regex.*;

public class Main {
	public static final String REGEXP = "'''.+? '''";
	
	static void myStaticMethod() {
    System.out.println("Static method");
  }

  public void myPublicMethod() {
    System.out.println("Public method");
  }

  public static void main(String[] args) {
    myStaticMethod();

    Main myObj = new Main();
    myObj.myPublicMethod();
  }
}
```

👎👎👎
```java
package sample.package;
import java.util.regex.*;
public class Main {
	public static final String REGEXP = "'''.+? '''";
	static void myStaticMethod() {
    System.out.println("Static method");}
  public void myPublicMethod() {
    System.out.println("Public method");}
  public static void main(String[] args) {
    myStaticMethod();
    Main myObj = new Main();
    myObj.myPublicMethod();}
}
```

---

_Ao longo do capítulo o autor dá várias outras dicas, mas preferi não me alongar muito e escolhi apenas os pontos que considerei mais importantes._

_Para um entendimento mais profundo e detalhado, não deixe de ler o livro!_

[>> Próximo capítulo: Objetos e Estruturas de Dados](https://github.com/allan-pires/cleancode4noobs/blob/master/capitulo-6/objetos-e-estruturas-de-dados.md)

[<< Capitulo anterior: Funções](https://github.com/allan-pires/cleancode4noobs/blob/master/capitulo-4/funcoes.md)
