#include <stdlib.h>
#include <stdio.h>
#include <time.h>
#include <string.h>
 
#define max 1700
#define min 0
#define tentativi 5
 

 //GENERATORE ARRAY
void genera(int a[], int i){
   int cont;
    for(cont=0;cont<i;cont++){
       a[cont]=min+rand()%(max-min+1);
   }
 
}
 
 
 //INSERTIONSORT
void insertionsort2(int* a, int low, int high) {
 int i, j, key = 0;
 for (j=low; j<=high; j++) {
   key = a[j];
   i = j-1;
   while(i>=low && a[i]> key) {
     a[i+1] = a[i];
     i = i-1;
   }
   a[i+1] = key;
 }
}


//STAMPA ARRAY
 int stampa_array(int a[],int i){
  for(int k=0; k<i;k++){
    printf("%d\t", a[k]);
  }
  printf("\n");
}
 

 //MERGE
void merge(int a[], int p, int q, int r) {
 int i,j,k;
 int n1 = q-p+1;
 int n2 = r-q;

 int* L = malloc(n1*sizeof(int));
 int* R = malloc(n2*sizeof(int));



for(i=0;i<n1;i++){
  L[i]=a[p+i];
}
for(j=0;j<n2;j++){
  R[j]=a[q+j+1];
}

 for (i=0, j=0, k=p; k<r+1; k++) {      // <-- DEVE essere r+1, e non r. // infatti vogliamo TUTTE le posizioni tra p ed r, quindi k deve poter prendere il valore r
   if (i==n1) a[k] = R[j++];
   else if (j==n2) a[k] = L[i++];
   else if (L[i] <= R[j]) a[k] = L[i++];
   else a[k] = R[j++];
 }
 free(L);
 free(R);
}


//MERGESORT 
void mergeSort(int a[], int p, int r) {
 int q;
 if (p < r) {
   q = (p+r)/2;
     mergeSort(a, p, q);
    mergeSort(a, q+1, r);
     merge(a, p, q, r);
  
 }
 return;
}


//IBRIDO
void Ibrido(int a[], int p, int r) {
 int q;
 int s;
 if (p < r) {
     
      s=(r-p)+1;

   if(q<700){
      insertionsort2(a,0,s-1);
   }
   else{ 
     q = (p+r)/2;
     Ibrido(a,p,q);
     Ibrido(a, q+1, r);
     merge(a, p, q, r);
   }
  
 }
 return;
}



 
int main(void) {
 int i, n;
 int b[i],c[i];
   clock_t start, end, timeIS, timeMS = 0, timeIB;
   srand(1);
   

   //INIZIALIZZAZIONE FILE 
       FILE *fp;
  fp=fopen("Test.txt","w");
   if(fp==NULL){
       printf("errore nell'apertura del file\n");
       return(1);}
   fprintf(fp, "lunghezza\t insertion\t merge\t ibrido\n");


   for (i=10;i<=max;i+=10){
           int a[i];
       genera(a,i);
      //COPIO L'ARRAY 
      for(int u=0;u<i;u++){
         b[u]=a[u];
       }

       for(int z=0;z<i;z++){
         c[z]=a[z];
       }

       timeIS = timeMS = timeIB = 0;
   for(n=0;n<tentativi;n++){
      

        start = clock();
       insertionsort2(a,0,i-1);
       end = clock();
       timeIS += end-start;


       start = clock();
       mergeSort(b,0,i-1);
       end = clock();
       timeMS += end-start;


        start =clock();
       Ibrido(c,0,i-1);
       end =clock();
       timeIB +=end-start;


   }
 

 fprintf(fp,"%d\t %f\t %f\t %f\n", i,  (double)timeIS/tentativi, (double)timeMS/tentativi, (double)timeIB/tentativi);
   }
 
return (0);
}


