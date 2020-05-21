# Capítulo 3: Funções

<img src="https://miro.medium.com/max/267/1*JPRwyIpOwyYrcAOdvPkxyA.png" width="380">

Quem nunca passou mais tempo do que deveria tentando entender uma função que (teoricamente) deveria ser simples de se entender? As vezes você precisa ter sido o próprio autor daquele pedaço de código para conseguir entendê-lo, e tem casos em que até ele mesmo tem dificuldade de entender.

Para que isso se torne menos recorrente, aqui vão algumas das dicas que o Clean Code dá sobre como lidar com funções:

## 1. Funções pequenas!
Primeiro: funções devem ser pequenas.

Segundo: funções devem ser **ainda menores** que isso.

Não existe nada que realmente dite que uma função pequena é melhor que uma função grande, mas venhamos e convenhamos que é muito mais fácil de entender uma função de 5 linhas do que uma com 500 linhas.

## 2. Estruturas condicionais
Seguindo a dica passada, blocos dentro de estruturas condicionais como if, else ou while devem ter apenas uma linha, e essa linha provavelmente deve ser uma chamada de função.

```java
//exemplo-4.java

public static String renderPageWithSetupsAndTeardowns(PageData pageData, boolean isSuite) throws Exception {
  if (isTestPage(pageData)){
    includeSetupAndTeardownPages(pageData, isSuite);
  }
  return pageData.getHtml();
}
```

Isso faz com que a leitura do código fique muito mais fácil e rápida.

## 3. Responsabilidade única
Funções devem fazer somente UMA coisa, e devem fazê-la bem.

<img src="https://66.media.tumblr.com/bd51c0328b590e10c10010cfab72b3f8/tumblr_inline_pjzs8aTkN91sqnfvc_400.gifv" width="380">

```java
//exemplo-5.java

  if (includeSuiteSetup) {
    WikiPage suiteTeardown = 
      PageCrawlerImpl. getInheritedPage(
                             SuiteResponder.SUITE_TEARDOWN_NAME,
                             wikiPage
      );
    if (suiteTeardown != null) {
     WikiPagePath pagePath =
         suiteTeardown.getPageCrawler().getFullPath (suiteTeardown);
    
     String pagePathName = PathParser.render(pagePath);
     buffer.append("!include -teardown .")
           .append(pagePathName)
           .append("\n");
     }
    }
  }
  pageData.setContent(buffer.toString());
  return pageData.getHtml();
}
```

Nesse exemplo acima podemos claramente ver que esse código faz bem mais que uma coisa e possui diferentes níveis de abstração. Cria buffers, busca páginas, renderiza caminhos, gera HTML, além de outras coisas.

Ué, mas no [exemplo 4](https://github.com/allan-pires/cleancode4noobs/new/master#2-estruturas-condicionais) o código também parece fazer mais de uma coisa:
- Determina se a página é de teste ou não
- Se for de teste, inclui mais duas páginas
- Renderiza a página em HTML

Bom, note que no exemplo passado o código se manteve o máximo de um level de abstração abaixo do nome da função (```RenderPageWithSetupsAndTeardowns```).

Se todos os passos de uma função estão em até um nível de abstração menor que o nome da função, podemos dizer que essa função faz somente uma coisa. Afinal, o motivo de criamos funções é justamente decompor uma tarefa maior numa série de passos, cada uma com uma abstração diferente.

## 4. Um level de abstração por função
No [exemplo 5](https://github.com/allan-pires/cleancode4noobs/new/master#3-responsabilidade-%C3%BAnica) pode-se notar que há abstrações de alto nível:

>.getHtml()

Bem como abstrações de baixo nível:

>.append(“\n”)

Misturar diferentes leveis de abstração em uma função é sempre confuso, procure sempre manter apenas um level de abstração por função.

## 5. Código deve ser lido de cima para baixo
Imagine seu código como um livro. Imagino que você não leia um livro alternando entre parágrafos de cima para baixo e de baixo para cima.
Cada função deve ser seguida por outra função com o próximo nível de abstração, de forma que a abstração seja decrescente. Assim quando lermos a lista de funções, em cada função a abstração vai caindo um nível por vez.

## 6. Poucos argumentos
O número ideal de argumentos para uma função é zero. Logo depois vem funções com um argumento, seguido de perto por funções com dois argumentos. Funções com três argumentos devem ser evitadas ao máximo e funções com mais argumentos ainda precisam de uma justificativa **muito especial** — e ainda não devem ser usadas mesmo assim.

Muitos argumentos dificultam o entendimento de uma função, fora que é bastante comum esquecermos da ordem dos argumentos.

Funções com muitos argumentos também aumentam muito a complexidade dos testes. Imagine criar todos os casos de testes para garantir que a combinação de vários diferentes argumentos funcionem corretamente.

## 7. Tratamento de Exceções
Tratar exceções conta como uma coisa, e funções devem fazer apenas uma coisa. Então uma funcionalidade que trata exceções deve fazer somente isso.

```java
//exemplo-6.java

public void delete(Page page) {
  try {
    deletePageAndAllReferences(page);
  }
  catch (Exception e) {
    logError(e);
  }
}

private void deletePageAndAllReferences(Page page) throws Exception {
  deletePage(page);
  registry.deleteReference(page.name);
  configKeys.deleteKey(page.name.makeKey());
}

private void logError(Exception e) {
  logger.log(e.getMessage());
}
```

## 8. DRY (Don’t Repeat Yourself)
Não repita a si mesmo. Trechos repetidos tornam o código mais obscuro e obsoleto, aumentam a complexidade e dificultam a manutenção.

---


_Ao longo do capítulo o autor dá várias outras dicas, mas preferi não me alongar muito e escolhi apenas os pontos que considerei mais importantes._

_Para um entendimento mais profundo e detalhado, não deixe de ler o livro!_

[>> Próximo capítulo: Comentários](https://github.com/allan-pires/cleancode4noobs/blob/master/capitulo-4/comentarios.md)

[<< Capitulo anterior: Nomes significantes](https://github.com/allan-pires/cleancode4noobs/blob/master/capitulo-2/nomes-significantes.md)
