<h2 align="center"> Big-Integers </h2>
<p align="center"> As in C++, there is no any Big Integer datatype as it exists only on Java and PythonIt so I made these implementions for C++. This repo contains all the operations of Big Integers for C++. </p>

---

<h3 align="center"> Addition of Big Integers </h3>

```
string add_Num(string a, string b)
{
    string sum = "";
    long long i = (long long)a.size() - 1, j = (long long)b.size() - 1;
    long long carry = 0;
    while (i >= 0 or j >= 0)
    {
        carry += (a[i] - '0') * (i >= 0) + (b[j] - '0') * (j >= 0);
        sum += '0' + (carry % 10);
        carry /= 10;
        i--;
        j--;
    }
    while (carry)
    {
        sum += '0' + (carry % 10);
        carry /= 10;
    }
    reverse(all(sum));
    return sum;
}
```