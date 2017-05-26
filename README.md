#include<stdio.h>
#include<string.h>
int num[20],atainokosu;
char input_str[100],enzanshi[10],str[10][20];

int a2i(char*str){
    int cnt;
    int num=0;

    for (cnt = 0; (str[cnt] >= '0') && (str[cnt] <= '9') ; cnt++) {
        num = 10 * num + (str[cnt]-'0');
    }
    return num;
}

int getch(){
    nt i=0;

    while( ( input_str[i] = getchar() ) != EOF)
        i++;
        input_str[i-1]='\0';
    return 0;
}

int divch(){

    int i=0,j=0,s=0;

    while(input_str[i]!='\0'){
        if(input_str[i] == '+' || input_str[i]=='-' || input_str[i]=='*' || input_str[i] =='/'){
            enzanshi[j]=input_str[i];
            j++;
            s=0;
        }
    else{
        str[j][s]=input_str[i];
        s++;
    }
    i++;
    }      
    atainokosu=j;
    for(i=0;i<=j;i++)
    num[i]=a2i(str[i]);

    return 0;
}

int calc(){
    int i=0,j;
    while(i<=atainokosu){
        if(enzanshi[i]=='*'){
            num[i]=num[i]*num[i+1];
            j=i;
            while(j<=atainokosu){
                num[j+1]=num[j+2];
                enzanshi[j]=enzanshi[j+1];
                j++;
            }
        atainokosu--;
        }
        else if(enzanshi[i]=='/'){
            num[i]=num[i]/num[i+1];
            j=i;
            while(j<=atainokosu){
                num[j+1]=num[j+2];
                enzanshi[j]=enzanshi[j+1];
                j++;
            }   
        atainokosu--;
        }
        else{
        i++;
        }
    }
    i=0;
    while(0<atainokosu){
        if(enzanshi[i]=='+'){
            num[i]=num[i]+num[i+1];
            j=i;
            while(j<=atainokosu){
                num[j+1]=num[j+2];
                enzanshi[j]=enzanshi[j+1];
                j++;
            }
            atainokosu--;
        }
        else if(enzanshi[i]=='-'){
            num[i]=num[i]-num[i+1];
            j=i;
            while(j<=atainokosu){
                num[j+1]=num[j+2];
                enzanshi[j]=enzanshi[j+1];
                j++;
            }
            atainokosu--;
        }
        else
        i++;
        }
    return 0;
}
int main(){
    int i;
    getch();
    divch();
    calc();
    printf("計算式=\"%s\"\n結果=%d\n",input_str,num[0]);

    return 0;
}
