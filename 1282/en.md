# LOJ 1282-Leading and Trailing
  we can use the Binary Exponentiation to calculate the last three digits,
  
  but what about the first three digit?
  
  for any number a, it can be expressed as 10^a, which is actually an exponential function based on 10, 
  
  b = 10^b, 
  
  so a = log10(b), this a is divided into integer parts and decimal parts. n^k can be expressed as 10^(ak), 
  
  we assume that this ak is x,y then n = 10^x + 10^(0.y) here 10^x affects the size, 10^(0.y) affect the precision, 
  
  we want to take the first three bits we only need to know y, because y will affect the precision, so 10^2 .y is our answer.
  
  # C++ code
      
      
     #include<bits/stdc++.h>
     using namespace std;
  
     typedef long long LL;
     typedef unsigned long long ULL;
  
    LL quick_pow(LL a, LL b, LL m){
        LL ans = 1;
        while(b){
           if(b&1) ans = ans*a%m;
           a = a*a%m;
           b >>= 1;
       }
      return ans;
     }
 
     int main(){
         int T;
         scanf("%d", &T);
         for(int ca = 1; ca <= T; ++ca){
             LL n, k;
             scanf("%lld%lld", &n, &k);
             LL a = (LL)pow(10.0, fmod(log10((double)n)*(double)k, 1)+2.0);
            LL b = quick_pow(n, k, 1000);
             printf("Case %d: %03lld %03lld\n", ca, a, b);
         }
         return 0;
     }
  
