<h1 align="center"> Big Integers For C++ </h1>
<p align="center"> As in C++, there is no any <b>Big Integer</b> datatype as it exists only on Java and Python so I made these implementions for C++. <br/>This repository contains all the operations of <b>Big Integer</b> for C++. </p>
<p align="center"> As in C++ we can store atmost <b>2e18 (2 x 10^18)</b> on <b>long long int</b> so for more than 2e18 we can implement a string or an array.
    
    
---

<h2 align="center"> Addition/Substraction of Big Integers </h2>

- A Boolean Type Function to check whether fist string is smaller than second or not.

```

bool isFirstSmall(string a, string b)
{
    if ((long long)a.size() > (long long)b.size())
        return false;
    else if ((long long)a.size() < (long long)b.size())
        return true;
    else if ((long long)a.size() == (long long)b.size())
    {
        for (long long i = 0; i < (long long)a.size(); i++)
        {
            if (a[i] != b[i])
            {
                if (a[i] < b[i])
                    return true;
                return false;;
            }
        }
    }
    return false;
}

```

- A Function to return the addition of a and b where a is greater than b.

```
string Add_Num(string a, string b)
{
    string sum = "";
    long long i = (long long)a.size() - 1;
    long long j = (long long)b.size() - 1;
    long long temp_sum = 0;
    while (i >= 0 or j >= 0)
    {
        temp_sum += (a[i] - '0') * (i >= 0) + (b[j] - '0') * (j >= 0);
        sum += '0' + (temp_sum % 10);
        temp_sum /= 10;
        i--;
        j--;
    }
    while (temp_sum)
    {
        sum += '0' + (temp_sum % 10);
        temp_sum /= 10;
    }
    reverse(sum.begin(), sum.end());
    return sum;
}

```
- A Function to return the substraction of a and b where a is greater than b.

```
string Sub_Num(string a, string b)
{
    if (a == b)
        return "0";
    string diff = "";
    long long i = (long long)a.size() - 1;
    long long j = (long long)b.size() - 1;
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
                while (a[k] == '0')
                    k--;
                a[k]--;
                for (long long x = k + 1; x < i; x++)
                    a[x] = '9';
                diff += 2 * '0' + 10 - b[j];
            }
        }
        else
        {
            if (i == 0 and a[i] == '0')
                break;
            diff += a[i];
        }
        i--;
        j--;
    }
    reverse(diff.begin(), diff.end());
    return diff;
}

```
- A Function to return the addition/substraction of a and b.

```
string AddorSub(string a, string b)
{
    string res = "";
    if (a[0] == '-' and b[0] == '-')
    {
        a = a.substr(1, (long long)a.size() - 1);
        b = b.substr(1, (long long)b.size() - 1);
        res += '-';
    }
    if (a[0] == '-' or b[0] == '-')
    {
        if (a[0] == '-')
        {
            a = a.substr(1, (long long)a.size() - 1);
            if (isFirstSmall(a, b))
                res += Sub_Num(b, a);
            else
                res = '-' + Sub_Num(a, b);
        }
        else
        {
            b = b.substr(1, (long long)b.size() - 1);
            if (isFirstSmall(b, a))
                res += Sub_Num(a, b);
            else
                res = '-' + Sub_Num(b, a);
        }
    }
    else
    {
        if (isFirstSmall(a, b))
            res += Add_Num(b, a);
        else
            res += Add_Num(a, b);
    }
    return res;
}

```
