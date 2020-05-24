# <a id="summary">Clean Code</a>

- [O Código Limpo](#codigolimpo)
- [Nomes com Significado](#nomesignificado)
- [Classes](#classes)
- [Funções](#funcoes)
- [Comentários](#comentarios)
- [Formatação](#formatacao)
- [Objetos e Estrutura de Dados](#objetosestrutura)
- [Tratamento de Erro](#tratamentoerro)
- [Teste Unitário](#testeunitario)
- [Fronteiras](#fronteiras)
- [Sistemas](#sistemas)
- [Conceitos Finais](#conceitos)

## <a id="codigolimpo"> O Código Limpo</a>

Se o seu código **não** está limpo, o problema é **seu** e provavelmente o problema é **você**! 

**Você não foi profissional!**

Não é o cronograma, não é o gerente, o usuário ou o cliente, o problema é **você**!

Da mesma forma que um médico defende lavar as mãos antes de uma cirurgia mesmo que o dono do hospital diga pra não lavar para defender a vida do paciente você deve **defender** o **código**!

Saber identificar código ruim **não significa que você é o cara**! 
Você **pode saber identificar** que uma pintura está mal pintada **mesmo não sabendo** pintar.

Crie seu **senso de código**, que é saber o que é código bom e ruim e tenha estratégias e disciplina  para transformar um código ruim em um código limpo

**Não é a linguagem** que faz um programa ser simples,  **é um programa** que faz a linguagem parecer simples.

Você passa **10** vezes mais tempo **lendo código** do que escrevendo então escreva bem, mesmo que seja difícil, pense e demore o tempo necessário para escrevê-lo, assim **poderá ler mais rápido**

###### <a href="#summary">voltar sumário</a>

## <a id="nomesignificado">Nomes com Significado</a> 

Tudo é nomeado, classe, métodos, parâmetros, projetos, arquivos e diretórios então **faça isso direito!**

Qualquer **idiota** pode escrever código que **máquinas** entendem, um **profissional** escreve código que outras **pessoas** entendem.

Use nome reveladores, invista tempo pensando, isso irá salvar tempo no futuro.

Nomes são usados para comunicar com os outros, **pense** neles

>**Porque existe? O que faz? Como usar?** São perguntas que ajudam a encontrar um bom nome, se um nome precisa de um comentário para explicar é porque não é um bom nome

Nome tem que ser capaz de pronunciar, não pareça um idiota tentando falar palavras impossíveis como apRltd ou vlTranscMsg


**Não use comentários, use nomes:**

**Errado:**
```
int d;//elapsed time in days
```

**Certo:**
```
int elapsedTiemInDays;
```

Pense em comunicar sua **intenção** pelo nome, se precisa explicar o nome com um comentário o nome escolhido é péssimo

**Evitar desinformação**, nome que não faz o que diz é um erro rude!

**Evitar encondings, prefixo e sufixo,** evolua como o mundo evoluiu 
Esqueça o **Impl**, não use o **I** não use o **_** 

O Impl pode receber o nome **especializado** e o I na frente do nome pouco importa o **tipo** que a entidade é para o **nome** que recebe 


**Errado:**
```
_transaction
ITransactionRepository
TransactionRepositoryImpl
```

**Certo:**
```
transactionToProcess
TransactionRepository
TransactionRepositoryCosmosDB ou TransactionCosmosDBRepository
TransactionRepositoryMySQL
TransactionRepositoryDynamoDB
```

**Faça seu código ser legível e ter padrão:**

- Coloque o get, set e is
- Verbo para método
- Substantivo para classe
- Adjetivo para enum
- Classes especializadas tem o nome especializado
- Se a classe é abstrata o nome também deve ser
- Não use constantes sendo o próprio nome, de nome inteligente para elas


**Certo:**
```
getAge
setAge
isAdultAge

Food (Classe Abstrata)
Coffee (Classe)
CoffeeSpecialty (Classe Especializada)
CoffeeTraditional (Classe Especializada)
```

**Errado:**
```
ageValueInt -> getAge
changeAgeValue -> setAge
ageBellowThan -> isAgeBelowThan

FoodCoffeeSpecial (Classe) Food -> Coffee -> CoffeeSpecialty
```

**Variáveis** devem ter **nomes curtos** em um **escopo curto** e **nome longos** em um **escopo longo** 

> Nomes curtos para variavel de um método e nomes longos para constantes, por exemplo 

**Funções** devem ter **nomes curtos** quando o **escopo é longo** e **nome longo** quando o **escopo é curto**

> Nomes curtos para classes públicas nomes longos para classes privadas 


**Variável:**
```
public const String LOG_MESSAGE_SUCCESS_READ_DATABASE =....

private String coffeeName = ....
```

**Função:**
```
public String toString() {
...
} 

private boolean isCoffeeSpecialty(Coffee coffee) {
...
}

````
###### <a href="#summary">voltar sumário</a>
## <a id="classes">Classes</a>
**Organização das classes:**
- Constantes primeiro 
- Variáveis estátivas
- Variáveis da instância 
- Funções públicas 
- Funções privadas 

> Pode-se preferir por Função pública seguidas de seus métodos privados correlacionados e depois outra função pública, assim por diante. 

**Encapsulação:** 

- Variáveis e funções úteis devem ser privadas
> Não seja fanático podemos quebrar a regra pra **melhorar os testes**

**Tamanho:**
- Classe devem ser pequenas 
>Como medimos? Com responsabilidade, deve ter apenas uma responsabilidade!

**Coesão:** 
- Uma classe tem algumas propriedades e quanto mais metodos manipulam essas propriedades mais coeso é o método com a classe, se um método não utiliza as propriedades ou utiliza apenas uma, ele não é coeso com a classe

**Cuidado** para não ferir oPrincípio da responsabilidade única (SRP), Aberto-Fechado (Open-close) e o Princípio da Inversão de Dependência (Dependency Inversion Principle)

> Não ser dependente dos detalhes de implementação e sim das abstrações

###### <a href="#summary">voltar sumário</a>

## <a id="funcoes">Funções</a>

Uma **função** deve fazer **uma coisa**, somente uma, e **faze-la bem!** 

**Funções devem ser pequenas**

**A regra do scroll** diz que você não deveria usar o scroll pra ler uma função se usasse é porque ela estava grande demais, essa regra é dos **anos 80** onde cabiam apenas **20 linhas** na tela, quantas cabem na sua? Esqueça essa regra

**6 linhas de código** está muito bem, **10 é muito grande!** Ou seja, Funções devem ser pequenas, no máximo 8 linhas é uma boa métrica. 

> Qual é a sua métrica? Não tem métrica?

O nome de uma **função** deve ser **um verbo** e a função deve ser bem nomeada

**Funções longas** provavelmente **estão escondendo classes**. Muitas funções grandes podem ser quebradas em classes.

Não adianta quebrar em várias funções, uma classe deve ter uma **única responsabilidade**

**Extrair até cair ou Extrair até eliminar**
É uma **regra** que diz que deveriamos **extrair métodos curtos de dentro de longos métodos** e continuar fazendo isso até que o método tenha somente **uma responsabilidade**

Tenha **a mesma organização** em **todas** suas classes. 

Regra Passo para baixo (Step Down rule) diz que o mais importante vem primeiro, **constantes globais e variáveis** , **métodos público e seus filhos**, ou se preferir, **todos os públicos e depois os privados**

**Funções devem:**

Devemos **ter muitas e muitas** funções **pequenas** mas **nenhuma grande**

Funções devem fazer somente **uma coisa**

Funções devem ter no máximo **um bloco de identação**

> Se tem mais, extrair, refatorar, extrair, refatorar, extrair!

Funções devem ter **um nível de abstração**

Funções devem ter **3 parâmetros no máximo**, **1 é o ideal**

> Crie objetos como parâmetro se necessário 

Funções **não** devem possuir **parâmetros de output**

> Dificulta e muito a leitura e compreensão do código

Funções **não** devem usar **booleanos ou nulos como parâmetros**

> Já pensou que quando fazemos isso provavelmente é porque não estamos usando Orientação à Objetos da melhor forma, talvez tenha um tipo especializado escondido no seu parâmetro booleano

Fuja dos **efeitos colaterais** (side effects), **faça o que o nome diz** e somente isso

> Efeito colateral é quando chamamos um método que diz fazer uma coisa mas acaba fazendo duas e quem chama nem imagina

**Prefira exceptions** do que **código de erro** 

> Código de erro ficam obsoletos desatualizados e geram dependência e confusão

**Try/catch** deve fazer somente isso, ele nasceu para isso, **extrair o resto** em um outro metodo


**Certo:**
```
try { 
	addNewCoffeeItem(coffee);
}
catch (CoffeeNotAddedException ex) {
	...
}

private void addCoffeeItem(Coffee coffee) {
	...
} 
```

**Peça não pergunte (Tell don't ask)**, não recupere objetos ou propriedades para que você atue com eles não é sua responsabilidade, peça que algo seja feito.


**Errado:**
```
CellPhone c = new CellPhone();
Boolean hasCamera = c.isCellPhoneWithCamera();

if(!hasCamera) {
 	throw new CellPhoneNoCameraException("Cell phone doesn't have camera");
}
 
c.turnOnCamera();

if(c.isCameraTurnedOn()) {
	c.takePhoto();
}
```

**Certo:**
```
CellPhone c = new CellPhone();
c.takePhoto();
````
> Toda responsabilidade de saber ligar a câmera tratar erros, retentativas, validações e etc devem ser da classe responsável e de suas especializações não de quem a utiliza


**Evitar ao máximo Switch**, ele cria dependências fortes, tentou **polimorfismo ou abstract factory**, tente primeiro, pense mais um pouco e se usá-lo for realmente necessário **use somente em classe baixo nível** e que esse switch **nunca se repita** em outro ponto do código

**Não se repita** (DRI, don't repeat yourself) essa regra é fácil se está usando **CTRL + C e CTRL** + V algo de errado **não está certo**! Está ferindo algum ou muitos princípios, não possua métodos ou classes que fazem as mesmas coisas e coisas muito parecidas!
###### <a href="#summary">voltar sumário</a>
## <a id="comentarios"> Comentários</a>

 Comentários devem ser **coisas raras** em seu código, **seu comentário, é o próprio código!**

Comentários indicam que você **falhou em expressar sua intenção** no código, todo comentário é uma **falha normalmente de nomenclatura** de variáveis, de métodos, até mesmo por não **extrair seus métodos** para terem apenas uma responsabilidade

**Errado:**
```
//Método que verifica se um café já existe, cria se não existe e retorna true, se existe atualiza e returna false, se não existe returna null
public static Boolean create(Coffee coffee){

}
```

**Certo:**
```
...
try {
	createOrUpdate(coffee);
} catch (CoffeeNotExists ex) {
	...
}

public static void createOrUpdate(Coffee coffee) {

}
```

Se necessário, e somente assim, **aceite a falha e escreva um comentário** que deixe sua intenção clara para qualquer pessoa, normalmente utilizamos para:

- Explicar uma regular expressions
- Explicar um comando sql
- Explicar uma fórmula matemática complicada
- Documentar uma api publica
- Copyright

```
//Regex - CPF e CNPJ com caracteres ".", "-" e "/" opcionais
([0-9]{2}[\.]?[0-9]{3}[\.]?[0-9]{3}[\/]?[0-9]{4}[-]?[0-9]{2})|([0-9]{3}[\.]?[0-9]{3}[\.]?[0-9]{3}[-]?[0-9]{2})

//Retorna todos os clientes e possíveis pedidos
SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID
ORDER BY Customers.CustomerName;

```

**Comentários mentem!** Não por mal, mas escrevemos os comentários na primeira versão do código e depois que refatoramos, ou atualizamos nem sempre atualizamos os comentários e o que acontece quando alguém lê depois de alguns meses, eles mentem!

Comentários precisam ser **bem posicionados**, se existe um comentário sobre um método em outro lugar sem ser **exatamente acima** dele a chance de ele ser esquecido é muito grande

**Comentários //TODO** servem por um propósito de revisão de código ou de uma tarefa que será realizada em um curto período de tempo, você, como um bom profissional **nunca deveria submeter código com um TODO**

###### <a href="#summary">voltar sumário</a>

## <a id="formatacao">Formatação</a>

**Todos** no time devem seguir a mesma formatação, não importa se concorda ou não depois de estabelecido pelo time **siga a formatação!**

O código **tem que** possuir uma **organização percetível** e não parecer que foi escrito por um conjunto de bêbados ou por pessoas e sim por um time

Crie as regras do time, em 10 minutos definam a formatação, convenção de nomes e etc

Ter uma **ferramenta** para **automátizar a formatação** é a maneira mais efetiva!

Criar padrões de **organização de classe**

Manter uma **organização clara** de package, namespaces, imports, variáveis, métodos públicos e privados. Ou seja, tudo deve ser padronizado!

**O mais importante no começo** é uma regra que diz que as coisas mais importantes em uma classe ou função devem estar nas primeiras linhas!

**Funções dependentes** uma próxima da outra! 

Se esforce para **não ultrapassar 100 linhas por arquivo ou 120 caracteres por linha** 

Ou seja, nunca use o scroll para a direita, se é necessário utilizá-lo você está escrevendo mal!

Sempre **coloque espaços e linhas em branco** para tornar o programa **mais legível**, lembre-se o programa é escrito para que humanos possam ler e não máquinas!

Fazer seu **código legível é mais importante do que do que código que funciona**

Tente **evitar get e set**, use **peça não pergunte (tell don't ask)**, aumenta a coesão do seu programa.

###### <a href="#summary">voltar sumário</a>

## <a id="objetosestrutura"> Objetos e Estrutura de Dados </a>

- **Não confunda classe com estrutura de dados**:
	- Estrutura de dados tem variáveis públicas mas sem funções de negócio
	- Classes tem variáveis privadas e métodos públicos 


**Objetos esconde dados e expõe funções**

**Estrutura de dados expõe dados e esconde funções**

**Estruturas** se dão bem com **adicionar funções** mas não com **adicionar novos tipos**

**Objetos** se dão bem em **adicionar novos tipos** mas **não com funções** 

Ou seja:,

**Objetos expõe comportamento e esconde dados, isso facilita criação de outros tipos de objetos com o mesmo comportamento e dificulta alterar comportamento nos tipo existentes**

**Estrutura de dados expõe dados e não possui comportamento significativo o que facilita alterar comportamento das estruturas existentes mas dificulta adicionar novos tipos aos comportamentos existentes**


### <a href="https://pt.wikipedia.org/wiki/Lei_de_Demeter" target="_blank">Lei de Demeter</a> 
**Uma classe não deve expor sua estrutura interna e nem conhecer outras**


Evitar acidentes de trem (Train Wrecks):
a().b().c()

**Evitar esses get e set** para não criar dependência

**Errado:**
```
User user = UserService.getUser();
user.authenticate();

```
Certo:
```
UserSerice.authenticate();
```
> Peça, não pergunte. A responsabilidade de saber como autenticar um usuário deve ser apenas da classe que conhece o usuário

**Interfaces ajudam a esconder a implementação** 

**Evite criar híbrido**, ou é um objeto ou é uma estrutura de dados

**Use DTOs (Data Transfer Objects) para transformar estrutura de dados em objetos**, por exemplo de Banco de dados ou de comunicação socket, api etc.

**Registro ativo (Active record)** é um dto com finalidade de salvar (save) e de buscar (find) mas ainda não são objetos 

A lei de Demeter nao se aplica para estrutura de dados

Lembrando que podemos **solucionar** esses problemas com o **Peça, não pergunte** (Tell, don't ask)

###### <a href="#summary">voltar sumário</a>

## <a id="tratamentoerro"> Tratamento de Erros </a>

**Use Exceções ao invés de códigos de retorno**, códigos de retorno se tornam desatualizados ou mentirosos

**Try-catch-finally** é a primeira coisa em um método e possui uma ou duas linhas em cada bloco, extraia em outros métodos

**Errado:**
```
private void wrong() {
	
	try {
		x.anything = doOtherThing();
		logger.log("Hey");
		if (x.isThis()) { 
			doOther();
		}
		doSomething();
		logger.log("Hey");
	} catch (IllegalArgumentException | NullPointerException ex) {
		logger.error("Hey");
		if(x.some()){
			doOnError();
		}
	} finally {
		...
	}
}
```

**Certo:**
```
private void right() {
	try {
		tryRight();
	} catch (SomeCustomException ex) {
		doOnError();
	} finally {
		...
	}
}

private void tryRight() {
	x = getSomething();
	x.anything = doOtherThing();
	logger.log("Hey");
	....
}

private void doOnError() {
	....
}
```
**Envie junto com a exceção uma mensagem coerente**

**Crie abstrações** para apis ou na entrada do programa para lançar apenas uma exceção customizada

Defina um **handler para capturar exceções na saída do programa**

**Cuidado com os nulos**, não retorne e nem passe, **use classes especializadas com casos especiais ou com lance exceções 

###### <a href="#summary">voltar sumário</a>

## <a id="testeunitario">Teste Unitário</a>

**3 regras do Teste Unitário (Unit Test):**

- Não escreva código em produção até ter um teste falhando 

- Você não deve escrever nada além do Unit test que quebre o código 

- Você não deve escrever nada além do que o necessario para passar no teste falho 

O **código dos testes** é tão **importante** quanto o de produção, **limpe-o**!

O que torna seus testes limpos? **Legibilidade** 

Nomenclatura deve ter um **padrão**, uma estratégia pode ser utilizar o **given-when-then**

**Crie métodos** com asserts auxiliares e retire trecho de código que ofusquem ou que não não passem a melhor intenção do teste 

**Tente usar apenas um Assert** em cada Unit test ou pelo menos minimizar eles ao máximo

Um test unitário tem que ser **FIRST:**
- Fast (Rápido)
- Independent (Independente) 
- Repeatable (Repetível) 
- Self-Validating (Auto validável)
- Timely (Feito no tempo certo e que não demore)

Os testes tem que ser **rápidos**, **independentes** um do outro, executáveis em qualquer **ambiente**, sempre retornar um **booleano** e sempre ser escrito **antes do código** de produção e que não demore para executar

**Desenvolvimento orientado a testes (TDD):**
- Escreva um teste que falhe
- Escreva o código que faça o teste passar
- Refatorar
- Repita!


###### <a href="#summary">voltar sumário</a>


## <a id="fronteiras">Fronteiras</a>

**Código nas fronteiras, vão mudar!** Devemos estar preparados pra isso então esse código precisa de uma separação, evite ter muitas referencias no código, **encapsule em classes** e use o padrão **Adapter**

Use **interfaces** e **padrões** de projeto para criar fronteiras com códigos que não existem ainda

Encapsular **código de terceiros** em uma **classe** para **não expor** métodos e propriedades indesejadas

**Aprenda código de terceiro fazendo unit testes**, não no código de produção
###### <a href="#summary">voltar sumário</a>

## <a id="sistemas">Sistemas</a>

Para um **sistema** ser considerado **limpo**:
- Ser testável
- Não ter código duplicado 
- Expressar sua intenção 
- Minimizar o número de classes e métodos 

**Concorrência:** 
- É complexo 
- Pode estar correto agora mas com carga não 
- Há muitos caminhos algum pode ser o errado
- Manter o código sobre concorrência longe dos demais 
- Encapsule e limite acesso a dados compartilhados
- Use sincronized ou copie os dados
- Tente usar variáveis locais 
- Sua thread deve ter seu próprio mundo particular 

> Sempre fique atento com a Concorrência do sistema, estude, teste e siga as dicas acima

###### <a href="#summary">voltar sumário</a>

## <a id="conceitos">Conceitos finais</a>
Comece pelos requisitos, os testes de UAT, os dados de entrada e de saída, requisitos técnicos e não funcionais.

Escreva o software engeneering guide

Vá para o quadro branco, desenhe a arquitetura e o design do sistema, com padrões e princípios

Escreva um código que funcione usando TDD

Faça sempre um teste que quebra, arrume e refatore 

Mantenha o código limpo 

Se virar um monstro antes de adicionar mais feature refatore 

Não tem motivo de você não tentar ter 100% de cobertura de código
###### <a href="#summary">voltar sumário</a>