#include <iostream>
#include <cstring>
using namespace std;
int i,n,j,poz,meniu,ok=1;
char num[20];
struct data
{
    int zi,luna,an;
};
struct pompier
{
    char nume[20];
    data data_nasterii;
    float salariu;
} v[30],aux;
void citire()
{
    n++;
    i=n;
    cout<<"Numele pompierului: ";
    cin>>v[i].nume;
    cout<<"Data nasterii: zi/luna/an";
    cin>>v[i].data_nasterii.zi>>v[i].data_nasterii.luna>>v[i].data_nasterii.an;
    cout<<"Salariu: ";
    cin>>v[i].salariu;
}
void afisare()
{
    cout<<"\n";
    for(i=1; i<=n; i++)
    {
        cout<<v[i].nume;
        cout<<" "<<v[i].data_nasterii.zi<<"/"<<v[i].data_nasterii.luna<<"/"<<v[i].data_nasterii.an;
        cout<<" "<<v[i].salariu;
        cout<<"\n";
    }
}
void stergere()
{
    cout<<"Nume:";cin>>num;
    for(i=1; i<=n; i++)
        if(strcmp(num,v[i].nume)==0)
        {
            for(j=i; j<=n; j++)
                v[j]=v[j+1];
            n--;
        }
}
void stergerepoz()
{
    cin>>poz;
    for(i=poz+1; i<=n; i++)
        v[poz]=v[i];
    n--;
}
void sortsalariu()
{
    for(i=1; i<=n; i++)
        for(j=i+1; j<n; j++)
            if(v[i].salariu>v[j].salariu)
                swap(v[i],v[j]);
}
void sortalf()
{
    for(i=1; i<=n; i++)
        for(j=i+1; j<n; j++)
            if(strcmp(v[i].nume,v[j].nume)==1)
                swap (v[i],v[j]);

}
void interfata()
{
    cout<<"~~~~~~~~~~~~~~~~~~~~~~~~MENIU~~~~~~~~~~~~~~~~~~~~~~~~"<<'\n';
    cout<<"1.Adaugare pompier."<<'\n';
    cout<<"2.Stergere pompier dupa nume."<<'\n';
    cout<<"3.Stergere pompier dupa o pozitie"<<'\n';
    cout<<"4.Afisare pompier in ordinea crescatoare a salariilor"<<'\n';
    cout<<"5.Afisare pompieri in ordine alfabetica."<<'\n';
    cout<<"6.Iesire."<<'\n';
    cout<<"~~~~~~~~~~~~~~~~~~~~~~~~MENIU~~~~~~~~~~~~~~~~~~~~~~~~"<<'\n';


}

int main()
{
    interfata ();
    while (ok)
    {
        cin>>meniu;
        switch (meniu)
        {
        case 1:
        {
            citire ();
            break;
        }
        case 2:
        {
            stergere();
            break;
        }
        case 3:
        {
            stergerepoz();
            break;

        }
        case 4:
        {
            sortsalariu();
            afisare();
            break;
        }
        case 5:
        {
            sortalf();
            afisare();
            break;
        }
        case 6:
            ok=0;
            break;
        default: "Alt raspuns"
            ;

        }

    }
    return 0;
}
