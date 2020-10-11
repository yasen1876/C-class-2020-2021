//NAME: Yasen Alchev
//CLASS: 11v
//NUMBER: 25

#include <iostream>
#include <stdio.h>
using namespace std;

const int N =50;

void print(int A[][N], int n, int m);
bool equal_fn(int A[][N],int m1, int n1, int B[][N],int m2, int n2);
void sum_fn(int A[][N], int B[][N], int C[][N], int m, int n);
void transpose_fn(int A[][N], int B[][N], int m, int n);
void sMult(int A[][N], int R[][N], int m, int n, int s);
void sub(int A[][N], int B[][N], int C[][N], int m, int n);

int main()
{
    int A[3][N] = {{12, 64, -34},
                    {-234, 12, 823},
                    {657, 283, -123}};
    int B[3][N] = {{31, 46, 67},
                    {81, 19, 34},
                    {0, 3, -12}};
    int C[3][N] = {{0}};

    print(A ,3 ,3);
    printf("%d\n",equal_fn(A,3,3,A,3,3));
    printf("%d\n",equal_fn(A,3,3,B,3,3));
    sum_fn(A, B, C, 3, 3);
    transpose_fn(B, C, 3, 3);
    sMult(B, C, 3, 3, -2);
    sub(A, B, C, 3, 3);
    return 0;
}

void print(int A[][N], int n, int m)
{
    for(int i=0; i<n; i++)
    {
        printf("    { ");
        for(int j=0; j<m; j++)
        {
            printf("%d ",A[i][j]);
        }
        printf("} ");
        printf("\n");
    }
    printf("\n");
}

bool equal_fn(int A[][N],int m1, int n1, int B[][N],int m2, int n2)
{
    if((m1 != m2) || (n1 != n2))
    {
        return false;
    }
    for(int i=0; i<m1; i++)
    {
        for(int j=0; j<n1; j++)
        {
            if(A[i][j] != B[i][j])
            {
                return false;
            }
        }
    }
    return true;
}

void sum_fn(int A[][N], int B[][N], int C[][N], int m, int n)
{
    printf("Summed:\n");
    for(int i=0; i<m; i++)
    {
        for(int j=0; j<n; j++)
        {
            C[i][j] = A[i][j] + B[i][j];
        }
    }
    print(C, m, n);
}

void transpose_fn(int A[][N], int B[][N], int m, int n)
{
    printf("Transposed:\n");
    for(int i=0; i<m; i++)
    {
        for(int j=0; j<n; j++)
        {
            B[i][j] = A[j][i];
        }
    }
    print(B, m, n);
}

void sMult(int A[][N], int R[][N], int m, int n, int s)
{
    printf("Multiplied by a number:\n");
    for(int i=0; i<m; i++)
    {
        for(int j=0; j<n; j++)
        {
            R[i][j] = A[i][j] * s;
        }
    }
    print(R, m, n);
}

void sub(int A[][N], int B[][N], int C[][N], int m, int n)
{
    printf("--------sub_----------\n");
    sMult(B, B, m, n, -1);
    sum_fn(A, B, C, m, n);
    printf("-----------after_all_actions-------------\n");
    print(C, m, n);
}

