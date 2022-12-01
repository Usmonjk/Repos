///@CodeByUsmonjk@
#include<bits/stdc++.h>
#define ll long long
#define ld long double
#define ull unsigned long long
#define en '\n'
#define ios ios_base::sync_with_stdio(0) ; cin.tie(0) ; cout.tie(0) ;
using namespace std;


int main()
{
    ld a,b,c,d,e;
    vector<pair<ld , ld>>pr;
    cout<<fixed<<setprecision(10);
    cin>>a>>b>>c;
    for(ll i=0; i<a; i++)
    {
        cin>>d>>e;
        pr.push_back( { e , d } );
    }
    sort(pr.begin() , pr.end());
    ld l=0, r=1e9;
    while(r-l>0.0000000001)
    {
        bool ok=1;
        ld mid=(l+r)/2;
        ld height=0,width=0;
        for(ll i=0; i<pr.size(); i++)
        {
            if(pr[i].second*mid>b)
            {
                ok=0;
                break;
            }
            height+=pr[i].first*mid;
            width+=pr[i].second*mid;
            if(pr[i].first==pr[i-1].first and i!=0 and width<=b)
            {
                height-=pr[i].first*mid;
            }
            else
            {
                width=pr[i].second*mid;
            }
        }
        if(height>c)
        {
            ok=0;
        }
        if(ok==1)
        {
            l=mid;
        }
        else
        {
            r=mid;
        }
    }
    cout<<l<<en;
}
