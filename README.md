<h2 align="center"> Big-Integers </h2>
<p align="center"> As in C++, there is no any Big Integer datatype as it exists only on Java and PythonIt so I made these implementions for C++. This repo contains all the operations of Big Integers for C++. </p>

---

<h3 align="center"> Addition of Big Integers </h3>

```
string Add_Num(string &a, string &b)
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
    reverse(sum.begin(), sum.end());
    return sum;
}
```
---

<h3 align="center"> Difference of Big Integers </h3>

```
void Make_A_Bigger(string &a, string &b)
{
    if (size(a) < size(b))
        swap(a, b);
    else if (size(a) == size(b))
    {
        rep(i, 0, size(a))
        {
            if (a[i] != b[i])
            {
                if (a[i] < b[i])
                    swap(a, b);
                break;
            }
        }
    }
}
string Diff_Num(string &a, string &b)
{
    Make_A_Bigger(a, b);
    string diff = "";
    long long i = (long long)a.size() - 1;
    long long j = (long long)b.size() - 1;
    long long carry = 0;
    while (i >= 0 or j >= 0)
    {
        if (j >= 0)
        {
            if (a[i] >= b[j])
            {
                if (i != 0)
                    diff += (a[i] - b[j]) + '0'; 
            }
            else
            {
                long long k = i - 1;
                while (!a[k])
                    k--;
                a[k]--;
                for (long long x = k; x > i; x--)
                    a[x]++;
                diff += 2 * '0' + 10 - b[j];
            }
        }
        else
            diff += a[i];
        i--;
        j--;
    }
    reverse(diff.begin(), diff.end());
    return diff;
}
```
