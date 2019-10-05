Title: Ponteiros - Para tirar duvidas
Date: 2011-05-02 10:00
Author: arruda
Category: C/C++, programação
Tags: C, CPP, ponteiro
Slug: ponteiros
Status: published

Como muitas pessoas tem dúvidas no assunto, decidi fazer um post explicando a idéia básica por trás dos ponteiros.

Vou usar um simples exemplo para passar a idéia:

``` {lang="c" line="1"}
int main(void){

int * a;
int b, c;
b=110;
a=&b;
c=b;
(*a)--;

printf("%d %d %d", *a, b, c);

return 0;
}
```

O que será impresso no exemplo acima?  
Caso não tenha percebido ainda, o resultado será:  
"109 109 110"

Eis o por que:
--------------

Existem ali 2 variaveis inteiras(b e c) e um ponteiro para inteiro(\*a), logo b e c estão alocados à algum endereco de memoria(ex: 4042XF00 e 1280FX92), e a ainda não está apontando para nenhum endereço de inteiro.

**Quando faço:**

``` {lang="c"}
b=110;
```

estou atribuindo a variavel b o valor de "110".

**Depois quando faço:**

``` {lang="c"}
a=&b;
```

estou dizendo que: *a variavel "a" vai receber o valor do endereco da variavel b.*  
Isso fará com que "a" aponte para "b".

Mas por que passar fazer "a = &b" e não simplesmente "a = b"?  
Por que "a" por ser um ponteiro inteiro, não armazena o valor de um inteiro, e sim do endereço de memoria para um inteiro.

**Logo depois, com a linha:**

``` {lang="c"}
c=b;
```

Estou fazendo com que "c" receba o mesmo valor de "b". E com isso temos que c = 110.

**Agora, na linha:**

``` {lang="c"}
(*a)--;
```

Pode ser facilmente traduzido para:  
*acesse o conteudo da variavel para quem a esta apontando(\*a) e reduza em um essa variavel.* E que em codigo é a mesma coisa que:

``` {lang="c"}
b--;
//que pode ser escrito como:
b = b -1;
```

Com isso temos que b=109.

**Para finalizar:**

``` {lang="c"}
printf("%d %d %d", *a, b, c);
```

Isso vai imprimir o conteúdo de a(que como já vimos antes é b), b e c.  
Como b é igual a 109, e c é igual a 110.  
O resultado vai ser "109 109 110".

Espero que isso ajude quem tem duvidas em ponteiro, o que é algo bem comum até.  
Abraços.
