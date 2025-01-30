#include <iostream>
#include <cstdlib>
#include <string>
#include <limits>
#include <unistd.h>

using namespace std;

// Colores ANSI para el gradiente
const string GRAY2 = "\033[38;5;235m";  // Gris oscuro
const string GRAY3 = "\033[38;5;239m";  // Gris medio oscuro
const string GRAY4 = "\033[38;5;243m";  // Gris medio
const string GRAY5 = "\033[38;5;247m";  // Gris medio claro
const string GRAY6 = "\033[38;5;251m";  // Gris claro
const string WHITE = "\033[38;5;255m";  // Blanco puro
const string RESET = "\033[0m";         // Restablecer colores

// Función para imprimir el banner
void printBanner() {
    cout << "\n\n";
    cout << GRAY2 << "       ██╗██████╗ ███████╗██╗  ██╗███████╗██████╗ ██╗      ██████╗  ██╗████████╗" << RESET << endl;
    cout << GRAY3 << "      ██╔╝██╔══██╗██╔════╝╚██╗██╔╝██╔════╝██╔══██╗██║     ██╔═████╗███║╚══██╔══╝" << RESET << endl;
    cout << GRAY4 << "     ██╔╝ ██║  ██║█████╗   ╚███╔╝ ███████╗██████╔╝██║     ██║██╔██║╚██║   ██║   " << RESET << endl;
    cout << GRAY5 << "    ██╔╝  ██║  ██║██╔══╝   ██╔██╗ ╚════██║██╔═══╝ ██║     ████╔╝██║ ██║   ██║   " << RESET << endl;
    cout << GRAY6 << "██╗██╔╝   ██████╔╝███████╗██╔╝ ██╗███████║██║     ███████╗╚██████╔╝ ██║   ██║   " << RESET << endl;
    cout << GRAY6 << "╚═╝╚═╝    ╚═════╝ ╚══════╝╚═╝  ╚═╝╚══════╝╚═╝     ╚══════╝ ╚═════╝  ╚═╝   ╚═╝   " << RESET << endl;
    cout << endl;
}

// Función para ejecutar comandos del sistema
void executeCommand(const string& command) {
    int result = system(command.c_str());
    if (result != 0) {
        cerr << "Error al ejecutar: " << command << endl;
    }
}

// Función para verificar si un programa está instalado
bool isProgramInstalled(const string& program) {
    string command = "which " + program + " > /dev/null 2>&1";
    int result = system(command.c_str());
    return (result == 0);
}

// Función para instalar programas necesarios
void installRequiredPrograms() {
    if (!isProgramInstalled("apktool")) {
        cout << "Instalando apktool..." << endl;
        executeCommand("sudo apt-get install apktool -y");
    } else {
        cout << "apktool ya está instalado." << endl;
    }

    if (!isProgramInstalled("dex2jar")) {
        cout << "Instalando dex2jar..." << endl;
        executeCommand("sudo apt-get install dex2jar -y");
    } else {
        cout << "dex2jar ya está instalado." << endl;
    }

    if (!isProgramInstalled("jd-gui")) {
        cout << "Instalando JD-GUI..." << endl;
        executeCommand("sudo apt-get install jd-gui -y");
    } else {
        cout << "JD-GUI ya está instalado." << endl;
    }

    if (!isProgramInstalled("smali")) {
        cout << "Instalando smali..." << endl;
        executeCommand("sudo apt-get install smali -y");
    } else {
        cout << "smali ya está instalado." << endl;
    }
}

// Menú de opciones
void showMenu() {
    cout << GRAY2 << "╔═══════════════════════════════════════════════╗" << RESET << endl;
    cout << GRAY3 << "║                                               ║" << RESET << endl;
    cout << GRAY4 << "║          Automatización de APKTool            ║" << RESET << endl;
    cout << GRAY5 << "║                                               ║" << RESET << endl;
    cout << GRAY6 << "╠═══════════════════════════════════════════════╣" << RESET << endl;

    // Opciones del menú
    cout << GRAY6 << "║ 1. Descompilar APK                            ║" << RESET << endl;
    cout << GRAY6 << "║ 2. Recompilar APK                             ║" << RESET << endl;
    cout << GRAY6 << "║ 3. Firmar APK                                 ║" << RESET << endl;
    cout << GRAY5 << "║ 4. Usar dex2jar para convertir .dex a .jar    ║" << RESET << endl;
    cout << GRAY5 << "║ 5. Abrir JD-GUI para inspeccionar .jar        ║" << RESET << endl;
    cout << GRAY4 << "║ 6. Ayuda                                      ║" << RESET << endl;
    cout << GRAY3 << "║ 0. Salir                                      ║" << RESET << endl;
    cout << GRAY2 << "╠═══════════════════════════════════════════════╣" << RESET << endl;

    cout << GRAY2 << "\n\n >" << GRAY3 << ">" << GRAY4 << "> ";
}

// Funcion para limpiar la ventana
void limpiarPantalla() {
    std::cout << "\033[2J\033[1;1H"; // Código ANSI para limpiar la pantalla
}

// Funcion para esperar tecla
void esperarTecla() {
    std::cout << "\nPresione la tecla Enter para continuar... ";
    std::cin.ignore();
    std::cin.get();
}

// Función para obtener la ruta completa del archivo
string expandHomePath(const string& path) {
    if (path[0] == '~') {
        const char* homeDir = getenv("HOME");
        return string(homeDir) + path.substr(1);
    }
    return path;
}

// Función para descompilar el APK
void decompileAPK() {
    limpiarPantalla();
    string apkFile;
    cout << GRAY5 << "Introduce la ruta del archivo APK a descompilar\n";
    cout << GRAY6 << "═══════════════════════════════════════════════\n\n";
    cout << GRAY3 << ">" << GRAY4 << ">" << GRAY5 << "> ";
    getline(cin, apkFile);  // Solo getline; el buffer ya está limpio
    cout << GRAY6 << "\n\n═══════════════════════════════════════════════\n";
    if (!apkFile.empty()) {
        apkFile = expandHomePath(apkFile);  // Expande el ~ a la ruta completa
        string command = "apktool d \"" + apkFile + "\"";  // Comillas para rutas con espacios
        executeCommand(command);
        cout << GRAY6 << "\n═══════════════════════════════════════════════";
    } else {
        cout << "La ruta proporcionada no es válida." << endl;
    }
    esperarTecla();
}

void recompileAPK() {
    limpiarPantalla();
    string folder;
    cout << "Introduce la carpeta con los archivos descompilados: ";
    getline(cin, folder);  // No es necesario cin.ignore()
    if (!folder.empty()) {
        string command = "apktool b \"" + folder + "\"";  // Comillas para manejar espacios
        executeCommand(command);
    } else {
        cout << "La ruta proporcionada no es válida." << endl;
    }
    esperarTecla();
}

void signAPK() {
    limpiarPantalla();
    string apkFile;
    cout << "Introduce la ruta del archivo APK a firmar: ";
    getline(cin, apkFile);  // No es necesario cin.ignore()
    if (!apkFile.empty()) {
        string command = "jarsigner -verbose -keystore my-release-key.jks \"" + apkFile + "\" alias_name";
        cout << "Asegúrate de tener configurado el keystore antes de continuar." << endl;
        executeCommand(command);
    } else {
        cout << "La ruta proporcionada no es válida." << endl;
    }
    esperarTecla();
}

// Función para usar dex2jar
void useDex2Jar() {
    limpiarPantalla();
    string dexFile;
    cout << GRAY5 << "Introduce la ruta del archivo .dex a convertir a .jar\n";
    cout << GRAY6 << "═══════════════════════════════════════════════\n\n";
    cout << GRAY3 << ">" << GRAY4 << ">" << GRAY5 << "> ";
    getline(cin, dexFile);
    cout << GRAY6 << "\n\n═══════════════════════════════════════════════\n";
    if (!dexFile.empty()) {
        dexFile = expandHomePath(dexFile);  // Expande el ~ a la ruta completa
        string command = "d2j-dex2jar \"" + dexFile + "\"";
        executeCommand(command);
        cout << GRAY6 << "\n═══════════════════════════════════════════════";
    } else {
        cout << "La ruta proporcionada no es válida." << endl;
    }
    esperarTecla();
}

// Función para abrir JD-GUI
void openJDGUI() {
    limpiarPantalla();
    string jarFile;
    cout << GRAY5 << "Introduce la ruta del archivo .jar a inspeccionar\n";
    cout << GRAY6 << "═══════════════════════════════════════════════\n\n";
    cout << GRAY3 << ">" << GRAY4 << ">" << GRAY5 << "> ";
    getline(cin, jarFile);
    cout << GRAY6 << "\n\n═══════════════════════════════════════════════\n";
    if (!jarFile.empty()) {
        jarFile = expandHomePath(jarFile);  // Expande el ~ a la ruta completa
        string command = "jd-gui \"" + jarFile + "\"";
        executeCommand(command);
        cout << GRAY6 << "\n═══════════════════════════════════════════════";
    } else {
        cout << "La ruta proporcionada no es válida." << endl;
    }
    esperarTecla();
}

// Función para mostrar la ayuda
void showHelp() {
    limpiarPantalla();
    cout << GRAY5 << "═══════════════════════════════════════════════\n";
    cout << GRAY6 << "                  AYUDA\n";
    cout << GRAY5 << "═══════════════════════════════════════════════\n\n";
    cout << GRAY3 << "1. Descompilar APK:\n";
    cout << GRAY4 << "   Esta opción permite descompilar un archivo APK en su código fuente.\n";
    cout << GRAY5 << "   Ejemplo: Introduce la ruta del archivo APK (ej: ~/Descargas/app.apk).\n\n";
    cout << GRAY3 << "2. Recompilar APK:\n";
    cout << GRAY4 << "   Esta opción permite recompilar una carpeta con archivos descompilados en un APK.\n";
    cout << GRAY5 << "   Ejemplo: Introduce la ruta de la carpeta descompilada (ej: ~/app_decompiled).\n\n";
    cout << GRAY3 << "3. Firmar APK:\n";
    cout << GRAY4 << "   Esta opción permite firmar un archivo APK con un keystore.\n";
    cout << GRAY5 << "   Ejemplo: Introduce la ruta del archivo APK (ej: ~/app_recompiled.apk).\n";
    cout << GRAY6 << "   Asegúrate de tener un keystore configurado.\n\n";
    cout << GRAY3 << "4. Usar dex2jar:\n";
    cout << GRAY4 << "   Esta opción convierte un archivo .dex a .jar para su inspección.\n";
    cout << GRAY5 << "   Ejemplo: Introduce la ruta del archivo .dex (ej: ~/classes.dex).\n\n";
    cout << GRAY3 << "5. Abrir JD-GUI:\n";
    cout << GRAY4 << "   Esta opción abre JD-GUI para inspeccionar un archivo .jar.\n";
    cout << GRAY5 << "   Ejemplo: Introduce la ruta del archivo .jar (ej: ~/classes-dex2jar.jar).\n\n";
    cout << GRAY3 << "6. Ayuda:\n";
    cout << GRAY4 << "   Muestra esta pantalla de ayuda con información sobre cada opción.\n\n";
    cout << GRAY3 << "0. Salir:\n";
    cout << GRAY4 << "   Cierra el programa.\n\n";
    cout << GRAY5 << "═══════════════════════════════════════════════\n";
    esperarTecla();
}

int main() {
    // Verificar e instalar programas necesarios al inicio
    installRequiredPrograms();

    int choice;
    do {
        limpiarPantalla();
        printBanner();
        showMenu();

        cin >> choice;
        cin.ignore(numeric_limits<streamsize>::max(), '\n');  // Limpia el buffer después de leer la opción

        switch (choice) {
            case 1:
                decompileAPK();
                break;
            case 2:
                recompileAPK();
                break;
            case 3:
                signAPK();
                break;
            case 4:
                useDex2Jar();
                break;
            case 5:
                openJDGUI();
                break;
            case 6:
                showHelp();
                break;
            case 0:
                limpiarPantalla();
                cout << GRAY2 << "Sali" << GRAY3 << "endo" << GRAY4 << " del" << GRAY5 << " programa..." << endl;
                break;
            default:
                cout << "Opción no válida. Inténtalo de nuevo." << endl;
        }
    } while (choice != 0);
    return 0;
}
