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

### P1179 数字统计
[和P1980 计数问题解法相同]({% post_url 2023-08-20-part1-scratch %} #p1980-计数问题)
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
    int l, r;
    int cal(int n, int x){
        if(n <= 1) return 0;
        int t = 1, ans = 0;
        while(t <= n){
            int a = n / (t * 10);
            int b = n / t % 10;
            int c = n % t;
            
            if(b < x) ans += a * t;
            if(b == x) ans += a * t + c + 1;
            if(b > x) ans += (a + 1) * t;
            
            t *= 10;
        }
        return ans;
    }
    int main(){ 
        cin >> l >> r;
        cout << cal(r, 2) - cal(l-1, 2);
        system("pause");
        return 0;   
    }
    {% endhighlight %}
</details>

### P2615 神奇的幻方
纯模拟没啥说的
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
    int x[5000], y[5000], p[500][500];
    int n;
    int main(){ 
        cin >> n;
        x[1] = 1; y[1] = (1 + n) / 2; p[1][(1+n)/2] = 1;
        for(int i = 2 ; i <= n * n ; ++ i){
            if(x[i-1] == 1 && y[i-1] != n) x[i] = n, y[i] = y[i-1] + 1;
            if(x[i-1] != 1 && y[i-1] == n) x[i] = x[i-1] - 1, y[i] = 1;
            if(x[i-1] == 1 && y[i-1] == n) x[i] = x[i-1] + 1, y[i] = y[i-1];
            if(x[i-1] != 1 && y[i-1] != n){
                if(p[x[i-1]-1][y[i-1]+1] == 0) x[i] = x[i-1] - 1, y[i] = y[i-1] + 1;
                else x[i] = x[i-1] + 1, y[i] = y[i-1];
            }
            p[x[i]][y[i]] = i;
        }
        for(int i = 1 ; i <= n ; ++ i){
            for(int j = 1 ; j <= n ; ++ j){
                printf("%d%c", p[i][j], j==n?'\n':' ');
            }
        }
        system("pause");
        return 0;   
    }
    {% endhighlight %}
</details>

## Part 2.2 排序算法
### P1177 【模板】快速排序
第一种随机选[L, R]区间一个点作为基数排序。这种得特判所有数字都一样的数组，不然会T。
第二种写法三路快排。

<details> 
    <summary>普通快排</summary>
    {% highlight cpp %}
    #include <bits/stdc++.h>
    #define endl '\n'
    #define ll long long
    #define PB push_back
    #define POP pop_back
    #define INF 0x3f3f3f3f
    using namespace std;
    const int maxn = 2e5 + 10;
    int n;
    int a[maxn];
    inline int random(int l, int r){
        return (rand() % (r - l + 1)) + l;
    }
    inline void qsort(int L, int R){
        if(L >= R) return;
        int l = L, r = R;
        int mid = random(l, r), base = a[mid];
        swap(a[L], a[mid]);
        while(l < r){
            while(l < r && a[r] >= base) r --;
            while(l < r && a[l] <= base) l ++;
            if(l < r) swap(a[l], a[r]);
        }
        a[L] = a[l];
        a[l] = base;
        qsort(L, l - 1);
        qsort(l + 1, R);
    }
    int main(){ 
        srand(time(0));
        cin >> n;
        int f = 0;
        for(register int i = 1 ; i <= n ; ++ i){
            scanf("%d", &a[i]);
            if(i>=2 && a[i]!=a[i-1]) f = 1;
        }
        if(f) qsort(1, n);
        for(register int i = 1 ; i <= n ; ++ i) printf("%d%c", a[i], i==n?'\n':' ');
        system("pause");
        return 0;   
    }
    {% endhighlight %}
</details>

三路快排其实就是先随机挑选一个值V，然后把原始数组排成三块，一块是小于V，一块是等于V，一块是大于V。

我们分三种情况进行讨论三路快排的过程。


<a class="post-image" href="{{site.url}}/images/三路快排1.png" >
<img itemprop="image" data-src="{{site.url}}/images/三路快排1.png" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>

i: 遍历的当前索引位置

cur: 索引i所对应的值

L: 数组的最左端

R: 数组的最右端

V: 最开始在区间[L, R]随机挑选的基准值

sm: 数组中已经排好序的**小于**V区间的最后一个元素的索引

lg: 数组中已经排好序的**大于**V区间的第一个元素的索引

**第一种情况**

当前处理的元素cur = V，元素 e 直接纳入深蓝色区间，同时i向后移一位。
<a class="post-image" href="{{site.url}}/images/三路快排2.png" >
<img itemprop="image" data-src="{{site.url}}/images/三路快排2.png" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>

**第二种情况**

当前处理元素cur < V，cur和等于 V 区间(深蓝色)的第一个位置进行交换，同时索引 sm 和 i 都向后移动一位
<a class="post-image" href="{{site.url}}/images/三路快排3.png" >
<img itemprop="image" data-src="{{site.url}}/images/三路快排3.png" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>

**第三种情况**

当前处理元素cur > V，cur 和 lg-1 索引位置(也就是大于V区间最左端的前一个位置)的数值进行交换，同时 lg 索引向前移动一位。
<a class="post-image" href="{{site.url}}/images/三路快排4.png" >
<img itemprop="image" data-src="{{site.url}}/images/三路快排4.png" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>

最后当 i = lg 时，结束遍历，同时需要把 V 和索引 sm 指向的数值进行交换，这样这个排序过程就完成了，然后对 < V 和 > V 的数组部分用同样的方法再进行递归排序。

<details>  
    <summary>三路快排</summary>
    {% highlight cpp %}
    #include <bits/stdc++.h>
    #define endl '\n'
    #define ll long long
    #define PB push_back
    #define POP pop_back
    #define INF 0x3f3f3f3f
    using namespace std;
    const int maxn = 2e5 + 10;
    int n;
    int a[maxn];
    inline int random(int l, int r){
        return (rand() % (r - l + 1)) + l;
    }
    inline void qsort(int L, int R){
        if(L >= R) return;
        int l = L, r = R;
        swap(a[L], a[random(L, R)]);
        int sm = L, lg = R + 1, cur = L + 1, v = a[L];
        while(cur < lg){
            if(a[cur] < v){
                swap(a[sm + 1], a[cur]);
                cur ++;
                sm ++;
            }
            else if(a[cur] > v){
                swap(a[lg - 1], a[cur]);
                lg --;
            }
            else if(a[cur] == v) cur ++;
            
        }
        swap(a[sm], a[L]);
        qsort(L, sm - 1);
        qsort(lg, R);
    }
    int main(){ 
        srand(time(0));
        cin >> n;
        for(register int i = 1 ; i <= n ; ++ i){
            scanf("%d", &a[i]);
        }
        qsort(1, n);
        for(register int i = 1 ; i <= n ; ++ i) printf("%d%c", a[i], i==n?'\n':' ');
        system("pause");
        return 0;   
    }
    {% endhighlight %}
</details>

### P1059 明明的随机数
STL unique了解一下
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
	const int mod = 1e9 + 7;
	int n;
	int a[maxn];
	int main(){
		cin >> n;
		for(int i = 1 ; i <= n ; ++ i) scanf("%d", &a[i]);
		sort(a + 1, a + 1 + n);
		int m = unique(a + 1, a + 1 + n) - a - 1;
		cout << m << endl;
		for(int i = 1 ; i <= m ; ++ i) printf("%d%c", a[i], i == m ? '\n' : ' ');
		system("pause");
		return 0;   
	}
    {% endhighlight %}
</details>

### P1059 明明的随机数
STL unique了解一下
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
	const int mod = 1e9 + 7;
	int n;
	int a[maxn];
	int main(){
		cin >> n;
		for(int i = 1 ; i <= n ; ++ i) scanf("%d", &a[i]);
		sort(a + 1, a + 1 + n);
		int m = unique(a + 1, a + 1 + n) - a - 1;
		cout << m << endl;
		for(int i = 1 ; i <= m ; ++ i) printf("%d%c", a[i], i == m ? '\n' : ' ');
		system("pause");
		return 0;   
	}
    {% endhighlight %}
</details>

### P1068 分数线划定
结构体排序
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
	const int mod = 1e9 + 7;
	int n, m;
	unordered_map<int, int> mp;
	struct node{
		int id, mark;
		friend bool operator < (node a, node b){
			return a.mark == b.mark ? a.id < b.id : a.mark > b.mark;
		}
	}a[maxn];
	int main(){

		cin >> n >> m;
		for(int i = 1 ; i <= n ; ++ i) scanf("%d %d", &a[i].id, &a[i].mark);
		sort(a + 1, a + 1 + n);
		int k = int(m * 1.5);
		int p = n;
		while(a[p].mark < a[k].mark) p --;
		cout << a[p].mark << ' ' << p << endl;
		for(int i = 1 ; i <= p ; ++ i) cout << a[i].id << ' ' << a[i].mark << endl;
		system("pause");
		return 0;   
	}
    {% endhighlight %}
</details>

### P1051 谁拿了最多奖学金
结构体排序
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
	const int mod = 1e9 + 7;
	struct node{
		string name;
		int fen;
		int id;
		friend bool operator < (node a, node b){
			return a.fen == b.fen ? a.id < b.id : a.fen > b.fen;
		}
	}s[105];
	int n, num, mo, ban, sum;
	char a, b;
	int main(){
		scanf("%d", &n);
		for(int i = 1 ; i <= n ; ++ i){
			cin >> s[i].name >> mo >> ban >> a >> b >> num;
			if(mo > 80 && num >= 1) s[i].fen += 8000;
			if(mo > 85 && ban > 80) s[i].fen += 4000;
			if(mo > 90) s[i].fen += 2000;
			if(mo > 85 && b == 'Y') s[i].fen += 1000;
			if(ban > 80 && a == 'Y') s[i].fen += 850;
			s[i].id = i;
			sum += s[i].fen;
		}
		sort(s + 1, s + 1 + n);
		cout << s[1].name << endl;
		cout << s[1].fen << endl;
		cout << sum << endl;
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
        id:'2023-08-20-part2-basic-algorithm',

    });
    gitalk.render('gitalk-container');
</script>
<!-- Gitalk end -->

<script async src="//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"></script>
<span id="busuanzi_container_site_uv"><br>
  本站总访客数<span id="busuanzi_value_site_uv"></span>人次
</span>
