---
layout: post
title: "基础算法"
description: "The first post"
categories: [ACM]
tags: [题解]

---

* Kramdown table of contents
{:toc .toc}

# Part 2 基础算法
## Part 2.1 模拟
### P1003 铺地毯
8说了，自己看
<details> 
    <summary>展开代码</summary>
    {% highlight cpp %}
    #include <bits/stdc++.h>
    #define endl '\n'
    #define ll long long
    #define PB push_back
    #define POP pop_back
    #define INF 0x3f3f3f3f
    using namespace std;
    const int maxn = 2e5 + 10;
    int a[maxn][4];
    int n, x, y;
    int main(){ 
        cin >> n;
        for(int i = 1 ; i <= n ; ++ i){
            for(int j = 0 ; j < 4 ; ++ j) scanf("%d", &a[i][j]);
        }
        cin >> x >> y;
        for(int i = n ; i >= 1 ; -- i){
            if(x <= a[i][0]+a[i][2] && x >= a[i][0] && y <= a[i][1] + a[i][3] && y >= a[i][1]){
                cout << i;
                return 0;
            }
        }
        cout << "-1";
        system("pause");
        return 0;   
    }
    {% endhighlight %}
</details>

### P1067 多项式输出
注意以下系数为1、-1，首项和末项的判断。以及只有一个常数项的情况。
<details> 
    <summary>展开代码</summary>
    {% highlight cpp %}
    #include <bits/stdc++.h>
    #define endl '\n'
    #define ll long long
    #define PB push_back
    #define POP pop_back
    #define INF 0x3f3f3f3f
    using namespace std;
    const int maxn = 2e5 + 10;
    int n, x;
    int main(){ 
        cin >> n;
        for(int i = n ; i >= 0 ; -- i){
            cin >> x;
            if(n == 0){
                cout << x;
                return 0;
            }
            if(x == 0) continue;
            if(i == 0){
                cout << (x > 0 ? "+" : "");
                cout << x; continue;
            }
            else if(i == 1){
                if(x > 1) cout << "+" << x;
                else if(x == 1) cout << "+";
                else if(x < -1) cout << x;
                else if(x == -1) cout << "-";
                cout << "x"; continue;
            }
            else if(x == 1){
                if(i != n) cout << "+";
                cout << "x^" << i;
            }
            else if(x == -1){
                cout << "-x^" << i;
            }
            else{
                if(i != n && x > 0) cout << "+";
                printf("%dx^%d", x, i);
            }
        }
        system("pause");
        return 0;   
    }
    {% endhighlight %}
</details>

### P1328 生活大爆炸版石头剪刀布
8说了，自己看。不知道为什么题面没有图了。
不知道为什么定义vs数组用{}定义，Jekyll就报错了，所以用[]先代替了。
<details> 
    <summary>展开代码</summary>
    {% highlight cpp %}
    #include <bits/stdc++.h>
    #define endl '\n'
    #define ll long long
    #define PB push_back
    #define POP pop_back
    #define INF 0x3f3f3f3f
    using namespace std;
    const int maxn = 200 + 10;
    int n, a[maxn], b[maxn], x, y;
    int vs[5][5] = [[0,0,1,1,0],[1,0,0,1,0],[0,1,0,0,1],[0,0,1,0,1],[1,1,0,0,0]];
    int main(){ 
        cin >> n >> x >> y;
        for(int i = 0 ; i < x ; ++ i) scanf("%d", &a[i]);
        for(int i = 0 ; i < y ; ++ i) scanf("%d", &b[i]);
        int X = 0, Y = 0;
        for(int i = 0 ; i < n ; ++ i){
            if(a[i%x]==b[i%y]) continue;
            if(vs[a[i%x]][b[i%y]]) X ++;
            else Y ++;
        }
        cout << X << ' ' << Y;
        system("pause");
        return 0;   
    }
    {% endhighlight %}
</details>

### P1563 玩具谜题
巧用抑或和取余判方向。
<details> 
    <summary>展开代码</summary>
    {% highlight cpp %}
    #include <bits/stdc++.h>
    #define endl '\n'
    #define ll long long
    #define PB push_back
    #define POP pop_back
    #define INF 0x3f3f3f3f
    using namespace std;
    const int maxn = 2e5 + 10;
    int n, m;
    int a[maxn];
    char s[maxn][15];
    int main(){ 
        cin >> n >> m;
        for(int i = 0 ; i < n ; ++ i){
            scanf("%d %s", &a[i], s[i]);
            // cout << a[i] << ' ' << s[i] << endl;
        }    
        int x, y, pos = 0, fx = a[0];
        for(int i = 1 ; i <= m ; ++ i){
            scanf("%d %d", &x, &y);
            //逆时针01 10
            if(x^fx) pos = (pos + y) % n, fx = a[pos];
            else pos = (pos - y + n) % n, fx = a[pos]; 
        }
        printf("%s", s[pos]);
        system("pause");
        return 0;   
    }
    {% endhighlight %}
</details>

### P1042 乒乓球
注意直接一个E结束，和正好11：0结束都需要在输出一个0：0
<details> 
    <summary>展开代码</summary>
    {% highlight cpp %}
    #include <bits/stdc++.h>
    #define endl '\n'
    #define ll long long
    #define PB push_back
    #define POP pop_back
    #define INF 0x3f3f3f3f
    using namespace std;
    const int maxn = 2e5 + 10;
    int n, m;
    string s = "";
    char x;
    int main(){ 
        while(1){
            x = getchar();
            if(x == '\n') continue;
            if(x == 'E'){
                if(s.length() == 0) cout << "0:0\n\n0:0";
                break;
            }
            s += x;
        }
        n = s.length();
        int x = 0, y = 0;
        for(int i = 0 ; i < n ; ++ i){
            if(s[i] == 'W') x ++;
            if(s[i] == 'L') y ++;
            if(max(x, y) >= 11 && abs(x - y) >= 2){
                cout << x << ":" << y << endl;
                x = 0, y = 0;
                if(i == n - 1) cout << "0:0\n\n";
            }
            else if(i == n - 1){
                cout << x << ":" << y << endl;
                x = 0, y = 0; cout << '\n';
            }
        }
        for(int i = 0 ; i < n ; ++ i){
            if(s[i] == 'W') x ++;
            if(s[i] == 'L') y ++;
            if(max(x, y) >= 21 && abs(x - y) >= 2){
                cout << x << ":" << y << endl;
                x = 0, y = 0;
                if(i == n - 1) cout << "0:0";

            }
            else if(i == n - 1){
                cout << x << ":" << y << endl;
                x = 0, y = 0;
            }
        }
        system("pause");
        return 0;   
    }
    {% endhighlight %}
</details>

[^1]: This is a footnote.

[kramdown]: https://kramdown.gettalong.org/
[Simple Texture]: https://github.com/yizeng/jekyll-theme-simple-texture

<!-- Link Gitalk 的支持文件  -->
<link rel="stylesheet" href="https://unpkg.com/gitalk/dist/gitalk.css">
<script src="https://unpkg.com/gitalk@latest/dist/gitalk.min.js"></script>
<div id="gitalk-container"></div>
<script type="text/javascript">
    var gitalk = new Gitalk({

    // gitalk的主要参数
        clientID: '33599ca507921d70615d',
        clientSecret: '1e6229b3a409aac51d5d51dc5458a9c257ca59a9',
        repo: '300id.github.io',
        owner: '300id',
        admin: ['300id'],
        id:'2021-05-02-how-to-build-a-blog',

    });
    gitalk.render('gitalk-container');
</script>
<!-- Gitalk end -->

<script async src="//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"></script>
<span id="busuanzi_container_site_uv"><br>
  本站总访客数<span id="busuanzi_value_site_uv"></span>人次
</span>
