---
title: Math Project
date: 2025-01-02
categories: Project
tags: [Python]
image:
    path: assets\kokomi-removebg-preview.jpg
---

# My Math Project
Hello everyone, I'm Aristo from Ciputra Makassar Univercity. In this side I will show you my littel helper that can solve a simpel Matrix problem. In this project I use python to make the code. This program can run for Matrix 2x2 to Matrix 4x4. Next I will show all of you the rest of the coding that I made.

```python
import os
import time

def create_matrix(rows, cols):
    matrix = []
    print("Masukkan elemen matriks satu per satu:")
    for i in range(rows):
        row = []
        for j in range(cols):
            while True:
                try:
                    value = float(input(f"Masukkan elemen [{i+1}, {j+1}]: "))
                    row.append(value)
                    break
                except ValueError:
                    print("Input harus berupa angka. Coba lagi.")
        matrix.append(row)
    return matrix

def display_matrix(matrix):
    for row in matrix:
        print("\t".join(map(lambda x: f"{x:.2f}", row)))

def add_matrices(matrix1, matrix2):
    rows = len(matrix1)
    cols = len(matrix1[0])
    result = []
    for i in range(rows):
        row = []
        for j in range(cols):
            row.append(matrix1[i][j] + matrix2[i][j])
        result.append(row)
    return result

def subtract_matrices(matrix1, matrix2):
    rows = len(matrix1)
    cols = len(matrix1[0])
    result = []
    for i in range(rows):
        row = []
        for j in range(cols):
            row.append(matrix1[i][j] - matrix2[i][j])
        result.append(row)
    return result

def multiply_matrices(matrix1, matrix2):
    rows1 = len(matrix1)
    cols1 = len(matrix1[0])
    rows2 = len(matrix2)
    cols2 = len(matrix2[0])

    if cols1 != rows2:
        print("Matriks tidak dapat dikalikan. Jumlah kolom matriks pertama harus sama dengan jumlah baris matriks kedua.")
        return None

    result = []
    for i in range(rows1):
        row = []
        for j in range(cols2):
            value = sum(matrix1[i][k] * matrix2[k][j] for k in range(cols1))
            row.append(value)
        result.append(row)
    return result

def transpose_matrix(matrix):
    return [[matrix[j][i] for j in range(len(matrix))] for i in range(len(matrix[0]))]

def determinant_recursive(mat):
    if len(mat) == 1:
        return mat[0][0]
    if len(mat) == 2:
        return mat[0][0] * mat[1][1] - mat[0][1] * mat[1][0]

    det = 0
    for col in range(len(mat)):
        minor = [row[:col] + row[col+1:] for row in mat[1:]]
        det += ((-1) ** col) * mat[0][col] * determinant_recursive(minor)
    return det

def cofactor_matrix(matrix):
    size = len(matrix)
    cofactors = []

    for r in range(size):
        cofactor_row = []
        for c in range(size):
            minor = [row[:c] + row[c+1:] for row in (matrix[:r] + matrix[r+1:])]
            cofactor_row.append(((-1) ** (r + c)) * determinant_recursive(minor))
        cofactors.append(cofactor_row)
    return cofactors

def inverse_matrix(matrix):
    det = determinant_recursive(matrix)
    if det == 0 or det is None:
        time.sleep(1)
        os.system('cls')
        print("Invers tidak dapat dihitung untuk matriks dengan determinan 0.")
        return None

    cofactors = cofactor_matrix(matrix)
    adjoint = transpose_matrix(cofactors)
    inverse = [[adjoint[r][c] / det for c in range(len(matrix))] for r in range(len(matrix))]
    return inverse

if __name__ == "__main__":
    try:
        print("Pilih operasi yang ingin dilakukan:")
        print("1. Penjumlahan Matriks")
        print("2. Pengurangan Matriks")
        print("3. Perkalian Matriks")
        print("4. Determinan Matriks")
        print("5. Invers Matriks")
        choice = int(input("Masukkan pilihan (1-5): "))
        time.sleep(1)
        os.system('cls')

        if choice in [1, 2, 3]:
            rows1 = int(input("Masukkan jumlah baris matriks pertama: "))
            cols1 = int(input("Masukkan jumlah kolom matriks pertama: "))
            print("Matriks pertama:")
            matrix1 = create_matrix(rows1, cols1)

            time.sleep(0.5)
            os.system('cls')

            rows2 = int(input("Masukkan jumlah baris matriks kedua: "))
            cols2 = int(input("Masukkan jumlah kolom matriks kedua: "))
            print("Matriks kedua:")
            matrix2 = create_matrix(rows2, cols2)

            time.sleep(0.5)
            os.system('cls')

            if choice == 1:
                if rows1 == rows2 and cols1 == cols2:
                    time.sleep(1)
                    os.system('cls')
                    print("Hasil Penjumlahan Matriks:")
                    display_matrix(add_matrices(matrix1, matrix2))
                else:
                    time.sleep(1)
                    os.system('cls')
                    print("Matriks harus memiliki ukuran yang sama untuk dijumlahkan.")

            elif choice == 2:
                if rows1 == rows2 and cols1 == cols2:
                    time.sleep(1)
                    os.system('cls')
                    print("Hasil Pengurangan Matriks:")
                    display_matrix(subtract_matrices(matrix1, matrix2))
                else:
                    time.sleep(1)
                    os.system('cls')
                    print("Matriks harus memiliki ukuran yang sama untuk dikurangkan.")

            elif choice == 3:
                result = multiply_matrices(matrix1, matrix2)
                if result:
                    time.sleep(1)
                    os.system('cls')
                    print("Hasil Perkalian Matriks:")
                    display_matrix(result)

        elif choice == 4:
            rows = int(input("Masukkan ukuran matriks persegi (baris = kolom): "))
            matrix = create_matrix(rows, rows)
            det = determinant_recursive(matrix)
            time.sleep(1)
            os.system('cls')
            print(f"Determinan Matriks: {det:.2f}")

        elif choice == 5:
            rows = int(input("Masukkan ukuran matriks persegi (baris = kolom): "))
            matrix = create_matrix(rows, rows)
            inv = inverse_matrix(matrix)
            if inv:
                time.sleep(1)
                os.system('cls')
                print("Invers Matriks:")
                display_matrix(inv)

        else:
            time.sleep(1)
            os.system('cls')
            print("Pilihan tidak valid.")

    except ValueError:
        time.sleep(1)
        os.system('cls')
        print("Input harus berupa angka.")
```