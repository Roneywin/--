--
==

背包

//HDU 3466
#include<algorithm>
#include<iostream>
#include<cstring>
#include<cstdio>
#define Max(a,b) ((a)>(b)?(a):(b))
using namespace std;

int n,m;
int f[5005];
struct node{
    int p,q,v;
} mer[505];

bool cmp(node a,node b){
    return a.q-a.p<b.q-b.p;
}

int main()
{
    int n,m;
    while(scanf("%d %d",&n,&m)!=EOF){
        memset(f,0,sizeof(f));
        for(int i=1;i<=n;i++){
            scanf("%d %d %d",&mer[i].p,&mer[i].q,&mer[i].v);
        }
        sort(mer+1,mer+n+1,cmp);
        for(int i=1;i<=n;i++){
            for(int j=m;j>=mer[i].p;j--){
                if(j>=mer[i].q) f[j]=Max(f[j],f[j-mer[i].p]+mer[i].v);
            }
        }
        printf("%d\n",f[m]);
    }
    return 0;
}
