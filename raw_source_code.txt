#include <iostream>

using namespace std;

/**
 * Die Funktion testet, ob das angegebene Jahr ein Schaltjahr ist, oder nicht.
 * @param jahr Jahreszahl (ab Geburt Christi)
 * @return true/false, jenachdem ob es ein Schaltjahr ist oder nicht.
 */
bool schaltjahr(int jahr){
    //Die drei Bedingungen, die erfüllt sein müssen damit ein
    //Jahr ein Schaltjahr ist, sind:
    // (1)Die Jahreszahl ist restlos durch 4 teilbar.
    // (2)Die Jahreszahl ist restlos durch 100 teilbar.
    // (3)Die Jahreszahl ist restlos durch 400 teilbar.
    //Da alle Bedingungen zutreffen müssen, werden sie
    //im if-Statement mit dem logischen UND-Operator ('&&') verknüpft.
    if (jahr % 4 == 0 && jahr % 100 == 0 && jahr % 400 == 0){
        return true;
    }
    else{
        return false;
    }
}

/**
 * Gibt die Tageslänge als String aus. In diesem Fall als hässliches Switch-Case-LookUp, mit
 * hart codierten Werten.
 * @param monat der Monat der überprüft wird
 * @param jahr das Jahr das überprüft wird
 */
void tageslaenge_alt(int monat, int jahr){
    if (schaltjahr(jahr)){
        //Sollte das übergebene Jahr ein Schaltjahr sein, so
        //wird der Monat in diesem Switch-Case verfahren gesucht
        //und der jeweilige Text ausgegeben.
        switch (monat) {
            case 1: cout << "Der Monat Januar hat 31 Tage\n";
                break;
            case 2: cout << "Der Monat Februar hat 29 Tage\n";
                break;
            case 3: cout << "Der Monat März hat 31 Tage\n";
                break;
            case 4: cout << "Der Monat April hat 30 Tage\n";
                break;
            case 5: cout << "Der Monat Mai hat 31 Tage\n";
                break;
            case 6: cout << "Der Monat Juni hat 30 Tage\n";
                break;
            case 7: cout << "Der Monat Juli hat 31 Tage\n";
                break;
            case 8: cout << "Der Monat August hat 31 Tage\n";
                break;
            case 9: cout << "Der Monat September hat 30 Tage\n";
                break;
            case 10: cout << "Der Monat Oktober hat 31 Tage\n";
                break;
            case 11: cout << "Der Monat November hat 30 Tage\n";
                break;
            case 12: cout << "Der Monat Dezember hat 31 Tage\n";
                break;
            default: cout << "Ungültiger Monat!";
        }
    }
    //So wie oben, nur dass das Jahr KEIN Schaltjahr ist, und sich
    //somit der Text für den Februar ändert. Alles andere bleibt gleich.
    else{
        //februar mit 28 Tagen
        switch (monat) {
            case 1: cout << "Der Monat Januar hat 31 Tage\n";
                break;
            case 2: cout << "Der Monat Februar hat 28 Tage\n";
                break;
            case 3: cout << "Der Monat März hat 31 Tage\n";
                break;
            case 4: cout << "Der Monat April hat 30 Tage\n";
                break;
            case 5: cout << "Der Monat Mai hat 31 Tage\n";
                break;
            case 6: cout << "Der Monat Juni hat 30 Tage\n";
                break;
            case 7: cout << "Der Monat Juli hat 31 Tage\n";
                break;
            case 8: cout << "Der Monat August hat 31 Tage\n";
                break;
            case 9: cout << "Der Monat September hat 30 Tage\n";
                break;
            case 10: cout << "Der Monat Oktober hat 31 Tage\n";
                break;
            case 11: cout << "Der Monat November hat 30 Tage\n";
                break;
            case 12: cout << "Der Monat Dezember hat 31 Tage\n";
                break;
            default: cout << "Ungültiger Monat!";
        }
    }
}


/**
 * Gibt die Tageslänge als String aus. In diesem Fall etwas komplexer, indem über
 * zwei Arrays iteriert wird, um festzustellen, ob ein Monat 30 oder 31 Tage hat.
 * @param monat der Monat der überprüft wird
 * @param jahr das Jahr das überprüft wird
 */
void tageslaenge_neu(int monat, int jahr){
    //Initialisiert zwei Arrays. In einem sind die Zahlen der
    //Monate mit 31 Tagen hinterlegt, im anderen die mit 30.
    //Ausgenommen ist natürlich der Februar ('2').
    int monate_31_tage[7] = {1, 3, 5, 7, 8, 10, 12};
    int monate_30_tage[4] = {4, 6, 9, 11};


    //Die folgenden zwei for-Schleifen gehen nun in 1er Schritten über die
    //beiden Arrays, indem die Variable i als Index des Arrays eingesetzt wird
    //und das darin liegende if-Statement prüft, ob der angegebene Monat im
    //jeweiligen Array enthalten ist. Ist dies der Fall wird der Text augegeben.
    //Wenn nicht wird i um 1 erhöht und die Schleife wiederholt.
    //Dies geschieht solang, bis eine Zahl gefunden wird.
    for(int i = 0; i < 7; i++){
        if (monat == monate_31_tage[i]){
            cout << "Der Monat hat 31 Tage\n";
        }
    }

    for(int i = 0; i < 4; i++){
        if (monat == monate_30_tage[i]){
            cout << "Der Monat hat 30 Tage\n";
        }
    }


    //Sollte der übergebene Monat Februar (also '2') sein, wird
    //geprüft, ob das übergebene Jahr ein Schaltjahr ist (mithilfe
    //der dafür erstellten Funktion).
    //Daraufhin wird der jeweilige Text ausgegeben.
    if (monat == 2 && schaltjahr(jahr)){                                //Schaltjahr(jahr) ist 'true'
        cout << "Der Monat hat 29 Tage. Es ist ein Schaltjahr.\n";
    }
    else if (monat == 2 && !schaltjahr(jahr)){                          //SChaltjahr(jahr) ist 'false'
        cout << "Der Monat hat 28 Tage. Es ist kein Schaltjahr.\n";
    }
}

int main()
{
    //Aufforderung User-Input
    int monat, jahr;
    cout << "Geben sie einen Monat ein:" << endl;
    cin >> monat;
    cout << "Geben sie eine Jahreszahl ein:" << endl;
    cin >> jahr;

    //Eine der beiden Funktionen mit den Werten des Users
    //aufrufen. Beide funktionieren, durch auskommentieren
    //kann man eine zur Nutzung festlegen.

    //tageslaenge_alt(monat, jahr);
    tageslaenge_neu(monat, jahr);
    return 0;
}
