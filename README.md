# Estrutura-de-Decisao-aninhadas

Ir para o conteúdo principal
 
Moodle - IFRS

Programação Básica com Java III - Turma 2022B
Painel Meus cursos  PBJIII2022B 1. Integrando Estruturas de Controle  1.1. Estruturas de Decisão Aninhadas
1.1. Estruturas de Decisão Aninhadas
Você já deve conhecer estruturas de decisão do tipo se...então, que permitem executar um determinado bloco de instruções  caso sua condição seja verdadeira e outro bloco de instruções caso o teste seja falso. Dentro desses blocos de instruções podem aparecer quaisquer tipos de comando que já estudamos até agora, incluindo até mesmo outras estruturas se...então! A isso chamamos de estruturas se...então aninhadas.

Um triângulo retângulo é mostrado com os catetos (identificados como A e C) e a hipotenusa (identificada como B).
Para entender melhor o uso de estruturas aninhadas, vamos analisar um exemplo. Uma figura bem conhecida na matemática é o triângulo. Um triângulo é formado por três lados que apresentam certas medidas, que podemos chamar genericamente de A, B e C. Eis algumas propriedades dos triângulos:

para que três medidas quaisquer A, B e C formem um triângulo, é necessário que a soma de duas delas seja maior do que a que sobra (A + B > C, A + C > B, B + C > A);
se as três medidas são iguais, o triângulo é equilátero;
se as três medidas são diferentes, o triângulo é escaleno;
se há apenas duas medidas iguais , o triângulo é isósceles.
Dadas essas propriedades de triângulos, deseja-se construir um programa que receba os valores para as três medidas A, B e C e diga se elas formam um triângulo ou não. Caso formem um triângulo, o programa deve mostrar que tipo de triângulo é formado.

A primeira coisa que precisamos descobrir é qual é a entrada necessária para o programa. Analisando o enunciado do problema, percebe-se que o usuário precisa informar os valores das medidas para os lados A, B e C (vamos utilizar o tipo real e permitir que o usuário informe qualquer tipo de número para as medidas).

Podemos resumir a saída que o programa precisa gerar em uma única mensagem. Digamos que mostraremos “As medidas informadas não formam um triângulo”, caso as medidas A, B e C informadas não formem um triângulo, a mensagem “As medidas formam um triângulo EQUILATERO” caso formem um triângulo equilátero e as mensagens “As medidas formam um triângulo ISÓSCELES” e “As medidas formam um triângulo ESCALENO” para triângulos isósceles e escalenos, respectivamente.

Cada uma destas mensagens será mostrada em uma condição diferente. E quando precisamos testar condições, utilizamos estruturas SE...ENTÃO.

A questão neste problema é: quantas estruturas se...então serão necessárias e como serão organizadas no código? Bem, analisando o enunciado de nosso problema, verificamos que precisamos testar quatro coisas: se A, B e C formam um triângulo, se formam um triângulo equilátero, se formam um triângulo isósceles e se formam um triângulo escaleno.

Então precisamos de quatro estruturas se...então? Talvez. Como veremos daqui a pouco, podemos resolver esse problema com apenas três.

Primeiramente precisamos verificar se A, B e C formam um triângulo. Seguindo o que vimos até aqui, podemos desenvolver o pseudocódigo mostrado abaixo.




Algoritmo “Verificação de Triângulo – versão 1”

var


A, B, C : real


início

      leia A, B, C

      se A + B > C e A + C > B e B + C > A então

            escreva “As medidas informadas formam um triângulo”

      senão

            escreva “As medidas informadas NÃO formam um triângulo”

      fim se

fim


Porém, ainda nos falta verificar o tipo do triângulo formado. Essa verificação só será feita caso as medidas A, B e C realmente formem um triângulo. Logo, deveremos colocar esses testes dentro da estrutura se...então mostrado anteriormente. Assim, podemos construir o algoritmo mostrado abaixo.




Algoritmo “Verificação de Triângulo (versão 2)”

var


A, B, C : real


início

       leia A, B, C

       se A + B > C e A + C > B e B + C > A então

              se A = B e B = C então

                    escreva “As medidas formam um triângulo EQUILÁTERO”

             senão

                    se A != B e A != C e B != C então

                           escreva “As medidas formam um triângulo ESCALENO”

                    senão

                           escreva “As medidas formam um triângulo ISÓSCELES”

                    fim se

             fim se

       senão

             escreva “As medidas informadas NÃO formam um triângulo”

       fim se

fim


Uau! Isso parece muito louco! Estruturas se...então dentro de outras estruturas se...então. Como isso funciona?

O primeiro se...então que encontramos no algoritmo é exatamente o que fizemos no algoritmo anterior. Como vimos, ele serve para verificar se as medidas A, B e C formam um triângulo. Se elas não formarem, a mensagem “As medidas informadas NÃO formam um triângulo” será mostrada. A diversão começa quando as medidas formam um triângulo válido. Nesse caso, é necessário verificar o tipo do triângulo formado. Veja que estes testes só serão executados caso a condição do primeiro se...então for verdadeira, já que eles estão dentro dessa estrutura.

Note que a forma como escrevemos esses testes de tipo de triângulo parece estranha. Há apenas duas estruturas se...então, e a segunda está dentro do senão da primeira. Como isso funciona?

Primeiramente verificamos se as medidas A, B e C são iguais. Nesse caso a mensagem “As medidas formam um triângulo EQUILÁTERO” é mostrada, já que o triângulo com três lados iguais é equilátero. Ao observar a condição presente nesse se...então você pode pensar: não está faltando um teste? Afinal se verifica se A é igual a B e se B é igual a C, mas não se verifica se A = C. Bem, essa verificação não é necessária, já que, se A = B e B = C, por consequência A = C (isso é o que se chama em matemática de transitividade). Se você não ficou convencido, sinta-se desafiado a encontrar algum caso onde A = B, B = C e A é diferente de C!

Se as três medidas A, B e C não forem iguais, a sequência de execução do algoritmo cai na parte “senão” desse se...então. O que há lá? Outro se...então. Nesse caso, verificando se as medidas são todas diferentes (nesse caso as medidas formariam um triângulo escaleno). A operação de diferença não é matematicamente transitiva, e não é possível resumir a condição desse se...então em apenas dois testes: A != B  e B != C. Por exemplo, para A = 3, B = 4 e C = 3 o teste resultaria em verdadeiro, mas essas medidas formam um triângulo isósceles e não escaleno.

Veja que a mensagem “As medidas formam um triângulo ESCALENO” será exibida somente se o teste para triângulo equilátero for falso e se o teste para triângulo escaleno for verdadeiro. Assim, se o triângulo não é equilátero e não é escaleno, só sobra uma alternativa: o triângulo é isósceles. Assim, não é necessário se inserir mais um se...então.

Não seria mais simples construir um código contendo três estruturas se...então para se verificar o tipo de triângulos? Nesse caso, teríamos que construí-lo como mostrado abaixo.




             se A = B e B = C então

                    escreva “As medidas formam um triângulo EQUILÁTERO”

             fim se

             se A != B e A != C e B != C então

                    escreva “As medidas formam um triângulo ESCALENO”

             fim se

             se A = B e A != C ou A = C e A != B ou B = C e A != B então

                    escreva “As medidas formam um triângulo ISÓSCELES”

             fim se

 

A condição do último se...então, que verifica se o triângulo é isósceles, é bem grande! Seria possível simplifica-la, tornando-a menor? Não basta apenas verificar se A = B ou A = C ou B = C? Afinal, um triângulo isósceles não se caracteriza por possuir dois lados iguais? De acordo com esse raciocínio, obteríamos o pseudocódigo mostrado abaixo. 




             se A = B e B = C então

                    escreva “As medidas formam um triângulo EQUILÁTERO”

             fim se

             se A != B e A != C e B != C então

                    escreva “As medidas formam um triângulo ESCALENO”

             fim se

             se A = B ou A = C ou B = C então

                    escreva “As medidas formam um triângulo ISÓSCELES”

             fim se



Será que esse pedaço de algoritmo funciona corretamente? Vamos realizar um teste, imaginando que A = 2, B = 2 e C = 3. Nesse caso, o teste para o primeiro se...então resultará em falso, pois A = B é verdadeiro e B = C é falso. O teste do segundo se...então também resultará em falso, já que A != B resultará em falso. O teste do último se...então resultará em verdadeiro, já que A = B resultará em verdadeiro. 

Oba! Parece que funciona! Será mesmo? Deste exemplo você deve aprender uma lição importante: nunca se convença que um algoritmo funciona antes de testá-lo mais de uma vez. Um único teste correto não garante que o algoritmo realmente funciona. Quer ver?

Vamos testar agora nosso pedaço de algoritmo considerando A = 2, B = 2 e C = 2. Nesse caso, o triângulo é equilátero. O teste do primeiro se...então resulta em verdadeiro, como esperado, já que A = B e B = C. O teste do segundo se...então resulta em falso, já que A != B é falso, A != C é falso e B != C é falso também. E o teste do último se...então? Ao contrário do esperado, resulta em verdadeiro!!!! Isso acontece, pois A = B é verdadeiro, A = C é verdadeiro e B = C também. Assim, o programa mostraria que o triângulo é equilátero e também isósceles, o que não está correto. Para resolvermos esse problema, precisamos incluir também testes que verifiquem que há um lado diferente dos dois iguais (o que colocamos no pseudocódigo anterior).

Vamos voltar à primeira solução proposta (com as estruturas se..então aninhadas). Esse algoritmo não lhe parece mais simples do que o mostrado no pseudocódigo anterior? Esse é um caso em que utilizar estruturas aninhadas nos permite diminuir a quantidade de condições a serem verificados. Quanto menos testes melhor, afinal são menos instruções que a CPU precisa executar, fazendo com que o programa seja executado em menor tempo.

O código correspondente em Java é mostrado abaixo. 




public class VerificacaoTriangulo {

   public static void main(String[] args) {

      double A, B, C;

 

      System.out.print(“Medida A: ”);

      A = Double.parseDouble(System.console().readLine());

      System.out.print(“Medida B: ”);

      B = Double.parseDouble(System.console().readLine());

      System.out.print(“Medida C: ”);

      C = Double.parseDouble(System.console().readLine());

 

      if(A + B > C && A + C > B && B + C > A) {

          if(A == B && B == C)

             System.out.println(“As medidas formam um triângulo EQUILÁTERO”);

          else if(A != B && A != C && B != C)

             System.out.println(“As medidas formam um triângulo ESCALENO”);

          else

             System.out.println(“As medidas formam um triângulo ISÓSCELES”);

      } else {

          System.out.println(“As medidas informadas NÃO formam um triângulo”);

      }

   }

}


Note como escrevemos as estruturas if. Na primeira, que verifica se as medidas informadas formam um triângulo, utilizamos um par de chaves para delimitar suas instruções. O uso de chaves nesse if é necessário para evitar que o último else  do código não seja interpretado erroneamente pelo compilador. Isso acontece, pois sem o uso de chaves o compilador Java tenta atribuir um else sempre ao if mais próximo anterior a ele. Em nosso programa, se removêssemos as chaves, o compilador interpretaria que o último else se refere ao if que testa se o triângulo é escaleno, que por sua vez já possui um else. Que confusão!

Outro detalhe importante é que escrevemos o if que testa se o triângulo é escaleno na mesma linha do else do if anterior. Isso é uma prática comum, mas não é uma regra. Se você preferir escrevê-lo uma linha após, não há problema nenhum. Lembre-se de que o compilador Java ignora espaços em branco.

O uso de estruturas se...então aninhadas é bastante comum. Por exemplo, poderíamos escrever um algoritmo que verifica o maior de dois números como mostrado abaixo. Observe que não há teste para verificar se os números são iguais.




Algoritmo “Maior de Dois Números com Estruturas Aninhadas”

var

       n1, n2: real

início

       leia n1, n2

      

       se n1 > n2 então

             escreva n1

       senão

             se n2 > n1 então

                    escreva n2

              senão

                    escreva “Os números são iguais”

             fim se

       fim se

fim


O programa em Java que implementa esse algoritmo é mostrado abaixo. Note que as estruturas if aninhadas foram escritas de forma similar às do exemplo anterior.




public class MaiorDeDoisNumeros {


public static void main(String[] args) {


double n1, n2;

System.out.print(“Digite o primeiro número: ”);

n1 = Double.parseDouble(System.console().readLine());

System.out.print(“Digite o segundo número: ”);

n2 = Double.parseDouble(System.console().readLine());

 

if(n1 > n2)

System.out.printf(“Maior número: %d\n”, n1);

else if(n2 > n1)

System.out.printf(“Maior número: %d\n”, n2);

else

System.out.println(“Os números são iguais.”);













}


}


Última atualização: domingo, 1 nov 2020, 16:38
Seguir para...
Academi
Dúvidas? 
Perguntas frequentes

Fale conosco | Suporte | Contato

Informação
Termos e Condições de Uso
Aviso de Privacidade e Proteção de Dados Pessoais
Contato
Rua Gen. Osório, 348, Bento Gonçalves/RS
Siga-nos
Copyright © 2017 - Desenvolvido por LMSACE.com. Distribuído por Moodle

Português - Brasil ‎(pt_br)‎
English ‎(en)‎
Español - Internacional ‎(es)‎
Français ‎(fr)‎
Italiano ‎(it)‎
Português - Brasil ‎(pt_br)‎
Mudar para o tema padrão
