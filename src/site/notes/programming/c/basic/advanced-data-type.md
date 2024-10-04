---
{"dg-publish":true,"dg-permalink":"programming/c/basic/advanced-data-type.md","permalink":"/programming/c/basic/advanced-data-type.md/"}
---


# Advanced Data Type

## struct

<details>

<summary>record in pascal</summary>

```pascal
program PrintBirthday;

type
    birthday = record
        year : integer;
        month : integer;
        day : integer;
    end;

var
    b : birthday;

begin
    b := (year: 2000; month: 1; day: 1); // 创建并初始化生日记录

    // 打印生日
    writeln('Birthday: ', b.day, '/', b.month, '/', b.year);
end.

```

</details>

<details>

<summary>struct in C</summary>

<pre class="language-c"><code class="lang-c">//* book.c -- one-book inventory */
#include &#x3C;stdio.h>
#include &#x3C;string.h>
char * s_gets(char * st, int n);
#define MAXTITL  41      /* maximum length of title + 1         */
#define MAXAUTL  31      /* maximum length of author's name + 1 */

<strong>struct book {            /* structure template: tag is book     */
</strong><strong>    char title[MAXTITL];
</strong><strong>    char author[MAXAUTL];
</strong><strong>    float value;
</strong><strong>};                       /* end of structure template           */
</strong>
int main(void)
{
<strong>    struct book library; /* declare library as a book variable  */
</strong>    
    printf("Please enter the book title.\n");
    s_gets(library.title, MAXTITL); /* access to the title portion         */
    printf("Now enter the author.\n");
    s_gets(library.author, MAXAUTL);
    printf("Now enter the value.\n");
    scanf("%f", &#x26;library.value);
    printf("%s by %s: $%.2f\n",library.title,
           library.author, library.value);
    printf("%s: \"%s\" ($%.2f)\n", library.author,
           library.title, library.value);
    printf("Done.\n");
    
    return 0;
}

char * s_gets(char * st, int n)
{
    char * ret_val;
    char * find;
    
    ret_val = fgets(st, n, stdin);
    if (ret_val)
    {
        find = strchr(st, '\n');   // look for newline
        if (find)                  // if the address is not NULL,
            *find = '\0';          // place a null character there
        else
            while (getchar() != '\n')
                continue;          // dispose of rest of line
    }
    return ret_val;
}

(base) kimshan@MacBook-Pro output % ./"book"
Please enter the book title.
Hello
Now enter the author.
Charles
Now enter the value.
10
Hello by Charles: $10.00
Charles: "Hello" ($10.00)
Done.
</code></pre>

</details>

<details>

<summary>struct 基础</summary>

声明

```c
// 1
struct book {            /* structure template: tag is book     */
    char title[MAXTITL];
    char author[MAXAUTL];
    float value;
};                       /* end of structure template           */
struct book library, *p_lib;

// 2 简化
struct book { 
    char title[MAXTITL];
    char author[MAXAUTL];
    float value;
} library, *p_lib;

// 3. 数组
struct book library[MAXBOOKS];

// 4. 嵌套
struct book {
    char title[MAXTITL];
    char author[MAXAUTL];
    float value;
    struct book[MAXRELATE] res;
} library[MAXBOOKS];

// 5 typedef
typedef struct BiTNode
{
    int data;
    struct BiTNode *lchild;
    struct BiTNode *rchild;
    //struct BiTNode *parent; // 变成了 三叉链表
}BiTNode,*BiTree;
```

初始化

```c
// 1. 按顺序
struct book library = 
{
    "The Pious Pirate and te Devious Damsel",
    "Rennee Vivotte",
    1.95
};

// 2. 按成员
struct book gift = 
{
    .value = 25.99;
    .author = "Me";
    .title = "You";
}
```

访问

```c
scanf("%f", &library.value);
s_gets(library.author, MAXAUTL);

scanf("%f", &p_lib->value);
s_gets(p_lib->author, MAXAUTL);
```

</details>

<details>

<summary>struct + malloc</summary>

struct 中声明字符串然后 scanf 进来会导致错误（可能把字符串保存在任意位置）

<pre class="language-c"><code class="lang-c">#include &#x3C;stdio.h>

#define LEN 20

struct names {
    char first[LEN];
    char last[LEN];
};

int main() {
    struct names veep = {"Talia", "Summers"};
    struct pnames treas = {"Brad", "Fallingjaw"};
    
    printf("%s and %s\n", veep.first, treas.first);
    
<strong>    struct names accountant;
</strong><strong>    struct names attorney;
</strong>
    printf("Enter the last name of your accountant: ");
<strong>    scanf("%s", accountant.last);
</strong>
    printf("Enter the last name of your attorney: ");
<strong>    scanf("%s", attorney.last); /* 这里有一个潜在的危险 */
</strong>    
    return 0;
}
</code></pre>

现在更好的办法是，struct 里边不要字符串，而是改成指针，每次去 malloc

<pre class="language-c"><code class="lang-c">// names3.c -- use pointers and malloc()
#include &#x3C;stdio.h>
#include &#x3C;string.h>   // for strcpy(), strlen()
#include &#x3C;stdlib.h>   // for malloc(), free()
#define SLEN 81
struct namect {
<strong>    char * fname;  // using pointers
</strong><strong>    char * lname;
</strong>    int letters;
};

void getinfo(struct namect *);        // allocates memory
void makeinfo(struct namect *);
void showinfo(const struct namect *);
void cleanup(struct namect *);        // free memory when done
char * s_gets(char * st, int n);

int main(void)
{
    struct namect person;
    
    getinfo(&#x26;person);
    makeinfo(&#x26;person);
    showinfo(&#x26;person);
    cleanup(&#x26;person);
    
    return 0;
}

void getinfo (struct namect * pst)
{
    char temp[SLEN];
    printf("Please enter your first name.\n");
    s_gets(temp, SLEN);
    // allocate memory to hold name
<strong>    pst->fname = (char *) malloc(strlen(temp) + 1);
</strong>    // copy name to allocated memory
    strcpy(pst->fname, temp);
    printf("Please enter your last name.\n");
    s_gets(temp, SLEN);
<strong>    pst->lname = (char *) malloc(strlen(temp) + 1);
</strong>    strcpy(pst->lname, temp);
}

void makeinfo (struct namect * pst)
{
    pst->letters = strlen(pst->fname) +
    strlen(pst->lname);
}

void showinfo (const struct namect * pst)
{
    printf("%s %s, your name contains %d letters.\n",
           pst->fname, pst->lname, pst->letters);
}

void cleanup(struct namect * pst)
{
    free(pst->fname);
    free(pst->lname);
}

char * s_gets(char * st, int n)
{
    char * ret_val;
    char * find;
    
    ret_val = fgets(st, n, stdin);
    if (ret_val)
    {
        find = strchr(st, '\n');   // look for newline
        if (find)                  // if the address is not NULL,
            *find = '\0';          // place a null character there
        else
            while (getchar() != '\n')
                continue;          // dispose of rest of line
    }
    return ret_val;
}


</code></pre>

</details>

<details>

<summary>struct 复合字面量（C99）</summary>

<pre class="language-c"><code class="lang-c">/* complit.c -- compound literals */
#include &#x3C;stdio.h>
#define MAXTITL  41
#define MAXAUTL  31

struct book {          // structure template: tag is book
    char title[MAXTITL];
    char author[MAXAUTL];
    float value;
};

int main(void)
{
    struct book readfirst;
    int score;
    
    printf("Enter test score: ");
    scanf("%d",&#x26;score);
    
    if(score >= 84)
<strong>        readfirst = (struct book) {"Crime and Punishment",
</strong><strong>            "Fyodor Dostoyevsky",
</strong><strong>            11.25};
</strong>    else
<strong>        readfirst = (struct book) {"Mr. Bouncy's Nice Hat",
</strong><strong>            "Fred Winsome",
</strong><strong>            5.99};
</strong>    printf("Your assigned reading:\n");
    printf("%s by %s: $%.2f\n",readfirst.title,
           readfirst.author, readfirst.value);
    
    return 0;
}
</code></pre>

</details>

<details>

<summary>伸缩型成员变量（C99）</summary>

结构体里边的数组不写 MAX，只写 方括号，这样后边的 malloc 就要去计算大小了

<pre class="language-c"><code class="lang-c">// flexmemb.c -- flexible array member (C99 feature)
#include &#x3C;stdio.h>
#include &#x3C;stdlib.h>

struct flex
{
    size_t count;
    double average;
<strong>    double scores[];   // flexible array member
</strong>};

void showFlex(const struct flex * p);

int main(void)
{
<strong>    struct flex * pf1, *pf2;
</strong>    int n = 5;
    int i;
    int tot = 0;
    
    // allocate space for structure plus array
<strong>    pf1 = malloc(sizeof(struct flex) + n * sizeof(double));
</strong>    pf1->count = n;
    for (i = 0; i &#x3C; n; i++)
    {
        pf1->scores[i] = 20.0 - i;
        tot += pf1->scores[i];
    }
    pf1->average = tot / n;
    showFlex(pf1);
    
    n = 9;
    tot = 0;
<strong>    pf2 = malloc(sizeof(struct flex) + n * sizeof(double));
</strong>    pf2->count = n;
    for (i = 0; i &#x3C; n; i++)
    {
        pf2->scores[i] = 20.0 - i/2.0;
        tot += pf2->scores[i];
    }
    pf2->average = tot / n;
    showFlex(pf2);
    free(pf1);
    free(pf2);
    
    return 0;
}

void showFlex(const struct flex * p)
{
    int i;
    printf("Scores : ");
    for (i = 0; i &#x3C; p->count; i++)
        printf("%g ", p->scores[i]);
    printf("\nAverage: %g\n", p->average);
}

</code></pre>

</details>

<details>

<summary>匿名结构（C11）</summary>

<pre class="language-c"><code class="lang-c">struct person
{
    int id;
<strong>    struct {char first[20]; char last[20];}; // 匿名结构
</strong>};

// 初始化
struct person ted = {8483, {"ted", "grass"}};
</code></pre>

</details>

<details>

<summary>结构体保存在文件中</summary>

<pre class="language-c"><code class="lang-c"><strong>#define MAXTITL 40  
</strong>#define MAXAUTL 40  
struct book {    
char title[MAXTITL];   
char author[ MAXAUTL ];    
float value;  
};  
</code></pre>

1. 可以用 fprintf

```c
fprintf(pbooks, "%s. %s. %.2f\n", primer.title, primer.author, primer.value);
```

2. fprintf + 固定宽度

```c
fprintf(pbooks, "%39s%39s%8.2f\n", primer.title, primer.author, primer.value);
```

3. 保存二进制文件

以二进制表示法储存数据的缺点是,不同的系统可能使用不同的二进制表示法,所以数据文件可能不具可移植性。甚至同一个系统,不同编译器设置也可能导致不同的二进制布局。

```c
fwrite(&primer, sizeof(struct book),l,pbooks);  
```

</details>

***

## union

只能存一个变量的数组，推荐使用方式：结构+联合

<pre class="language-c"><code class="lang-c">struct owner {
    char sosecurity[12];
    ...
};

struct leasecompany {
    char name[40];
    char headquarters[40];
    ...
};

union data {
    struct owner owncar;
    struct leasecompany leasecar;
};

struct car_data {
    char make[15];
<strong>    int status; /* 私有为0，租赁为1 */
</strong><strong>    union data ownerinfo;
</strong>    ...
};

</code></pre>

***

## enum

枚举，默认值是从 0 开始的 int，也可以自定义数值

```c
enum week = {Mon, Tus, Wen, Thr, Fri, Sat, Sun};
enum levels = {lows = 100, medium = 500, high = 2000};
```

<details>

<summary>Demo</summary>

```c
/* enum.c -- uses enumerated values */
#include <stdio.h>
#include <string.h>    // for strcmp(), strchr()
#include <stdbool.h>   // C99 feature
char * s_gets(char * st, int n);

enum spectrum {red, orange, yellow, green, blue, violet};
const char * colors[] = {"red", "orange", "yellow",
    "green", "blue", "violet"};
#define LEN 30

int main(void)
{
    char choice[LEN];
    enum spectrum color;
    bool color_is_found = false;
    
    puts("Enter a color (empty line to quit):");
    while (s_gets(choice, LEN) != NULL && choice[0] != '\0')
    {
        for (color = red; color <= violet; color++)
        {
            if (strcmp(choice, colors[color]) == 0)
            {
                color_is_found = true;
                break;
            }
        }
        if (color_is_found)
            switch(color)
        {
            case red    : puts("Roses are red.");
                break;
            case orange : puts("Poppies are orange.");
                break;
            case yellow : puts("Sunflowers are yellow.");
                break;
            case green  : puts("Grass is green.");
                break;
            case blue   : puts("Bluebells are blue.");
                break;
            case violet : puts("Violets are violet.");
                break;
        }
        else
            printf("I don't know about the color %s.\n", choice);
        color_is_found = false;
        puts("Next color, please (empty line to quit):");
    }
    puts("Goodbye!");
    
    return 0;
}

char * s_gets(char * st, int n)
{
    char * ret_val;
    char * find;
    
    ret_val = fgets(st, n, stdin);
    if (ret_val)
    {
        find = strchr(st, '\n');   // look for newline
        if (find)                  // if the address is not NULL,
            *find = '\0';          // place a null character there
        else
            while (getchar() != '\n')
                continue;          // dispose of rest of line
    }
    return ret_val;
}


```

</details>

***

## typedef

typedef 是编译器解释的，#define 是预处理器解释的。

typedef+结构(上边结构里边)

***

## 复杂声明

`int a[2][3];`

<svg version="1.1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 903.3535461425781 261.59228515625" width="1806.7070922851562" height="523.1845703125">  <!-- svg-source:excalidraw -->  <!-- payload-type:application/vnd.excalidraw+json --><!-- payload-version:2 --><!-- payload-start -->eyJ2ZXJzaW9uIjoiMSIsImVuY29kaW5nIjoiYnN0cmluZyIsImNvbXByZXNzZWQiOnRydWUsImVuY29kZWQiOiJ4nO1daVPbSFx1MDAxM/6eX5Fiv20t2pnuOfdcdTAwMWKQhDtcdTAwMWMmXHUwMDA0SG1RPuQjXHUwMDE4yfjAkK3897dHgCXLyFx1MDAxOONDm32dXHUwMDE0wVx1MDAxYdlcdTAwMWFp+ul+numeyT/v3r9f6d63/JW/3q/4d+Vis1FpXHUwMDE3+yt/uOO3frvTXGJcdTAwMDNqguh9J+y1y9GZ9W631fnrzz+LrZZXa3RLYXjllcPrh4/5Tf/aXHUwMDBmulx1MDAxZDrxXHUwMDFivX///p/oZ+JCXf+uXHUwMDFinVx1MDAxYlx1MDAxZI0vIyB98HNcdTAwMThEV1x1MDAwNFx1MDAwZUZcdTAwMTijtFx1MDAxZZzR6HygK3X9XG41V4vNjlx1MDAxZre4QytcdTAwMDdnbNdf3127qTbOt897R7vhvqnHV602ms1C975cdTAwMTl1qFx1MDAxM9J9x22dbju88r82Kt36080njmd9qlx1MDAxZPZq9cDvuFx1MDAxYueDo2GrWG50790xxlx1MDAwNkeLQS36jvjIXHUwMDFkvZOIXHUwMDFlXHUwMDEzkjNhXHJcdTAwMTPKmEGr+zyA9Fx1MDAwMFBcdTAwMThcdTAwMDYgXHUwMDE0s2hSXHUwMDFk21xim2Hbdew3qFpfiLhrpWL5qkb9XHUwMDBiKoNzuu1i0GlcdTAwMTXbNFLxef3HWzbMXHUwMDEz1lplhVx1MDAwMVx1MDAwMTzRkbrfqNW7rjcyvrpcdTAwMWZcclx1MDAwMufSSNTW2EGLu2Zru1x1MDAxMpnC3/Gjb1x1MDAxN6/9bfeRoNdsJp9fUHl8fkNcciXX8DFtVUnLSlxmO7DguH1S7vnl80rtZLe4gbeVtcFcdTAwMWRcdTAwMGWZYbHdXHUwMDBl+yuDlp9/jPtee79cdTAwMTP8uLztfb6rfvix1S/37+qXm5N97+Nv8Vx1MDAwM+i1KsVcdTAwMDfD5Vx1MDAxYaTkQqJUOn7IzUZwlX5cYs2wfPWMrVfDoFto/IgwwoaOfipeN5r3Q7ZcdTAwMTjhznXwXHUwMDFi+5v+rlxmNaw1XHUwMDFiNVx1MDAwN8KVpl9cdTAwMWRGZ7dBfmHQ3FxyW3FrmS5UbFx1MDAwNH57dDjDdqPWXGKKzZOsi9Jd+ltP5sS9hEGVilx1MDAxZN+1uuPmXWJsJvYkXG6zPFx0l1pcdEveJD7jRU+y8VFcdTAwMTe+dM+PVeNMNaty26+Iu3x7XHUwMDEyJSUhXHUwMDE4XHUwMDE0XHUwMDE3OuUqXHUwMDFlPFx09yzTXHUwMDEyuUZcdTAwMDOGJ7Gc8iTcd3+m9yRcdTAwMWE8Lq3VyFx1MDAwNVl58kpjPFx0cJTk7lx1MDAwNcTefk6eZFxmJlx1MDAxMVx1MDAwNLcsaa3zxyRfXHUwMDA2JvmiMKnTXHUwMDA3XHUwMDA3mFQg0VxuXHUwMDE08WN5XHSTPdPf2j2wm3BY3lhjd9qorl/KNya1Up5cdTAwMDXGOJJha1x1MDAxNGJcdTAwMTiT3HrzgyFcdTAwMDV0qymgS2D0k9n42uNcdTAwMDK6XHUwMDA0Llxmar5UXHUwMDE4XG4mUSRccnT+MIRlwFx1MDAxMFx1MDAxNlx1MDAwNEOO2bHROtJJTnry2Li69/nm6nj9+0Et9I8uzqTof7jdyDdcdTAwMGWJbHlEr41gzGhjmVx1MDAxYcahJlx1MDAwZW6JYFx1MDAxYoqemlx1MDAxYp2z2GiFpiFiXHUwMDE4NyxcdTAwMDOTgnGZtNY5Y5Ivg67yxdFVXHUwMDBlKn30XHSTXHUwMDE2gYRcdTAwMTWpwokhefxlY6cusXZ8sFx1MDAxZaizQnntoFn5nG9IKqk91IpYXHUwMDFmQ1x1MDAwMFCjkFx1MDAwNGUl4VFpqVxyT/VrdohU6Fx1MDAxOU6IVIYpJZiaXGaSim5QKmCx11xcXHUwMDA2JKVNiJ6FQHLxbJUvjq1yZOmjT5Aknmo542ZytopH1/Wdxu1p40dHXHUwMDFkfy3ip+JcdTAwMGb8nm9IXHUwMDEyXHUwMDA2KEqilkpzNErHV36AJPOMM3nGwIJVNtWvmVx1MDAwNkmFxFmN0cA0w/huxjFXxVx1MDAxNFx1MDAxYYmwXFxIWs100ljnXHUwMDBmycUzV75I5mrSR1x1MDAwN8xcdTAwMTWIzVmcnLd+2OqvXHUwMDFktFum/uP7fqhEsFe+uT/PN1wi0VxiT1x1MDAxM1FUXHUwMDFjh+dsXCJAXG7jUciS1GBNNKczN0RcbuZp0pJyXHUwMDE0++NcdTAwMTBpkFgr8KVcdTAwMDJSK2tcdTAwMTYnJZthrVFeLFx1MDAxY1OXnFx1MDAwNVx1MDAxONt+uftgj88gUmXSVlx1MDAwZVx1MDAwNohcdTAwMTW9XCJG+vJo6/uhOL/Zrq7LvZ2i2TJfTL5cdTAwMTEpgXnWkFwiI9uSUiSQ8DCjXHUwMDAznkGpyC1Ji+N0pNW8XGbTXHUwMDAzXHUwMDEy0Xho0FxuriTDpKBcdTAwMWRcdTAwMDCSzlx1MDAwMLQuOZOe71x1MDAxZEz1XHUwMDE4qaXRM5jqiZMnT0aEj0d+xrf4mpRcdTAwMGWunVx1MDAxZV6FXHUwMDA3Vbw8XHUwMDBlLy3Uzj6p2uWsUi9O50uehMxcdTAwMGJOYXq08IRmXHUwMDFlmXlhhpN/4pPjZbdSL4D5umtP5fZcdTAwMDUvNa93YD3MOV649UjqWfLE9OyNTOGF1Fx1MDAxN4UwXHUwMDEwUjFcdTAwMDLTPGdeZoBcdTAwMTgjmFF2JvMwU1x1MDAwMWZcXJwjf6Jek02cR1x1MDAwMEBUykhiXGJcdTAwMTNcdTAwMWJ01Vx1MDAwNpunm+t8tVx1MDAwNIdlXHUwMDBiXHUwMDA129rdhLxcdTAwMWI0etwq7abzk1x1MDAxZT4yZ4ZcdTAwMWVcIjfCjEzvpc3ZJ1mD/Fxy5iyVp8HSJaxW8tlZXHUwMDBizqzHXHUwMDFmlNzwnObjXHUwMDE0XHUwMDA2Q+ojmmW5/3FcdTAwMGVakzeYmYPOnoHLlPtuXGKNYcn5nZdMuXwob/3bw/omK8tbu7d2vNsuqXybMrlDT1i0pOxcdTAwMTkncs+HjJmswyPyzjRqZPP1zST4Lb1cdTAwMDA1i+LARPJcdTAwMDJRaNJGapmz4i7PvsBMVat+33GiYbFcbmP0qvNU/MCzUWlcdTAwMTHQWGYnXHUwMDBmMEFcdTAwMDW2vnzyYfND76T3/XS/v31/8DHfqJQgPFx1MDAwMIpcdTAwMWZKXHUwMDFizZN521x1MDAwN1RqwlxuKWuQipRGonVcdTAwMGX549dcdTAwMTeEXHUwMDE5XHUwMDAwlMjUMtPHXHUwMDBiXHUwMDA25a9fWVx1MDAwNYmnmYakJipNdEhOXHUwMDBlyVp4eoLYgk6xf/Lpols1e81cdTAwMGY635BUQnlEoqxSUsJIXHUwMDE5XHUwMDA3vfdIUrqyXHUwMDA1Q4whf6VVzCUutOBzL9LMXHUwMDE5KH/p0ipcdTAwMTgzM64tKEuSe/JcdTAwMDRyx7bPd8PSiazfXHUwMDFk9XD78624rLfzXHJKLY1HVFx1MDAwMJWEUSWGXHUwMDAyPNDCslRbPoqsjJRcdTAwMTYkuc7/XHUwMDE4IH/pXCIrXHUwMDEyL5mAJE5kiEK9grjWXHUwMDBim+3SXHUwMDBmvnt+f9a6Kn/xNy57Z2v5XHUwMDA2pLHCc4xcdTAwMTVBc2FEqlx1MDAwMJmioyOuXFzRaeOnRpZcdTAwMTIkudKgyFn8p4jrr15jhWPWXHUwMDA0WK2QI06OSN/cXWz011fb1cvq4f7qx83Cxl7O5yo548pcdTAwMTOCjItcdTAwMTFDJ1pcdTAwMTBb91x1MDAwMyS5x7Uku1x1MDAxN5JzzedX0TFdkZX7hKVuL7WkY1x1MDAxOaD8pauscMyiXHUwMDAwoVx1MDAxNFxuK/XkqNTfT2onX497Slx1MDAxZV/Dbr3S2+jeXHUwMDFk5Vx1MDAxY5VcdTAwMWO0Z1x1MDAxY0G3j5JxXHUwMDE4lWg8rbRGpjlcZtUq56POXG5olFx1MDAxMND+h+Zdf506q/HJashcXIwrXHUwMDE1KGmsmXwt7teD+1PJOltEfa/CU9XQ0Eo+plx1MDAxOVx1MDAwMLNS7NT9XHUwMDE55/YoID5VXHUwMDFjp6qtyN6IvzKrlLbzTYZw6TJ7XHUwMDE0rIm+XGZVdVxyUElxm6K1pl6kk39PIEWthYJkvWp+knuvxe5Yg47M/rkow7NMmUvyucKAnTy3p1n9y9ZFv3Zx++lroXp9s7u3XHUwMDEz8nxcdTAwMDdcdTAwMTnlolxil2Qh0cKzkdWggvyHpvgj9XxnLNmo9YL0KLZRmOfpxTZPhUlIfy2IXHUwMDE50L5R44U3XHUwMDE5ryBcdTAwMDYrp1pcdTAwMDbT6Vx1MDAxNtvd9UZQaVx1MDAwNLX0R/ygktHSLHa6XHUwMDFi4fV1o0vdOFxmXHUwMDFiQTd9RvS9a65cdTAwMDaq7lx1MDAxN0eeXHUwMDA1fXNmW8t93XAlVvzb+3jkojeD3//+4+Wz0yNcdTAwMWN/+F3y39diOiFQ0uHJclx1MDAxYVx1MDAxY1x1MDAwYpND+mqHXHUwMDA3VenbcK+sal8+XHUwMDE2Oripcp6u18J4XHUwMDAwkkvijtyJqGFIk9RTQFZqkDE911x1MDAwNd7MXHUwMDEz2jBjMFpK95yWQyRh+VRV8Ex4Ypa7iqVZbFx1MDAxYjFzhGueTF/+XHUwMDFm4U+v1axhd6/UgM9cbvCZ0zdWMbTIXlx1MDAxMcPLXHUwMDE3XHUwMDA3+5tHnavvXHUwMDA3bXV9eYNH/updIf+A1yCsjlxuJ0eKzdxqXHUwMDFkbYWUMj2nMnvAg5FcdTAwMDa0wlQpWVx1MDAxY9ONx1x1MDAxODAuuGL8OUZKwp5cdTAwMDFKlceYTvxITrXrwy+O+Kxhd6+RXHUwMDAxn1x1MDAxMeQzk5pCXHQk/akmR3xwtVM/xHrzY3BSrm3fVLSoXeW90IBYuys91CpcdTAwMTU4XHUwMDFmXHUwMDAwr1116TP6dFxuvP9WgiqUSlx1MDAxM1x1MDAxMXZcdTAwMDRiXHUwMDE2br0rT6daXHUwMDFmwa2l4Vx1MDAwZUNzUZtvXHUwMDA1t5H8/+B+4eyRXHUwMDExfiWaXHUwMDFm1mA8XHUwMDAzZ1x1MDAxYYFMQLvNilx1MDAwMMzkgFx1MDAxZb/PVy5cdTAwMDFN5ueRlEUk3zVaLu7mgd2+R4hE3Fx1MDAxNfH6TERPsLtbJqIl+XHG7DNeZYBw5lx1MDAxOWs5aVsghy5cdTAwMTFFYp+5x1wiXCKjXHUwMDA1+Z08MnaX67XxkE5cdTAwMGbxRMdcdTAwMWU3NIxuZKVcdTAwMDWNM9MubFx1MDAxNjYvSvv7XHUwMDFjPq+VXHUwMDBmYpbkbjos9zrRY4z0rpKaXHUwMDFlolFMyUTMXFypXHUwMDE1W85cIjwjwTo69MDpRm59yLdkdWn8TodDXTJcdTAwMTQrXHUwMDEwjJOGXHUwMDEyVEypXHUwMDEzPVx1MDAxMpJr4zZhSFx1MDAwNPK4QzN2aWlnMVOvlmnr7rU6auav9HOZxVgye7pRS05q5TVLXHTG21s+/Vx1MDAxY1pPkj0/ZZLS1IWjJ5lgcqBcdTAwMWXn4ulIhbqMsUktV1x1MDAxOJfNwlxiXHUwMDE0XFzOve5jYGmz3cDyyWzHuEfS7K9a7Vx1MDAxON/zNLmy338vLjZPNnTBWeTIMslcZumgTJS7pVRailegfPzuovlEuVx1MDAxNp7LOTHhcoGjfEZcdM9GS+65iyQ68TCmWP+ciXJhSZdyzVx1MDAxODrpObQvVrz2XHI86oTTJSRdtVx1MDAxNolFzoNcIkzyXHUwMDEzLv+RQ9FcdTAwMTJcdTAwMTGDqSA7IaPZvLrtb1x1MDAxN/p7N/efPt/Ug1B/XHJ7xefpXHUwMDAz6Vx1MDAwMZCWRl5cbk1cdTAwMWWejTJcdTAwMWH0NNFbhJH5/nlxXHUwMDFhiuNMMWFcXFrLus2RpeUjvbJcdTAwMWU39DDTiubfSWuyTd69VketfUa8hlRLlscjYyCAv8bhjTe6fDo8oT0kOm/wMeWScnhcdTAwMTKIzSNcdTAwMTdW8Fx1MDAxN2Zg3+DvXHUwMDAwPUVcdTAwMWHHXHUwMDE4ethcdTAwMTgtMJmI2ZCbtpZOXyqzme9cdTAwMTbaU7vJ6ZjNoonNjHlN5ia9mVtUSHI60dZcZlx1MDAxM2NcXFx1MDAwNXubh6WgXHUwMDFjXGJcdTAwMTFcdTAwMTR06fRgX1x1MDAxZeZ8zpV8nEdcbkBcdLcqQ+pUNVx1MDAxZck3j3MjlIWX9s1+65J+Q/LUlePJ9CqycShcdTAwMTfacq2MWupcdTAwMDb8+dqt5W0oL36Dv7/hwmv9Ulx1MDAxN52rjslezunmIEG9XCKrOn7kc4l3XG7WRGqlqzKybmXzcFx1MDAxOVx1MDAwNTfKY1xiT2VTY+r83lxud6JcdTAwMTbCkGVzSG+vXHUwMDEwq1x1MDAxOEN6SnGlKJA/WynlRFxm3fEsNs2ftYaZXHUwMDFltlx1MDAxM2qY8aFmWC7QOGv3P8lcYlTIXHUwMDE4s4mzXHUwMDFl1Fx1MDAwMidha9wqLcNccr5hXnb8jmbDnUJccqhobFx1MDAxNYlcdTAwMTm65minNJHLwVZiI/35V+mXLFt3r7SVx1/2LvmvXHUwMDBiXHUwMDE10devXHUwMDE0W61Cl6xtMFx1MDAwZWT1jcqjp4/vceW24ffXx6Py3eNcdTAwMTN1nsqPYPDz3c//XHUwMDAx4eLb3yJ9<!-- payload-end -->  <defs>    <style class="style-fonts">      @font-face {        font-family: "Virgil";        src: url("https://unpkg.com/@excalidraw/excalidraw@undefined/dist/excalidraw-assets/Virgil.woff2");      }      @font-face {        font-family: "Cascadia";        src: url("https://unpkg.com/@excalidraw/excalidraw@undefined/dist/excalidraw-assets/Cascadia.woff2");      }      @font-face {        font-family: "Assistant";        src: url("https://unpkg.com/@excalidraw/excalidraw@undefined/dist/excalidraw-assets/Assistant-Regular.woff2");      }    </style>      </defs>  <rect x="0" y="0" width="903.3535461425781" height="261.59228515625" fill="transparent"/><g transform="translate(179.55117797851562 80.10501098632812) rotate(0 40.24998474121094 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#2f9e44" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">a[0][0]</text></g><g transform="translate(301.9986877441406 76.7890625) rotate(0 36.079986572265625 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">a[0][1]</text></g><g transform="translate(413.42608642578125 74.38153076171875) rotate(0 40.48998260498047 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">a[0][2]</text></g><g transform="translate(182.3109130859375 127.9739990234375) rotate(0 36.079986572265625 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">a[1][0]</text></g><g transform="translate(303.88243103027344 128.15109252929688) rotate(0 31.909988403320312 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">a[1][1]</text></g><g transform="translate(415.30982971191406 125.74356079101562) rotate(0 36.319984436035156 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">a[1][2]</text></g><g transform="translate(31.251434326171875 103.54611206054688) rotate(0 20.389976501464844 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">logic</text></g><g stroke-linecap="round" transform="translate(167.49554443359375 67.71722412109375) rotate(0 169.1919708251953 19.11968994140625)"><path d="M9.56 0 C87.03 1.83, 165.58 1.7, 328.82 0 M9.56 0 C79.6 -0.57, 149.16 0.61, 328.82 0 M328.82 0 C334.89 1.45, 338.78 3.27, 338.38 9.56 M328.82 0 C333.67 -0.05, 338.41 2.83, 338.38 9.56 M338.38 9.56 C339.88 14.27, 336.96 17.63, 338.38 28.68 M338.38 9.56 C338.89 13.21, 338.33 17.3, 338.38 28.68 M338.38 28.68 C338.78 36.16, 337.18 38.2, 328.82 38.24 M338.38 28.68 C339.24 37.28, 335.28 40.33, 328.82 38.24 M328.82 38.24 C232.48 39.91, 134.89 40.24, 9.56 38.24 M328.82 38.24 C223.47 38.78, 118.27 38.29, 9.56 38.24 M9.56 38.24 C4.41 38.58, -1.96 35.32, 0 28.68 M9.56 38.24 C1.1 35.95, 1.99 33.56, 0 28.68 M0 28.68 C1.47 22.27, -0.81 18.03, 0 9.56 M0 28.68 C-0.42 23.08, -0.58 17.33, 0 9.56 M0 9.56 C-0.34 5.04, 1.85 -1.1, 9.56 0 M0 9.56 C-1.58 2.39, 4.44 -1.41, 9.56 0" stroke="#1971c2" stroke-width="2" fill="none"/></g><g stroke-linecap="round" transform="translate(166.1640167236328 118.5457763671875) rotate(0 169.1919708251953 19.11968994140625)"><path d="M9.56 0 C73.45 -2.07, 136.43 -1.96, 328.82 0 M9.56 0 C130.38 1.08, 252.26 1.46, 328.82 0 M328.82 0 C334.86 1.94, 337.78 2.2, 338.38 9.56 M328.82 0 C337.07 0.05, 337.84 5.41, 338.38 9.56 M338.38 9.56 C337.43 13.68, 339.05 16.75, 338.38 28.68 M338.38 9.56 C337.64 16.59, 338.91 22.52, 338.38 28.68 M338.38 28.68 C339.41 34.35, 336 39.45, 328.82 38.24 M338.38 28.68 C336.35 34.86, 332.99 40.43, 328.82 38.24 M328.82 38.24 C204.06 38.1, 82.55 36.13, 9.56 38.24 M328.82 38.24 C258.56 38.11, 188.54 38.64, 9.56 38.24 M9.56 38.24 C4.13 36.49, -1.38 34.8, 0 28.68 M9.56 38.24 C5.17 39.64, -1.37 32.86, 0 28.68 M0 28.68 C1 21.05, 1.31 13.63, 0 9.56 M0 28.68 C0.88 25.02, 0.81 20.9, 0 9.56 M0 9.56 C0.85 3.63, 4.6 0.83, 9.56 0 M0 9.56 C-0.17 3.13, 1.71 -1.47, 9.56 0" stroke="#1e1e1e" stroke-width="2" fill="none"/></g><g stroke-linecap="round" transform="translate(159.70285034179688 58.21337890625) rotate(0 178.36456298828125 54.585693359375)"><path d="M27.29 0 C110.41 -1.76, 194.89 -0.47, 329.44 0 M27.29 0 C118.9 -1.01, 210.22 -0.59, 329.44 0 M329.44 0 C349.34 1.53, 355.63 9.34, 356.73 27.29 M329.44 0 C348.71 -1.11, 354.61 10.4, 356.73 27.29 M356.73 27.29 C357.55 38.81, 358.4 50.08, 356.73 81.88 M356.73 27.29 C356.35 45.9, 356.95 64.67, 356.73 81.88 M356.73 81.88 C357.06 99.34, 346.25 111.13, 329.44 109.17 M356.73 81.88 C355.82 98.94, 349.8 107.66, 329.44 109.17 M329.44 109.17 C263.01 108.72, 193.01 108.42, 27.29 109.17 M329.44 109.17 C266.2 106.92, 203.94 107.99, 27.29 109.17 M27.29 109.17 C8.71 108.19, 0.04 98.6, 0 81.88 M27.29 109.17 C7.72 107.16, -0.84 100.45, 0 81.88 M0 81.88 C-0.7 59.98, -0.53 40.81, 0 27.29 M0 81.88 C0.01 62.03, 0.68 42.38, 0 27.29 M0 27.29 C0.63 10.97, 7.79 1.29, 27.29 0 M0 27.29 C-0.32 10.62, 7.83 0.92, 27.29 0" stroke="#e03131" stroke-width="2" fill="none"/></g><g transform="translate(30 200.0946044921875) rotate(0 36.499961853027344 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">physical</text></g><g transform="translate(170.73052978515625 202.87991333007812) rotate(0 40.24998474121094 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">a[0][0]</text></g><g transform="translate(293.17803955078125 199.56396484375) rotate(0 36.079986572265625 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">a[0][1]</text></g><g transform="translate(404.6054382324219 197.15643310546875) rotate(0 40.48998260498047 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">a[0][2]</text></g><g transform="translate(541.3771057128906 195.87969970703125) rotate(0 36.079986572265625 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">a[1][0]</text></g><g transform="translate(662.9486236572266 196.05679321289062) rotate(0 31.909988403320312 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">a[1][1]</text></g><g transform="translate(774.3760223388672 193.64926147460938) rotate(0 36.319984436035156 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">a[1][2]</text></g><g stroke-linecap="round" transform="translate(157.62374877929688 189.87249755859375) rotate(0 357.8648986816406 20.859893798828125)"><path d="M10.43 0 C219.18 -2.84, 429.42 -2.38, 705.3 0 M705.3 0 C714.15 1.58, 717.34 4.34, 715.73 10.43 M715.73 10.43 C716.93 18.95, 716.23 23.5, 715.73 31.29 M715.73 31.29 C714.66 38.57, 711.27 43.35, 705.3 41.72 M705.3 41.72 C552.02 43.69, 398.7 42.84, 10.43 41.72 M10.43 41.72 C2.03 40.66, -1.66 36.91, 0 31.29 M0 31.29 C-1.27 22.36, -0.67 17.24, 0 10.43 M0 10.43 C0.08 3.28, 3.45 0.25, 10.43 0" stroke="#1e1e1e" stroke-width="2.5" fill="none" stroke-dasharray="8 10"/></g><g stroke-linecap="round"><g transform="translate(285.2218322753906 79.13946533203125) rotate(0 0 12.65374755859375)"><path d="M0.3 -0.06 C0.23 4.19, 0.07 20.78, -0.05 24.96 M-0.22 -0.57 C-0.39 3.79, -0.66 21.15, -0.51 25.49" stroke="#1e1e1e" stroke-width="2" fill="none"/></g></g><mask/><g stroke-linecap="round"><g transform="translate(394.7312316894531 71.5087890625) rotate(0 -0.239044189453125 16.5885009765625)"><path d="M0.15 0.29 C0.05 5.82, -0.64 27.48, -0.78 33.05 M-0.43 -0.03 C-0.34 5.58, 0.42 28.19, 0.29 33.68" stroke="#1e1e1e" stroke-width="2" fill="none"/></g></g><mask/><g stroke-linecap="round"><g transform="translate(395.2310485839844 123.760986328125) rotate(0 0.142913818359375 14.001007080078125)"><path d="M-0.19 0.42 C-0.22 5.19, -0.36 23.45, -0.23 28.13 M0.71 0.16 C0.86 4.8, 0.79 22.64, 0.73 27.23" stroke="#1e1e1e" stroke-width="2" fill="none"/></g></g><mask/><g stroke-linecap="round"><g transform="translate(285.3549499511719 122.21270751953125) rotate(0 0 16.310028076171875)"><path d="M0.54 0.04 C0.57 5.49, 0.1 26.68, -0.06 32.17 M0.16 -0.41 C0.13 5.14, -0.61 27.22, -0.52 32.63" stroke="#1e1e1e" stroke-width="2" fill="none"/></g></g><mask/><g stroke-linecap="round"><g transform="translate(124.89840698242188 82.69511408898461) rotate(0 25.100494384765625 -0.4495840107076674)"><path d="M-0.1 0.27 C8 -0.16, 40.49 -1.2, 49.03 -1.38 M-1.61 -0.63 C6.8 -0.39, 42.38 -0.29, 51.13 -0.1" stroke="#2f9e44" stroke-width="2" fill="none"/></g><g transform="translate(124.89840698242188 82.69511408898461) rotate(0 25.100494384765625 -0.4495840107076674)"><path d="M27.44 8.22 C35.76 3.5, 42.46 4.27, 51.13 -0.1 M27.44 8.22 C35.11 5.21, 42.06 2.92, 51.13 -0.1" stroke="#2f9e44" stroke-width="2" fill="none"/></g><g transform="translate(124.89840698242188 82.69511408898461) rotate(0 25.100494384765625 -0.4495840107076674)"><path d="M27.64 -8.95 C36.07 -7.91, 42.69 -1.37, 51.13 -0.1 M27.64 -8.95 C35.38 -6.7, 42.27 -3.73, 51.13 -0.1" stroke="#2f9e44" stroke-width="2" fill="none"/></g></g><mask/><g transform="translate(86.06546020507812 68.38558959960938) rotate(0 16.989990234375 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#2f9e44" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">**a</text></g><g stroke-linecap="round"><g transform="translate(121.26577758789062 119.82529992734578) rotate(0 24.640850180075518 -6.4583790835887385)"><path d="M0.04 0.06 C8.25 -2.02, 41.53 -10.65, 49.69 -12.86 M-0.6 -0.38 C7.53 -2.34, 41.28 -10.07, 49.46 -12.13" stroke="#1971c2" stroke-width="2" fill="none"/></g><g transform="translate(121.26577758789062 119.82529992734578) rotate(0 24.640850180075518 -6.4583790835887385)"><path d="M28.2 1.9 C36.44 -2.7, 44.51 -9.33, 49.46 -12.13 M28.2 1.9 C33.28 -1.61, 38.69 -4.7, 49.46 -12.13" stroke="#1971c2" stroke-width="2" fill="none"/></g><g transform="translate(121.26577758789062 119.82529992734578) rotate(0 24.640850180075518 -6.4583790835887385)"><path d="M24.16 -15.05 C33.87 -13.21, 43.48 -13.4, 49.46 -12.13 M24.16 -15.05 C30.28 -14.29, 36.7 -13.12, 49.46 -12.13" stroke="#1971c2" stroke-width="2" fill="none"/></g></g><mask/><g transform="translate(93.87185668945312 107.73468017578125) rotate(0 11.829994201660156 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1971c2" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">*a</text></g><g transform="translate(45.11772155761719 30) rotate(0 40.41998291015625 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#e03131" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">a[2][3]</text></g><g stroke-linecap="round"><g transform="translate(140.74122619628906 40.91412353515625) rotate(0 23.743255615234375 9.47308349609375)"><path d="M1.07 1.12 C8.96 4.3, 39.51 14.84, 47.23 17.91 M0.18 0.67 C7.89 4.07, 38.41 16.09, 46.15 18.9" stroke="#e03131" stroke-width="2" fill="none"/></g><g transform="translate(140.74122619628906 40.91412353515625) rotate(0 23.743255615234375 9.47308349609375)"><path d="M20.59 18.51 C30 17.97, 33.92 18.4, 46.15 18.9 M20.59 18.51 C28.89 17.78, 38.3 17.93, 46.15 18.9" stroke="#e03131" stroke-width="2" fill="none"/></g><g transform="translate(140.74122619628906 40.91412353515625) rotate(0 23.743255615234375 9.47308349609375)"><path d="M26.82 2.17 C34.23 6.51, 36.32 11.75, 46.15 18.9 M26.82 2.17 C32.8 7.16, 40.04 13.02, 46.15 18.9" stroke="#e03131" stroke-width="2" fill="none"/></g></g><mask/></svg>

* 数组明后边的\[]和函数名后边的()具有相同优先级，他们优先级高于\*

```c
int *p[10]; // 含有十个指针的数组
int (*p)[10]; // 指向含有十个整数的数组的指针
```

```c
// 含有4 个指针的数组
    int *p[4];
    p[0] = &a[0][0];
    p[1] = &a[0][1];
    p[2] = &a[1][0];
    p[3] = &a[1][1];
    printf("%p %p %p %p\n", p[0], p[1], p[2], p[3]);
    printf("%d %d %d %d\n", *p[0], *p[1], *p[2], *p[3]);
    // 0x7ff7ba96b810 0x7ff7ba96b814 0x7ff7ba96b81c 0x7ff7ba96b820
    // 11 12 21 22

    // 指向数组的指针
    int num[4] = {100, 200, 300, 400};
    int(*q)[4] = num;
    printf("%p, sizeof(int)=%u,sizeof(q)=%u, sizeof(*q)=%u\n", q, sizeof(int), sizeof(q), sizeof(*q));
    printf("%d %d %d %d\n", (*q)[0], (*q)[1], (*q)[2], (*q)[3]);
    // 0x7ff7be28a7e0, sizeof(int)=4,sizeof(q)=8, sizeof(*q)=16
    // 100 200 300 400
```