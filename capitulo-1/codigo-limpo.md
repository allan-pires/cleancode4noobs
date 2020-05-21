# Capítulo 1: Código Limpo
<img src="https://res.cloudinary.com/wlion/f_auto,q_auto,c_fill/wlion/2017/04/CleanCode.jpg" width="380">

O capítulo começa com uma frase bem bacana que é:
> "Você está lendo esse livro por duas razões. Primeiro, você é um programador. Segundo, você quer ser um programador melhor. Ótimo. Precisamos de programadores melhores."

A principal proposta do Clean Code é ajudar o leitor a escrever um bom código. Perceber as diferenças entre um código ruim e um código bom, bem como transformar um código ruim em um código bom.

## Mas se o meu código 'ruim' tá funcionando, por que eu vou querer me dar ao trabalho de refatorar tudo pra deixar ele 'bom'?
Porque o custo total de manter um código ruim é **enorme**.

Quem trabalha ou trabalhou como programador por algum tempo já deve ter passado pela experiência de ter uma produtividade ruim por causa de código ruim. Algo que deveria ter levado horas para ser feito, acabou levando semanas. Uma mudança que bastava ser de uma linha, mas precisou ser feita também em centenas de outros módulos. Todos esses sintomas são bem comuns, adicionar uma funcionalidade simples acaba se tornando uma tarefa extremamente complexa.

![](https://miro.medium.com/max/1060/1*Yvtd3gFEZlfWryv63CsTtA.png)

## Por que isso acontece? Por que um código bom rapidamente apodrece em um código ruim?

A gente sempre tem alguma desculpa pra dar: o prazo de entrega era muito curto; os requisitos mudaram no meio do projeto; o gerente de produtos pediu coisas absurdas, entre outras. Mas a culpa na verdade é nossa. Nós como desenvolvedores devemos ser profissionais a ponto de defender a importância de escrever um código limpo, mesmo que demore mais pra ser feito.

Tem um exemplo muito bom no livro que diz o seguinte:
> "E se você fosse um médico e tivesse um paciente que pediu que você parasse com toda essa besteira de lavar as mãos antes de uma cirurgia pois estava demorando demais? 

> Claramente o paciente é o chefe, mas o médico claramente deve negar o pedido do paciente. Por quê? Porque o médico sabe mais do que o paciente sobre os riscos de doenças e infecções. 
> Seria uma atitude não profissional (sem falar criminal) se o médico aceitasse o pedido."

Seguindo a analogia, também não é profissional que um desenvolvedor se curve a todos os desejos de um gerente, que não entende os riscos de um código ruim. Os gerentes vão defender o prazo de entrega com unhas e dentes, mas isso faz parte do trabalho deles! Nosso trabalho é defender um código limpo com a mesma intensidade.


## Mas afinal, o que seria um código limpo?
O livro também mostra como programadores experientes interpretam o que seria um código limpo. Entre eles, o autor do livro (Uncle Bob), descreve que para ele um código limpo é um código que não precisa ser explicado. Um código que qualquer programador possa bater o olho e saber exatamente o que ele faz.
> "Qualquer tolo pode escrever um código que um computador consiga entender. Bons programadores escrevem código que humanos consigam entender." - Martin Fowler

Mas também não basta saber escrever um código limpo. É preciso **manter** o código limpo com o passar do tempo também, porque se tem uma coisa que é bastante comum de acontecer é começar um projeto bonitinho do zero, mas com o passar do tempo ele virar uma completa bagunça. Lembre-se sempre da **Regra do Escoteiro**:
> "Ao sair da área onde você estava acampado, deixe-a mais limpa do que quando a encontrou."

É uma regra simples, mas bastante efetiva. Quando você estiver trabalhando em algum código, se encontrou algo que pode ser melhorado, melhore! Não deixe pra depois, porque o depois na verdade quer dizer nunca.

Você não precisa refatorar a classe inteira, são ações pequenas como mudar o nome de um método que não estava muito claro ou quebrar um método que estava muito grande em outros menores.

---

_Ao longo do capítulo o autor dá várias outras dicas, mas preferi não me alongar muito e escolhi apenas os pontos que considerei mais importantes._

_Para um entendimento mais profundo e detalhado, não deixe de ler o livro!_

[Próximo capítulo: Nomes Significantes >>](https://github.com/allan-pires/cleancode4noobs/blob/master/capitulo-2/nomes-significantes.md)
