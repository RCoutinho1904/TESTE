#include <iomanip>
#include <iostream>
#include <fstream>
#include <cstring>
#include <ctime>
#include <cstdlib>
#include <string>
#include <conio.h>
#include<vector>
using namespace std;
struct bilhete
{
    int num_bilhete;
    char pais[1000];
    char continente[1000];
    char companhia[1000];
    char classe[1000];
    int dia;
    int mes;
}aeroporto_var;
void GerarHoraAliatoria(int hora, int minuto)
{
    srand(time(0));
    int hora = rand() % 24;
    int minuto = (rand() % 6) * 10;
    cout << "Hora do voo: " << setw(2) << setfill('0') << hora << ":"
        << setw(2) << setfill('0') << minuto << endl;
}
void gerarAssentosAleatorios(int numBilhetes, vector<string>& assentos) {
    for (int i = 0; i < numBilhetes; ++i) {
        int fila = rand() % 30 + 1;
        char coluna = 'A' + (rand() % 6);
        assentos[i] = "Fila " + to_string(fila) + ", Assento " + coluna;
    }
}
void exibirInformacoesBilhete(int numBilhetes, string assentos[], int hora, int minuto)
{
    cout << "\n+-----------------------------------------------------+" << endl;
    cout << "|                RESUMO DO(S) BILHETE(S)             |" << endl;
    cout << "+-----------------------------------------------------+" << endl;
    cout << "| Continente: " << setw(40) << left << aeroporto_var.continente << " |" << endl;
    cout << "| Companhia: " << setw(41) << left << aeroporto_var.companhia << " |" << endl;
    cout << "| Destino: " << setw(43) << left << aeroporto_var.pais << " |" << endl;
    cout << "| Data do voo: " << setw(36) << left<< to_string(aeroporto_var.dia) + "/" + to_string(aeroporto_var.mes) + "/2025"<< " |" << endl;
    cout << "| Hora do voo: " << setw(37) << left<< (to_string(hora) + ":" + (minuto < 10 ? "0" : "") + to_string(minuto))<< " |" << endl;
    cout << "| Classe: " << setw(43) << left<< (strcmp(aeroporto_var.classe, "executiva") == 0 ? "Executiva" : "Econômica")<< " |" << endl;
    cout << "+-----------------------------------------------------+" << endl;
    cout << "| Assentos Alocados:                                  |" << endl;

    for (int i = 0; i < numBilhetes; i++)
    {  
        cout << "|   Bilhete " << (i + 1) << ": " << setw(39) << left << assentos[i] << " |" << endl;
    }
    cout << "+-----------------------------------------------------+" << endl;
    cout << "\n";
    cout << "⠀⠀⠀⣖⠲⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⠉⡇⠀⠀⠀⠀⠀⠀⠀\n";
    cout << "⠀⠀⠀⠸⡆⠹⡀⣠⢤⡄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡏⠀⡧⢤⡄⠀⠀⠀⠀⠀\n";
    cout << "⠀⠀⠀⠀⡧⢄⣹⣅⣜⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⠁⠀⢹⠚⠃⠀⠀⠀⠀⠀\n";
    cout << "⠀⣀⠴⢒⣉⡹⣶⣤⣀⡉⠉⠒⠒⠒⠤⠤⣀⣀⣀⠇⠀⠀⢸⠠⣄⠀⠀⠀⠀⠀\n";
    cout << "⠀⠈⠉⠁⠀⠀⠀⠉⠒⠯⣟⣲⠦⣤⣀⡀⠀⠀⠈⠉⠉⠉⠛⠒⠻⢥⣀⠀⠀⠀\n";
    cout << "⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠙⣲⡬⠭⠿⢷⣦⣤⢄⣀⠀⠀⠚⠛⠛⠓⢦⡀\n";
    cout << "⠀⠀⠀⠀⠀⠀⠀⢀⣀⠤⠴⠚⠉⠁⠀⠀⠀⠀⣀⣉⡽⣕⣯⡉⠉⠉⠑⢒⣒⡾\n";
    cout << "⠀⠀⣀⡠⠴⠒⠉⠉⠀⢀⣀⣀⠤⡤⢶⣶⣋⠉⠉⠀⠀⠀⠈⠉⠉⠉⠉⠉⠁⠀\n";
    cout << "⣖⣉⣁⣠⠤⠶⡶⡶⢍⡉⠀⠀⠀⠙⠒⠯⠜⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀\n";
    cout << "⠀⠁⠀⠀⠀⠀⠑⢦⣯⠇\n";
}
bool realizarPagamento(double valorTotal) {
    cout << "\nValor total a pagar: " << fixed << setprecision(2) << valorTotal << " EUR" << endl;

    string senha = "";
    char ch;
    cout << "Digite a senha de 4 dígitos para confirmar o pagamento: ";

    // Captura os 4 caracteres da senha e os exibe como '*'
    for (int i = 0; i < 4; i++) {
        ch = _getch(); // Captura o caractere sem exibi-lo (usar getchar() no Linux/Mac)
        if (isdigit(ch)) { // Verifica se é um dígito
            senha += ch;    // Armazena o dígito real
            cout << "*";    // Exibe um asterisco
        }
        else {
            cout << "\nCaractere inválido! Digite apenas números." << endl;
            i--; // Regressa para que o caractere inválido não seja contado
        }
    }
    cout << endl;

    // Confirma o pagamento
    cout << "Pagamento confirmado! Compra concluída com sucesso." << endl;
    return true;
}
int main()
{
    setlocale(LC_ALL, "pt.UTF-8");
    int i;
    int s = 0, hora, minuto = 0;
    cout << "Bem vindo ao site do aeroporto de Simao&Ricardo." << endl;
    cout << "Voce dirigiu-se a uma maquina de bilhetes. Por favor digite 1 para iniciar o programa." << endl;
    cin >> i;
    system("cls");
    if (i == 1)
    {
        cout << "Indique o continente que deseja viajar.(Europa, Asia, Africa, America, Oceania)" << endl;
        cin >> aeroporto_var.continente;
        int continenteCode = -1;
        if (strcmp(aeroporto_var.continente, "Europa") == 0)
        {
            continenteCode = 1;
        }
        else if (strcmp(aeroporto_var.continente, "Asia") == 0)
        {
            continenteCode = 2;
        }
        else if (strcmp(aeroporto_var.continente, "Africa") == 0)
        {
            continenteCode = 3;
        }
        else if (strcmp(aeroporto_var.continente, "America") == 0)
        {
            continenteCode = 4;
        }
        else if (strcmp(aeroporto_var.continente, "Oceania") == 0)
        {
            continenteCode = 5;
        }
        switch (continenteCode)
        {
        case 1:
            cout << "As companhias disponiveis para a Europa sao: Easyjet, Emirates, Qatarairways, Tap, Ryanair, Flyone" << endl;
            cout << "Insira a companhia que deseja usar: " << endl;
            cin >> aeroporto_var.companhia;
            if (strcmp(aeroporto_var.companhia, "Easyjet") == 45)
            {
                cout << "Obrigado pela sua escolha da Easyjet!" << endl;
                cout << "Os paises que a companhia Easysjet se direciona sao: Espanha, Inglaterra, Franca, Alemanha, Italia, Grecia" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Espanha") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 45E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 100E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Inglaterra") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 45E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 100E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Franca") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 45E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 100E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Alemanha") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 45E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                }
                else if (strcmp(aeroporto_var.pais, "Italia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 45E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 100E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Grecia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 45E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 100E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            else if (strcmp(aeroporto_var.companhia, "Emirates") == 0)
            {
                cout << "Obrigado pela sua escolha da Emirates!" << endl;
                cout << "Os paises que a companhia Emirates se direciona sao: Espanha, Inglaterra, Franca, Alemanha, Italia, Grecia" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Espanha") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 750E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 1500E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Inglaterra") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 750E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 1500E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Franca") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 750E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 1500E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Alemanha") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 750E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 1500E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Italia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 750E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 1500E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Grecia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 750E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 1500E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            else if (strcmp(aeroporto_var.companhia, "Ryanair") == 0)
            {
                cout << "Obrigado pela sua escolha da Ryanair!" << endl;
                cout << "Os paises que a companhia Ryanair se direciona sao: Espanha, Inglaterra, Franca, Alemanha, Italia, Grecia" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Espanha") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 45E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 100E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Inglaterra") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 45E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 100E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Franca") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 45E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 100E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Alemanha") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 45E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 100E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Italia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 45E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 100E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Grecia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 45E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 100E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            else if (strcmp(aeroporto_var.companhia, "Tap") == 0)
            {
                cout << "Obrigado pela sua escolha da Tap!" << endl;
                cout << "Os paises que a companhia Tap se direciona sao: Espanha, Inglaterra, Franca, Alemanha, Italia, Grecia" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Espanha") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 180E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 240E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Inglaterra") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 180E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 240E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Franca") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 180E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 240E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Alemanha") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 180E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 240E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Italia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 180E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 240E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Grecia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 180E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 240E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            else if (strcmp(aeroporto_var.companhia, "Flyone") == 0)
            {
                cout << "Obrigado pela sua escolha da Flyone!" << endl;
                cout << "Os paises que a companhia Flyone se direciona sao: Espanha, Inglaterra, Franca, Alemanha, Italia, Grecia" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Espanha") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 350E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 420E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Inglaterra") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 350E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 420E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Franca") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 350E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 420E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Alemanha") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 350E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 420E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Italia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 350E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 420E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Grecia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 350E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 420E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            else if (strcmp(aeroporto_var.companhia, "Qatarairways") == 0)
            {
                cout << "Obrigado pela sua escolha da Qatarairways!" << endl;
                cout << "Os paises que a companhia Qatarairways se direciona sao: Espanha, Inglaterra, Franca, Alemanha, Italia, Grecia" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Espanha") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 750E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 1500E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Inglaterra") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 750E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 1500E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Franca") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 750E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 1500E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Alemanha") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 750E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 1500E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Italia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 750E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 1500E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Grecia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 750E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 1500E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            break;
        case 2:
            cout << "As companhias disponiveis para a Asia sao: Easyjet, Emirates, Qatarairways, Flyone, Tap" << endl;
            cout << "Insira a companhia que deseja usar." << endl;
            cin >> aeroporto_var.companhia;
            if (strcmp(aeroporto_var.companhia, "Easyjet") == 0)
            {
                cout << "Obrigado pela sua escolha da Easyjet!" << endl;
                cout << "Os paises que a companhia Easyjet se direciona sao : Turqui" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Turquia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 55E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 110E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            else if (strcmp(aeroporto_var.companhia, "Emirates") == 0)
            {
                cout << "Obrigado pela sua escolha da Emirates!" << endl;
                cout << "Os paises que a companhia Emirates se direciona sao: China, Japao, Taiwan, India, Turquia" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "China") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Japao") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Taiwan") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "India") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Turquia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            else if (strcmp(aeroporto_var.companhia, "Tap") == 0)
            {
                cout << "Obrigado pela sua escolha da Tap!" << endl;
                cout << "Os paises que a companhia Tap se direciona sao : Turqui" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Turquia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 180E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 300E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            else if (strcmp(aeroporto_var.companhia, "Flyone") == 0)
            {
                cout << "Obrigado pela sua escolha da Flyone!" << endl;
                cout << "Os paises que a companhia Flyone se direciona sao : Turqui" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Turquia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 375E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 500E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            else if (strcmp(aeroporto_var.companhia, "Qatarairways") == 0)
            {
                cout << "Obrigado pela sua escolha da Qatarairways!" << endl;
                cout << "Os paises que a companhia Qatarairways se direciona sao: China, Japao, Taiwan, India, Turquia" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "China") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Japao") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Taiwan") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "India") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2000E." << endl;
                    cin >> aeroporto_var.classe;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Turquia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            break;
        case 3:
            cout << "As companhias disponiveis para a Africa sao: Easyjet, Emirates, Qatarairways, Rayaniar, Tap" << endl;
            cout << "Insira a companhia que deseja usar." << endl;
            cin >> aeroporto_var.companhia;
            if (strcmp(aeroporto_var.companhia, "Easyjet") == 0)
            {
                cout << "Obrigado pela sua escolha da Easyjet!" << endl;
                cout << "Os paises que a companhia Easyjet se direciona sao: Marrocos" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Marrocos") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 50E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 120E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            else if (strcmp(aeroporto_var.companhia, "Emirates") == 0)
            {
                cout << "Obrigado pela sua escolha da Emirates!" << endl;
                cout << "Os paises que a companhia Emirates se direciona sao: Mocambique, Nigeria, Marrocos, Angola" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Mocambique") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2050E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Nigeria") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2050E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Marrocos") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2050E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Angola") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2050E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            else if (strcmp(aeroporto_var.companhia, "Ryanair") == 0)
            {
                cout << "Obrigado pela sua escolha da Ryanair!" << endl;
                cout << "Os paises que a companhia Ryanair se direciona sao: Marrocos" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Marrocos") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 60E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 130E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            else if (strcmp(aeroporto_var.companhia, "Tap") == 0)
            {
                cout << "Obrigado pela sua escolha da Tap!" << endl;
                cout << "Os paises que a companhia Tap se direciona sao: Mocambique, Angola" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Mocambique") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 190E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 400E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Angola") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 190E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 400E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            else if (strcmp(aeroporto_var.companhia, "Qatarairways") == 0)
            {
                cout << "Obrigado pela sua escolha da Qatarairways!" << endl;
                cout << "Os paises que a companhia Qatarairways se direciona sao: Mocambique, Nigeria, Marrocos, Madagascar, Angola" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Mocambique") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2050E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Nigeria") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2050E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Marrocos") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2050E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Madagascar") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2050E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Angola") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 950E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 2050E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            break;
        case 4:
            cout << "As companhias disponiveis para a America sao: Emirates, Tap, Qatarairways" << endl;
            cout << "Insira a companhia que deseja usar." << endl;
            cin >> aeroporto_var.companhia;
            if (strcmp(aeroporto_var.companhia, "Emirates") == 0)
            {
                cout << "Obrigado pela sua escolha da Emirates!" << endl;
                cout << "Os paises que a companhia Emirates se direciona sao: Estados_Unidos, Canada, Brasil" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Estados_Unidos") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 1000E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 3000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Canada") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 1000E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 3000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Brasil") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 1000E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 3000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            else if (strcmp(aeroporto_var.companhia, "Tap") == 0)
            {
                cout << "Obrigado pela sua escolha da Tap!" << endl;
                cout << "Os paises que a companhia Tap se direciona sao: Estados_Unidos, Canada, Brasil, Argentina" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Estados_Unidos") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 400E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 600E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Canada") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 400E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 600E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Brasil") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 400E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 600E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Argentina") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 400E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 600E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            else if (strcmp(aeroporto_var.companhia, "Qatarairways") == 0)
            {
                cout << "Obrigado pela sua escolha da Qatarairways!" << endl;
                cout << "Os paises que a companhia Qatarairways se direciona sao: Estados_Unidos, Canada, Brasil, Argentina" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Estados_Unidos") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 1000E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 3000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Canada") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 1000E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 3000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Brasil") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 1000E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 3000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Argentina") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 1000E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 3000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            break;
        case 5:
            cout << "As companhias disponiveis para a Oceania sao: Emirates, Qatarairways" << endl;
            cout << "Insira a companhia que deseja usar." << endl;
            cin >> aeroporto_var.companhia;
            if (strcmp(aeroporto_var.companhia, "Emirates") == 0)
            {
                cout << "Obrigado pela sua escolha da Emirates!" << endl;
                cout << "Os paises que a companhia Emirates se direciona sao: Australia, Nova Zelandia" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Australia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 1600E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 4000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Nova Zelandia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 1600E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 4000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
            }
            else if (strcmp(aeroporto_var.companhia, "Qatarairways") == 0)
            {
                cout << "Obrigado pela sua escolha da Qatarairways!" << endl;
                cout << "Os paises que a companhia Qatarairways se direciona sao: Australia, Nova Zelandia" << endl;
                cout << "Escolha o pais que desaja viajar proporcionado pela companhia que escolheu: " << endl;
                cin >> aeroporto_var.pais;
                if (strcmp(aeroporto_var.pais, "Australia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 1600E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 4000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende ir." << endl;
                    }
                }
                else if (strcmp(aeroporto_var.pais, "Nova Zelandia") == 0)
                {
                    cout << "Obrigada pela sua escolha" << endl;
                    cout << "O preco do(s) bilhete(s) e 1600E por pessoa.";
                    cout << " Quantos bilhete(s) deseja?" << endl;
                    cin >> aeroporto_var.num_bilhete;
                    cout << "Que classe de voo voce pretende utilizar, classe executiva ou economica.(executiva - 1; economica - 2)" << endl;
                    cout << "O preco da classe executiva e 4000E." << endl;
                    cin >> s;
                    if (s == 1)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende irr." << endl;
                    }
                    else if (s == 2)
                    {
                        cout << "Obrigado pela sua escolha.";
                        cout << "Por favor indique o dia em que pretende irr." << endl;
                    }
                }
            }
            break;
        default:
            cout << "Nao existe nenhum continente com esse nome." << endl;
            break;
            return 0;
        }
        cout << "Selecione o mes da viagem (1-12): ";
        cin >> aeroporto_var.mes;
        while (aeroporto_var.mes < 1 || aeroporto_var.mes > 12)
        {
            cout << "Mes invalido!! Digite novamente (1-12): ";
            cin >> aeroporto_var.mes;
        }
        cout << "Selecione o dia da viagem (1-30): ";
        cin >> aeroporto_var.dia;
        while (aeroporto_var.dia < 1 || aeroporto_var.dia  > 30)
        {
            cout << "Dia invalido!! Digite novamente (1-30): ";
            cin >> aeroporto_var.dia;
        }
        GerarHoraAliatoria(hora, minuto);

        string assentos[aeroporto_var.num_bilhete];
       
        gerarAssentosAleatorios(aeroporto_var.num_bilhete, assentos);
        exibirInformacoesBilhete(aeroporto_var.num_bilhete, assentos, hora, minuto);
   
    }
    else
    {
        cout << "Opcao invalida!! Por favor refassa a sua escolha." << endl;
    }


}
