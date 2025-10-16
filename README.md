# AlgoritmosePrograma-o
Codigos de aula de Algoritmos
#include <stdio.h>
#include <stdlib.h>

typedef struct celula cel;
struct celula
{
   int dado;
   cel* esq;
   cel* dir;
};

cel* inserir(int v, cel* raiz)
{
    if(raiz == NULL)
    {
        cel* c = malloc(sizeof(cel));
        c->dado = v;
        c->esq = NULL;
        c->dir = NULL;
        return c;
    }
    if(v < raiz->dado)
    {
        raiz->esq = inserir(v, raiz->esq);
    }
    else if(v > raiz-> dado)
    {
        raiz-> dir = inserir(v,raiz->dir);
    }
    return raiz;
}
void imprimirCelula(cel* raiz)
{
    if(raiz == NULL)
    {
        return;
    }
   printf("(");
   imprimirCelula(raiz->esq);
   printf(",%d,", raiz-> dado);
   imprimirCelula(raiz-> dir);
   printf(")");

}

cel* busca(cel* raiz, int v)
{
    if(raiz == NULL) return NULL;
    
    if(raiz-> dado == v)
    {
        return raiz;
    }
    else if(raiz-> dado > v)
    {
       return busca(raiz->esq,v);
    }
    else if(raiz ->dado < v)
    {
        return busca(raiz->dir,v);
    }

}

int main()
{
    cel* raiz = NULL;
    raiz = inserir(13,raiz);
    raiz = inserir(9,raiz);
    raiz = inserir(7,raiz);
    raiz = inserir(25,raiz);

    imprimirCelula(raiz);
    cel* aux = busca(raiz,9);
    if(aux == NULL)
    {
        printf("Não achou");
    }
    else{
        printf("valor %d", aux->dado);
    }
    printf("\n");

    return 0;
}
