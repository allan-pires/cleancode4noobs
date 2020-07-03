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

**Comentários informativos**

Comentários com informações básicas as vezes são úteis, como por exemplo formatos de expressões regulares.
```java
// Compara o seguinte formato kk:mm:ss EEE, MMM dd, yyyy
Pattern timeMatcher = Pattern.compile("\\d*:\\d*:\\d* \\w*, \\w* \\d*, \\d*");
```

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

**Gambiarras**
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

O que o comentário acima significa? Claramente significava algo pra o desenvolvedor, mas o motivo não é aparente.

**Comentários redundantes**
```java
// Calcula a pontuação total
public String calculateTotalScore() {

```

```java
/* O dia do mês. */
 private int dayOfMonth;
```

**Comentários enganosos**
```java
/** O nome. */
private String name;

/** A versão. */
private String version;

/** O nome da licença. */
private String licenceName;

/** A versão. */
private String info;
```
Leia atentamente os comentários mais uma vez.

Percebeu algo errado?

**Comentários obrigatórios**
```java
/**
 *
 * @param title Título do CD
 * @param author Autor do CD
 * @param tracks Número de faixas do CD
 * @param durationInMinutes Duração do CD em minutos
 */
public void addCD(String title, String author, int tracks, int durationInMinutes) {
  CD cd = new CD();
  cd.title = title;
  cd.author = author;
  cd.tracks = tracks;
  cd.duration = duration;
  cdList.add(cd);
}
```
<div align="center">
  <i>Robert C. Martin, 2009, p. 63. - Tradução livre</i>
</div>
<br>

Ter uma regra que obriga todos os métodos a terem javadoc ou todas as variáveis a terem comentários é ridículo e só serve para criar um aglomerado de informações desnecessárias que podem potencialmente criar confusão.

**Comentários de adição**
```java
/* Added by Steve */
```

**Código comentado**
```java
InputStreamResponse response = new InputStreamResponse();
response.setBody(formatter.getResultStream(), formatter.getByteCount());
// InputStream resultsStream = formatter.getResultStream();
// StreamReader reader = new StreamReader(resultsStream);
// response.setContent(reader.read(formatter.getByteCount()));
```
Poucas práticas são tão horrendas quanto código comentado, Não faça isso!

Muitas pessoas quando veem código comentado tem medo de deletar porque acham que ele deve estar lá por algum motivo importante. Se o código está num repositório git, isso vai ficar registrado no histórico e não precisa existir no código.

**Muita informação**
```java
/*
 RFC 2045 - Multipurpose Internet Mail Extensions (MIME)
 Part One: Format of Internet Message Bodies
 section 6.8. Base64 Content-Transfer-Encoding
 The encoding process represents 24-bit groups of input bits as output
 strings of 4 encoded characters. Proceeding from left to right, a
 24-bit input group is formed by concatenating 3 8-bit input groups.
 These 24 bits are then treated as 4 concatenated 6-bit groups, each
 of which is translated into a single digit in the base64 alphabet.
 When encoding a bit stream via the base64 encoding, the bit stream
 must be presumed to be ordered with the most-significant-bit first.
 That is, the first bit in the stream will be the high-order bit in
 the first 8-bit byte, and the eighth bit will be the low-order bit in
 the first 8-bit byte, and so on.
 */
```

**Javadocs em código não-público**
Javadocs pode ser muito útil para APIs públicas, mas não é nem um pouco necessário para código interno.

---

_Ao longo do capítulo o autor dá várias outras dicas, mas preferi não me alongar muito e escolhi apenas os pontos que considerei mais importantes._

_Para um entendimento mais profundo e detalhado, não deixe de ler o livro!_

[>> Próximo capítulo: Formatação](https://github.com/allan-pires/cleancode4noobs/blob/master/capitulo-5/formatacao.md)

[<< Capitulo anterior: Funções](https://github.com/allan-pires/cleancode4noobs/blob/master/capitulo-3/funcoes.md)
