---
title: Game Project
date: 2024-11-24
categories: Project
tags: [Python]     # TAG names should always be lowercase
image:
    path: assets\Paimon-removebg-preview.jpg
---

# My First Game Project
Hello everyone, I'm Aristo from Ciputra Makassar Univercity. In this side I will show you my littel project that I made by my self. To make this littel project I'm use Python as my programer language. This project it's a game that can play by two player. The objective of this game is to guess the other player word. If the player can guess the word, they will got a score to win the game and defeat the other player. Next I will show all of you the rest of the coding that I made.

```python
import os
import time

class Permainan:
    def __init__(self):
        self.petunjuk1 = []
        self.score1 = 0
        self.petunjuk2 = []
        self.score2 = 0

    def bantuan(self, petunjuk_list):
        petunjuk = input("Pemberi kata masukkan petunjuk dari kata yang ingin ditebak: ")
        petunjuk_list.append(petunjuk)
        time.sleep(0.5)
        os.system('cls')
        for A in petunjuk_list:
            print(f"Petunjuk saat ini: {A}")
        return -5  

    def berhasil(self, kata, score, petunjuk_list):
        print(f"Berhasil menebak kata {kata}!")
        petunjuk_list.clear()
        return score + 20

    def menyerah(self, kata, score, petunjuk_list):
        print(f"Tidak berhasil menebak kata. Kata yang benar adalah '{kata}'")
        petunjuk_list.clear()
        return score - 20

game = Permainan()
os.system('cls')

jumlah_ronde = int(input("Masukkan jumlah ronde yang ingin dimainkan: "))
os.system('cls')

for ronde in range(1, jumlah_ronde + 1):
    print(f"--- Ronde {ronde} ---")
    time.sleep(1)

    kata1 = input("Pemain 1, masukkan kata yang ingin ditebak: ").lower()
    time.sleep(1)
    os.system('cls')
    kesempatan = 3

    while kesempatan > 0:
        tebak1 = input("Pemain 2, masukkan tebakan kata: ").lower()
        time.sleep(1)

        if tebak1 == kata1:
            game.score2 = game.berhasil(kata1, game.score2, game.petunjuk1)
            time.sleep(2)
            os.system('cls')
            break

        else:
            kesempatan -= 1
            print(f"Tebakan salah! Kesempatan tersisa: {kesempatan}")
            print("\n")

            if kesempatan > 0:
                print("Pilih opsi:")
                print("1. Minta Bantuan")
                print("2. Menebak Lagi")
                print("3. Menyerah")

                pilihan = input("Masukkan pilihan (1-3): ")
                time.sleep(1)
                os.system('cls')

                if pilihan == "1":
                    game.score2 += game.bantuan(game.petunjuk1)  
                elif pilihan == "3":
                    game.score2 = game.menyerah(kata1, game.score2, game.petunjuk1)
                    break

    kata2 = input("Pemain 2, masukkan kata yang ingin ditebak: ").lower()
    time.sleep(1)
    os.system('cls')
    kesempatan = 3

    while kesempatan > 0:
        tebak2 = input("Pemain 1, masukkan tebakan kata: ").lower()
        time.sleep(1)

        if tebak2 == kata2:
            game.score1 = game.berhasil(kata2, game.score1, game.petunjuk2)
            time.sleep(2)
            os.system('cls')
            break
        else:
            kesempatan -= 1
            print(f"Tebakan salah! Kesempatan tersisa: {kesempatan}")
            print("\n")
            if kesempatan > 0:
                print("Pilih opsi:")
                print("1. Minta Bantuan")
                print("2. Menebak Lagi")
                print("3. Menyerah")

                pilihan = input("Masukkan pilihan (1-3): ")
                time.sleep(1)
                os.system('cls')

                if pilihan == "1":
                    game.score1 += game.bantuan(game.petunjuk2) 
                elif pilihan == "3":
                    game.score1 = game.menyerah(kata2, game.score1, game.petunjuk2)
                    break

os.system('cls')
print("--- Skor Akhir ---")
print(f"Skor Pemain 1: {game.score1}")
print(f"Skor Pemain 2: {game.score2}")
print("\n")

if game.score1 > game.score2:
    print("Pemain 1 menang!")
elif game.score2 > game.score1:
    print("Pemain 2 menang!")
else:
    print("Permainan berakhir seri!")
```