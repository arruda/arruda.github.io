Title: Ponteiros - Para tirar dúvidas Pt 2
Date: 2011-05-24 16:22
Author: arruda
Category: C/C++, programação
Tags: C, CPP, ponteiro
Slug: ponteiros-para-tirar-duvidas-pt-2
Status: published

Seguindo a mesma idéia do [post anterior](http://www.arruda.blog.br/?p=256 "Ponteiros – Para tirar duvidas"), dou uma continuidade no tópico de como utilizar ponteiros.

Agora vou focar em como acessar atributos de um objeto instanciado a partir de um ponteiro de uma classe:

``` {lang="cpp" line="1"}
class MinhaClasse{
private:
int x;
public:
MinhaClasse(){ x = 0; }

MinhaClasse(int x){
this->x = x;
}
void setX(int x){ this->x = x;}
int getX(void){return this->x;}
};
```

E na main.cpp:

``` {lang="cpp" line="1"}
int main(void){

/*Criando uma instancia da MinhaClasse,
usando o contrutor padrao.
*/
MinhaClasse instancia;

/*Criando uma instancia da MinhaClasse a partir de um ponteiro
da classe.
Usando construtor parametrizado.
*/
MinhaClasse * instanciaPonteiro = new MinhaClasse(10);

/*Criando um vetor de MinhaClasse apartir de um ponteiro
da classe.
Nesse caso ele utiliza o construtor padrão.
*/
MinhaClasse * vetorDeClasses = new MinhaClasse[15];

//===========Acessando Pos metodos:===========
cout << instancia.getX() << endl;

cout << instanciaPonteiro->getX() << endl;

for (int i=0; i < 15;i++)
    vetorDeClasses[i].setX(i);

for (int i=0; i < 15;i++)
    cout << vetorDeClasses[i].getX() <
Com esse código o que teremos de saída será:

"0

10

1

2

...

15"
Dessa forma, o que podemos notar é que:

Ao instanciar uma classe, acessamos seus atributos da forma:

"instancia.atributo", ou "instancia.getAtributo()" para atributos privados.
Para uma instancia a partir de um ponteiro, devemos usar no padrão:

"instanciaPonteiro->atributo" ou "instanciaPonteiro->getAtributo()" no caso de atributos privados.
Para acessar um atributo de uma instancia de um vetor(feito a partir de um ponteiro), usamos da seguinte forma:

"vetorDeClasses[posicao].atributo" ou "vetorDeClasses[posicao].getAtributo()" no caso de atributos privados.

Vcs me perguntam: "O que raios quer dizer esse ->?"

Esse "->" nada mais é do que um atalho para "acessar um atributo/método de uma instância através do conteúdo de um ponteiro". Isso é:

instanciaPonteiro->atributo = (*instanciaPonteiro).atributo 
```

Por enquanto é só isso, caso esteja com duvidas em coisas mais básicas sobre ponteiros, dê uma olhada no [post anterior](http://www.arruda.blog.br/?p=256 "Ponteiros – Para tirar duvidas").

Abraços.
