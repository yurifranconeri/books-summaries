# Clean Code

- [O Código Limpo](#codigolimpo)
- [Nomes com Significado](#nomesignificado)
- [Funções](#funcoes)
- [Comentários](#comentarios)
- [Formato](#formato)
- [Objetos e Estrutura de Dados](#objetosestrutura)
- [Tratamento de Erro](#tratamentoerro)
- [Teste Unitário](#testeunitario)
- [Fronteiras](#fronteiras)
- [Classes](#classes)
- [Sistemas](#sistemas)
- [Conceitos Finais](#conceitos)

## <a id="codigolimpo"/> O Código Limpo

Se o seu código **não** está limpo, o problema é **seu** e provavelmente o problema é **você**! 

**Você não foi profissional!**

Não é o cronograma, não é o gerente, o usuário ou o cliente, o problema é **você**!

Da mesma forma que um médico defende lavar as mãos antes de uma cirurgia mesmo que o dono do hospital diga pra não lavar para defender a vida do paciente você deve **defender** o **código**!

Saber identificar código ruim **não significa que você é o cara**! 
Você **pode saber identificar** que uma pintura está mal pintada **mesmo não sabendo** pintar.

Crie seu **senso de código**, que é saber o que é código bom e ruim e tenha estratégias e disciplina  para transformar um código ruim em um código limpo

**Não é a linguagem** que faz um programa ser simples,  **é um programa** que faz a linguagem parecer simples.

Você passa **10** vezes mais tempo **lendo código** do que escrevendo então escreva bem, mesmo que seja difícil, pense e demore o tempo necessário para escrevê-lo, assim **poderá ler mais rápido**

## <a id="nomesignificado" />Nomes com Significado
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

## <a id="funcoes" />Funções

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

 

