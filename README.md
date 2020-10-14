# typescript-cheatsheet
Algumas anotações que acho relevante sobre TypeScript.

## Começando do básico
A linguagem javascript possui definições de variáveis do tipo dinâmicas, porém com o avanço da tecnologia e a intenção de melhorias na qualidade de implementação e manutenção do código, foi criado a extensão do TypeScript, que é um js processado com tipagem das variáveis.

A intenção do typescript é a melhoria de definição dos recursos componentizados dentro de um projeto, minimizando a possibilidade de erros dentro dos parametros de uma função ou dados dentro de algum object.

## Posso testar os códigos aqui?
Sim, os códigos que são exibidos neste cheatsheet sempre são testados e executados no TypeScript Playground, acessível no site:
https://www.typescriptlang.org/play

Lá você está passível de testes a todos os recursos do TS.

## O que é este repositório?
Este repositório é um "guia de bolso" que resolvi compartilhar com a comunidade, com algumas utilidades de recursos do typescript.

Sinta-se a vontade para dar palpites nas issues.

Ah, aqui vou usar alguns termos 'abrasileirados' para 'tipagem', para facilitar o seu entendimento, então em alguns momentos vou falar 'tipar', ou 'tipando' e etc, mas tudo se refere ao termo 'tipagem'.

# O básico:
## Tipando uma variável:
```TYPESCRIPT
const nome: string;
// você pode também atribuir diretamente um valor:
const idade: number = 26
```
Existem diversos tipos de tipagens, como: `string, number, object, any, null, undefined, boolean` entre vários outros "tipos de tipagens"

## Tipando parâmetros:
Um dos pricipais recursos do TS é você poder criar tipagens para os seus parâmetros de uma função, o benefício disso, é que você 'obriga' o seu parceiro de equipe que está aproveitando este código a evitar falhas de algum parâmetro passando da forma inválida, fora de ordem e etc...

E você pode fazer da seguinte forma:
```TYPESCRIPT
// no padrão 'funcion'
function meuNome(nome: string){
  return `Meu nome é ${nome}`;
};
console.log(meuNome('Rodrigo')); // retorno: 'Meu nome é Rodrigo'
// no padrão 'arrow function' (e como se usa mais de um parametro)
const meuNome = (nome: string, sobrenome: string) => {
  return `Meu nome é ${nome} ${sobrenome}`
};
console.log(meuNome('Rodrigo', 'Almeida')); // retorno: 'Meu nome é Rodrigo Almeida'
```
De toda forma, sempre que você criar algum tipo de função que seja necessário parâmetros, basta você seguir o padrão `nomeDaVariavel: tipoDaVariavel`

## Tipando uma função:
Quando se fala de tipar uma função, você está se referindo ao retorno da função, então qual é o tipo do valor que ela vai retornar.

Na forma tradicional:
```TYPESCRIPT
function minhaIdade(idade: number):string {
  return `Sua idade é ${idade}`;
};
console.log(minhaIdade(26)) // retorno: 'Sua idade é 26'
```
O que aconteceu acima?
Eu forcei a função `minhaIdade` a mesmo que eu passe um valor do tipo `number` a retornar um valor do tipo `string`.

Então, caso eu precise salvar o retorno desta função em alguma variável (e certamente vou precisar), a própria variável já sabe que o retorno ali é uma string.

Mais um exemplo usando arrow function:
```TYPESCRIPT
const minhaIdade = (idade: number): string => {
  return `Sua idade é ${idade}`;
};
console.log(minhaIdade(26)) // retorno: 'Sua idade é 26'
```

Para exemplificar melhor, um erro que pode acontecer:
```TYPESCRIPT
function minhaIdade(idade: number): string {
  return `Sua idade é ${idade}`;
};

const idade: number = minhaIdade(26);
console.log(idade) // No caso vai dar um erro, pois em uma variável que deveria ser do tipo number, estou executando uma function que retorna uma string;
```
