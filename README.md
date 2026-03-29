# pr6
Вариант 8.
Написать программу с реализацией собственной функции dot(A, B), которая
производит умножение двух матриц A и B. Обязательно проверить
соответствие размерности массивов.
#include <iostream>
using namespace std;

void dot(int** A, int** B, int** C, int n, int m, int k)
{
    for (int i = 0; i < n; i++)
        for (int j = 0; j < k; j++)
        {
            C[i][j] = 0;
            for (int t = 0; t < m; t++)
                C[i][j] += A[i][t] * B[t][j];
        }
}

int main()
{
    int n, m, p, k;

    cout << "Size A (n m): ";
    cin >> n >> m;

    cout << "Size B (p k): ";
    cin >> p >> k;

    if (m != p)
    {
        cout << "Multiplication of these matrices is not possible\n";
        return 0;
    }

    int** A = new int* [n];
    int** B = new int* [p];
    int** C = new int* [n];

    for (int i = 0; i < n; i++) A[i] = new int[m];
    for (int i = 0; i < p; i++) B[i] = new int[k];
    for (int i = 0; i < n; i++) C[i] = new int[k];

    cout << "A:\n";
    for (int i = 0; i < n; i++)
        for (int j = 0; j < m; j++)
            cin >> A[i][j];

    cout << "B:\n";
    for (int i = 0; i < p; i++)
        for (int j = 0; j < k; j++)
            cin >> B[i][j];

    dot(A, B, C, n, m, k);

    cout << "Result:\n";
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < k; j++)
            cout << C[i][j] << " ";
        cout << endl;
    }

    return 0;
    }

Дан текст. Найти в нем все номера телефонов. Номера телефонов начинаются
с цифры 8 и содержат ровно 11 цифр. Не использовать регулярные выражения.

#include <iostream>
#include <string>
using namespace std;

int main()
{
    string s;
    getline(cin, s);

    for (int i = 0; i < s.length(); i++)
    {
        if (s[i] == '8')
        {
            string num = "";
            int j = i;

            while (j < s.length() && s[j] >= '0' && s[j] <= '9')
            {
                num += s[j];
                j++;
            }

            if (num.length() == 11)
                cout << num << endl;
        }
    }

    return 0;
    }
