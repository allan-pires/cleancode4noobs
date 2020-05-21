# Capítulo 4: Comentários
<img src="https://i.imgur.com/d9rgvMT.png">

Segundo o autor, comentários são fracassos. O uso de comentários é para compensar nosso fracasso em nos expressar no código.

Se a necessidade de escrever um comentário vier, pare e reflita um momento se não há uma forma de se expressar somente pelo código.

## Qual o problema de comentários?
<img src="https://i.imgur.com/ioIHtPe.png">

Comentários mentem. Não sempre, não intencionalmente, mas frequentemente. 

Comentários costumam ficar velhos e desatualizados porque são esquecidos enquanto o código evolui rapidamente.

É possível chegar a um ponto em que desenvolvedores são suficientemente disciplinados para manter os comentários atualizados, relevantes e corretos, mas é preferível que esse esforço seja direcionado em manter o código claro e expressivo de forma que sequer precise de comentários.

## Por que escrevemos comentários?
<img src="https://i.imgur.com/V4Y1ezm.png" width="320">

Uma das maiores motivações da escrita de comentários é código ruim. 

Se o código está desorganizado e confuso, ao invés de criar comentários e tentar explicar o que está acontecendo, use essa energia para limpá-lo.

Observe os seguintes exemplos, você prefere isso:
```java
// Checa se o personagem pode usar a magia Fire Ball
if ((hero.alive & STATUS_OK) && (hero.mana > 650))
```
Ou isso?

```java
if (hero.canUseFireBall())
```
Em muitos casos basta criar uma função que faz exatamente o que o comentário descreve.

## Comentários Bons
Alguns comentários são necessários ou benéficos, como por exemplo:

**Comentários de licenças**

As vezes os padrões corporativos nos obrigam a escrever certos códigos por razões legais, como _copyright_.
```java
// Copyright (C) 2003,2004,2005 by Object Mentor, Inc. All rights reserved.
// Released under the terms of the GNU General Public License version 2 or later.
```
<div align="center">
  <i>Robert C. Martin, 2009, p. 55.</i>
</div>
<br>

**Comentários informativos**

Comentários com informações básicas as vezes são úteis, como por exemplo formatos de expressões regulares.
```java
// Compara o seguinte formato kk:mm:ss EEE, MMM dd, yyyy
Pattern timeMatcher = Pattern.compile("\\d*:\\d*:\\d* \\w*, \\w* \\d*, \\d*");
```
<div align="center">
  <i>Robert C. Martin, 2009, p. 56. - Tradução livre</i>
</div>
<br>

**Comentários de aviso**

As vezes é útil avisar aos demais desenvolvedores sobre certas consequencias.
```java
public static SimpleDateFormat makeStandardHttpDateFormat() {
  // SimpleDateFormat não é thread-safe,
  // então precisamos criar cada instancia independentemente
  SimpleDateFormat df = new SimpleDateFormat("EEE, dd MMM yyyy HH:mm:ss z");
  df.setTimeZone(TimeZone.getTimeZone("GMT"));
  
  return df;
}
```
<div align="center">
  <i>Robert C. Martin, 2009, p. 58. - Tradução livre</i>
</div>
<br>

## Comentários Ruins
A maioria dos códigos se enquadra nessa categoria, normalmente são apenas desculpas para código e decisões ruins.

**Resmungado**
```java
public void loadProperties() {
  try {
    String propertiesPath = propertiesLocation + "/" + PROPERTIES_FILE;
    FileInputStream propertiesStream = new FileInputStream(propertiesPath);
    loadedProperties.load(propertiesStream);
  }
  catch(IOException e) {
    // Nenhum arquivo de propriedade significa que todos os valores padrões foram carregados
  }
}
```
<div align="center">
  <i>Robert C. Martin, 2009, p. 60. - Tradução livre</i>
</div>
<br>

O que o comentário acima significa? Claramente 

---

_Ao longo do capítulo o autor dá várias outras dicas, mas preferi não me alongar muito e escolhi apenas os pontos que considerei mais importantes._

_Para um entendimento mais profundo e detalhado, não deixe de ler o livro!_

[>> Próximo capítulo: Formatação](https://github.com/allan-pires/cleancode4noobs/blob/master/capitulo-5/formatacao.md)

[<< Capitulo anterior: Funções](https://github.com/allan-pires/cleancode4noobs/blob/master/capitulo-3/funcoes.md)
