# TIc-Tac-Toe
//Podstawowa gra w kółko i krzyżyk
#include <iostream>
using namespace std;


void showWinner(char im[]);
char ToSymbol(int value);

int main()
{
    char im1[20], im2[20];
    int gra[3][3], kol, wier, count = 0;
    bool Firstplayer = true, End = false;

    for (int i = 0; i < 3; i++)
    {
        for (int ii = 0; ii < 3; ii++)
        {
            gra[i][ii] = 0;
        }
    }
  

    cout << "Gra w kolko i krzyzyk\nPodaj imona graczy\nGracz 1:";
    cin.getline(im1, 19);
    cout << "Gracz2:";
    cin.getline(im2, 19);

    while (End == false)
    {
        cout << "\n";
        for (int i = 0; i < 5; i++)
        {
            for (int ii = 0; ii < 9; ii++)
            {
                if (i == 0)
                {
                    if (ii < 3 || ii == 4 || ii == 6)
                    {
                        cout << " ";
                    }
                    else if (ii == 3)
                    {
                        cout << "1";
                    }
                    else if (ii == 5)
                    {
                        cout << "2";
                    }
                    else if (ii == 7)
                    {
                        cout << "3";
                    }
                }
                if (i == 1)
                {
                    if (ii < 3 || ii == 4 || ii == 6 || ii == 8)
                    {
                        cout << " ";
                    }
                    else
                    {
                        cout << "_";
                    }
                }
                if (i == 2)
                {
                    if (ii == 0)
                    {
                        cout << "1";
                    }
                    else if (ii == 1)
                    {
                        cout << " ";
                    }
                    else if (ii == 3)
                    {
                        cout << ToSymbol(gra[0][0]);
                    }
                    else if (ii == 5)
                    {
                        cout << ToSymbol(gra[0][1]);
                    }
                    else if (ii == 7)
                    {
                        cout << ToSymbol(gra[0][2]);
                    }
                    else
                    {
                        cout << "|";
                    }
                }
                if (i == 3)
                {
                    if (ii == 0)
                    {
                        cout << "2";
                    }
                    else if (ii == 1)
                    {
                        cout << " ";
                    }
                    else if (ii == 3)
                    {
                        cout << ToSymbol(gra[1][0]);
                    }
                    else if (ii == 5)
                    {
                        cout << ToSymbol(gra[1][1]);
                    }
                    else if (ii == 7)
                    {
                        cout << ToSymbol(gra[1][2]);
                    }
                    else
                    {
                        cout << "|";
                    }
                }
                if (i == 4)
                {
                    if (ii == 0)
                    {
                        cout << "3";
                    }
                    else if (ii == 1)
                    {
                        cout << " ";
                    }
                    else if (ii == 3)
                    {
                        cout << ToSymbol(gra[2][0]);
                    }
                    else if (ii == 5)
                    {
                        cout << ToSymbol(gra[2][1]);
                    }
                    else if (ii == 7)
                    {
                        cout << ToSymbol(gra[2][2]);
                    }
                    else
                    {
                        cout << "|";
                    }
                }
            }
            cout << "\n";
        }
        if (Firstplayer == true)
        {
            cout << "Gracz " << im1 << " wybiera wiersz: ";
            cin >> wier;
            if (wier < 1)
            {
                wier = 1;
            }
            else if (wier > 3)
            {
                wier = 3;
            }
            cout << "\nGracz " << im1 << " wybiera kolumne: ";
            cin >> kol;
            if (kol < 1)
            {
                kol = 1;
            }
            else if (kol > 3)
            {
                kol = 3;
            }
            if (gra[wier - 1][kol - 1] == 0)
            {
                gra[wier - 1][kol - 1] = 1;
                Firstplayer = false;
                if (gra[wier - 1][0] == 1 && gra[wier - 1][1] == 1 && gra[wier - 1][2] == 1)
                {
                    showWinner(im1);
                    End = true;
                }
                else if (gra[0][kol - 1] == 1 && gra[1][kol - 1] == 1 && gra[2][kol - 1] == 1)
                {
                    showWinner(im1);
                    End = true;
                }
                else if (gra[0][0] == 1)
                {
                    if (gra[1][1] == 1 && gra[2][2] == 1)
                    {
                        showWinner(im1);
                        End = true;
                    }
                }
                else if (gra[0][2] == 1)
                {
                    if (gra[1][1] == 1 && gra[2][0] == 1)
                    {
                        showWinner(im1);
                        End = true;
                    }
                }
            }
            else
            {
                cout << "\n Wybrales juz zajeta komorke wybierz ponownie\n";
                continue;
            }
        }
        else
        {
            cout << "Gracz " << im2 << " wybiera wiersz: ";
            cin >> wier;
            if (wier < 1)
            {
                wier = 1;
            }
            else if (wier > 3)
            {
                wier = 3;
            }
            cout << "\nGracz " << im2 << " wybiera kolumne: ";
            cin >> kol;
            if (kol < 1)
            {
                kol = 1;
            }
            else if (kol > 3)
            {
                kol = 3;
            }
            if (gra[wier - 1][kol - 1] == 0)
            {
                count++;
                gra[wier - 1][kol - 1] = 2;
                Firstplayer = true;
                if (gra[wier - 1][0] == 2 && gra[wier - 1][1] == 2 && gra[wier - 1][2] == 2)
                {
                    showWinner(im2);
                    End = true;
                }
                else if (gra[0][kol - 1] == 2 && gra[1][kol - 1] == 2 && gra[2][kol - 1] == 2)
                {
                    showWinner(im2);
                    End = true;
                }
                else if (gra[0][0] == 2)
                {
                    if (gra[1][1] == 2 && gra[2][2] == 2)
                    {
                        showWinner(im2);
                        End = true;
                    }
                }
                else if (gra[0][2] == 2)
                {
                    if (gra[1][1] == 2 && gra[2][0] == 2)
                    {
                        showWinner(im2);
                        End = true;
                    }
                }
            }
            else
            {
                cout << "\n Wybrales juz zajeta komorke wybierz ponownie\n";
                continue;
            }

            if (count == 9)
            {
                cout << "Pelna plansza. Remis!\n";
                End = true;
            }
        }

    }
    cout << "\nPlansza na koniec wyglada o tak:\n";
    for (int i = 0; i < 5; i++)
    {
        for (int ii = 0; ii < 9; ii++)
        {
            if (i == 0)
            {
                if (ii < 3 || ii == 4 || ii == 6)
                {
                    cout << " ";
                }
                else if (ii == 3)
                {
                    cout << "1";
                }
                else if (ii == 5)
                {
                    cout << "2";
                }
                else if (ii == 7)
                {
                    cout << "3";
                }
            }
            if (i == 1)
            {
                if (ii < 3 || ii == 4 || ii == 6 || ii == 8)
                {
                    cout << " ";
                }
                else
                {
                    cout << "_";
                }
            }
            if (i == 2)
            {
                if (ii == 0)
                {
                    cout << "1";
                }
                else if (ii == 1)
                {
                    cout << " ";
                }
                else if (ii == 3)
                {
                    cout << ToSymbol(gra[0][0]);
                }
                else if (ii == 5)
                {
                    cout << ToSymbol(gra[0][1]);
                }
                else if (ii == 7)
                {
                    cout << ToSymbol(gra[0][2]);
                }
                else
                {
                    cout << "|";
                }
            }
            if (i == 3)
            {
                if (ii == 0)
                {
                    cout << "2";
                }
                else if (ii == 1)
                {
                    cout << " ";
                }
                else if (ii == 3)
                {
                    cout << ToSymbol(gra[1][0]);
                }
                else if (ii == 5)
                {
                    cout << ToSymbol(gra[1][1]);
                }
                else if (ii == 7)
                {
                    cout << ToSymbol(gra[1][2]);
                }
                else
                {
                    cout << "|";
                }
            }
            if (i == 4)
            {
                if (ii == 0)
                {
                    cout << "3";
                }
                else if (ii == 1)
                {
                    cout << " ";
                }
                else if (ii == 3)
                {
                    cout << ToSymbol(gra[2][0]);
                }
                else if (ii == 5)
                {
                    cout << ToSymbol(gra[2][1]);
                }
                else if (ii == 7)
                {
                    cout << ToSymbol(gra[2][2]);
                }
                else
                {
                    cout << "|";
                }
            }
        }
        cout << "\n";
    }
    return 0;
}

void showWinner(char im[])
{
    cout << "\nGracz " << im << " zwycieza! Brawo";
}

char ToSymbol(int value)
{
    if (value == 0)
    {
        return '_';
    }
    else if (value == 1)
    {
        return 'O';
    }
    else if (value == 2)
    {
        return 'X';
    }

}
