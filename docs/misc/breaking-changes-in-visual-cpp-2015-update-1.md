---
title: "Wichtige &#196;nderungen in Visual C++ 2015 Update 1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c0b1c2b-e1cf-4767-885b-b98df9b3730e
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "mithom"
manager: "ghogen"
---
# Wichtige &#196;nderungen in Visual C++ 2015 Update 1
Wenn Sie ein Upgrade auf Visual C\+\+ 2015 Update 1 ausführen, treten unter Umständen Kompilierungs\- und\/oder Laufzeitfehler im Code auf, der zuvor ordnungsgemäß kompiliert und ausgeführt wurde. Änderungen beim Compiler oder Laufzeitverhalten, die solche Probleme verursachen, werden als *wichtige Änderungen* bezeichnet und werden in der Regel durch Änderungen im C\+\+\-Sprachstandard, in den Funktionssignaturen oder im Layout von Objekten im Arbeitsspeicher erforderlich.  
  
 Der restliche Artikel beschreibt spezifische wichtige Änderungen in Visual C\+\+ 2015 Update 1, und die Begriffe „neues Verhalten“ und „jetzt“ in diesem Artikel beziehen sich auf diese Version. Die Begriffe „altes Verhalten“ und „früher“ beziehen sich auf die ursprüngliche Version von Visual Studio 2015 und frühere Versionen. Informationen zu wichtigen Änderungen, die zwischen Visual Studio 2013 und Visual Studio 2015 vorgenommen wurden, finden Sie unter [Wichtige Änderungen in Visual C\+\+ 2015](/visual-cpp/porting/visual-cpp-change-history-2003-20151).  
  
-   [Wichtige Compileränderungen](#BK_compiler)  
  
##  <a name="BK_compiler"></a> Visual C\+\+\-Compiler  
  
-   **Private virtuelle Basisklassen und indirekte Vererbung**  
  
     In früheren Versionen des Compilers war es abgeleiteten Klassen möglich, Member ihrer *indirekt abgeleiteten* `private virtual` Basisklassen aufzurufen. Dieses alte Verhalten war falsch und entsprach nicht dem C\+\+\-Standard. Der Compiler akzeptiert in dieser Weise erstellten Code nicht mehr und gibt den Compilerfehler C2280 als Ergebnis aus.  
  
 **Fehler C2280: *'void \*S3::\_\_delDtor\(unsigned int\)'*: Es wurde versucht, auf eine gelöschte Funktion zu verweisen**     Beispiel \(vorher\)  
  
    ```cpp  
    class base { protected: base(); ~base(); }; class middle: private virtual base {};class top: public virtual middle {}; void destroy(top *p) { delete p;  // }  
    ```  
  
     Beispiel \(nachher\)  
  
    ```cpp  
    class base;  // as above class middle: protected virtual base {}; class top: public virtual middle {}; void destroy(top *p) { delete p; }  
    ```  
  
     \- oder \-  
  
    ```  
    class base;  // as above class middle: private virtual base {}; class top: public virtual middle, private virtual bottom {}; void destroy(top *p) { delete p; }  
    ```  
  
-   **Überladener Operator „new“ und „delete“**  
  
     In früheren Versionen des Compilers konnte ein `operator new`, der kein Member war, und ein `operator delete`, der kein Member war, statisch deklariert werden und in anderen Namespaces als dem globalen deklariert werden.  Durch dieses alte Verhalten entstand eine Gefahr, dass das Programm den Operator `new` oder `delete` nicht in der vom Programmierer beabsichtigten Implementierung aufrief, was zu einem schlechten Laufzeitverhalten ohne Rückmeldung führte. Der Compiler akzeptiert in dieser Weise erstellten Code nicht mehr und gibt den Compilerfehler C2323 als Ergebnis aus.  
  
 **Fehler C2323: *„Operator new“*: Funktionen mit Nichtmemberoperatoren ‚new‘ oder ‚delete‘ können nicht statisch oder in einem anderen als dem globalen Namespace deklariert werden.**     Beispiel \(vorher\)  
  
    ```cpp  
  
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323  
    ```  
  
     Beispiel \(nachher\)  
  
    ```cpp  
  
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'  
    ```  
  
     Außerdem, auch wenn dazu keine spezifische Diagnose ausgegeben wird, wird ein Inlineoperator „new“ als nicht wohlgeformt angesehen.  
  
-   **Aufrufen von 'operator *type*\(\)' \(benutzerdefinierte Konversion\) für Nichtklassentypen**  
  
     Frühere Versionen ließen den Aufruf von 'operator *type*\(\)' für Nichtklassentypen zu und ignorierten den Aufruf stumm. Durch dieses alte Verhalten entstand die Gefahr der stummen Erzeugung von ungültigem Code, was zu unvorhersehbarem Laufzeitverhalten führt. Der Compiler akzeptiert in dieser Weise erstellten Code nicht mehr und gibt den Compilerfehler C2228 als Ergebnis aus.  
  
 **Fehler C2228: links von '.operator *type*' muss „class\/struct\/union“ angegeben werden**     Beispiel \(vorher\)  
  
    ```cpp  
    typedef int index_t; void bounds_check(index_t index); void login(int column) { bounds_check(column.operator index_t());  // error C2228 }  
    ```  
  
     Beispiel \(nachher\)  
  
    ```cpp  
    typedef int index_t; void bounds_check(index_t index); void login(int column) { bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int' }  
    ```  
  
-   **Redundanter Typname in ausführlichen Typbezeichner**  
  
     Frühere Versionen des Compilers ließen `typename` in ausführlichen Typbezeichnern zu; in dieser Weise erstellter Code ist semantisch inkorrekt. Der Compiler akzeptiert in dieser Weise erstellten Code nicht mehr und gibt den Compilerfehler C3406 als Ergebnis aus.  
  
 **Fehler C3406: 'typename' darf in ausführlichen Typbezeichnern nicht verwendet werden**     Beispiel \(vorher\)  
  
    ```cpp  
    template <typename class T> class container;  
    ```  
  
     Beispiel \(nachher\)  
  
    ```cpp  
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case class container;  
    ```  
  
-   **Typableitung von Arrays aus einer Initialisiererliste**  
  
     In früheren Versionen des Compilers wurde die Typableitung von Arrays aus einer Initialisiererliste nicht unterstützt. Der Compiler unterstützt jetzt diese Form der Typableitung. Das kann zur Folge haben, dass Aufrufe an Funktionsvorlagen mithilfe von Initialisiererlisten jetzt möglicherweise nicht mehr eindeutig sind, oder es wird eine andere Überladung gewählt als in früheren Versionen des Compilers. Um diese Probleme zu beheben, muss das Programm jetzt die vom Programmierer beabsichtigte Überladung explizit angeben.  
  
     Wenn dieses neue Verhalten dazu führt, dass bei der Überladungsauflösung ein weitere Kandidat als ebenso gut wie der historische Kandidat angesehen wird, ist der Aufruf nicht mehr eindeutig, und der Compiler gibt den Compilerfehler C2668 als Ergebnis aus.  
  
 **Fehler: '*\-Funktion*': Mehrdeutiger Aufruf einer überladenen Funktion.**     Beispiel 1: Mehrdeutiger Aufruf einer überladenen Funktion \(vorher\)  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...) template <typename... Args> void f(int, Args...);  // template <int N, typename... Args> void f(const int (&)[N], Args...); int main() { // The compiler now considers this call ambiguous, and issues a compiler error  f({3});  error C2668: 'f' ambiguous call to overloaded function }  
    ```  
  
     Beispiel 1: Mehrdeutiger Aufruf einer überladenen Funktion \(nachher\)  
  
    ```cpp  
    template <typename... Args> void f(int, Args...);  // template <int N, typename... Args> void f(const int (&)[N], Args...); int main() { // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it. f(3); }  
    ```  
  
     Wenn dieses neue Verhalten bewirkt, dass ein anderer Kandidat bei der Überladungsauflösung als bessere Übereinstimmung als der historische Kandidat angesehen wird, wird der Aufruf unzweideutig zum neuen Kandidaten aufgelöst, was eine Änderung im Verhalten des Programms bewirkt, das vermutlich von den Absichten des Programmierers abweicht.  
  
     Beispiel 2: Änderung an der Überladungsauflösung \(vorher\)  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...) struct S { int i; int j; }; template <typename... Args> void f(S, Args...); template <int N, typename... Args> void f(const int *&)[N], Args...); int main() { // The compiler now resolves this call to f(const int (&)[N], Args...) instead  f({1, 2}); }  
    ```  
  
     Beispiel 2: Änderung an der Überladungsauflösung \(nachher\)  
  
    ```cpp  
    struct S;  // as before template <typename... Args> void f(S, Args...); template <int N, typename... Args> void f(const int *&)[N], Args...); int main() { // To call f(S, Args...), perform an explicit cast to S on the initializer list. f(S{1, 2}); }  
    ```  
  
-   **Wiederherstellung von Warnungen der switch\-Anweisung**  
  
     In früheren Versionen des Compilers wurden bereits vorhandene Warnungen, die sich auf `switch`\-Anweisungen bezogen, entfernt; diese Warnungen wurden jetzt wiederhergestellt. Der Compiler gibt jetzt die wiederhergestellten Warnungen aus, und Warnungen, die sich auf bestimmte Fälle \(einschließlich des Standardfalls\) bezogen, werden jetzt in der Zeile ausgegeben, die den Verstoß enthält, statt in der letzten Zeile der switch\-Anweisung. Die Ausgabe dieser Warnungen in anderen Zeilen als bisher kann zur Folge haben, dass Warnungen, die früher mithilfe von `#pragma warning(disable:####)` unterdrückt wurden, möglicherweise nicht mehr wie beabsichtigt unterdrückt werden. Um diese Warnungen wie beabsichtigt zu unterdrücken, kann es erforderlich sein, die `#pragma warning(disable:####)`\-Anweisung in eine Zeile oberhalb des ersten möglichen Verstoßes zu verschieben. Die wiederhergestellten Warnungen folgen hier:  
  
 **Warnung C4060: switch\-Anweisung enthält weder „case“\- noch „default“\-Bezeichnungen Warnung C4061: Der Enumerator '*bit1*' in der switch\-Anweisung der Enumeration '*flags*' wird von keiner „case“\-Bezeichnung explizit behandelt Warnung C4062: Der Enumerator '*bit1*' in der switch\-Anweisung der Enumeration '*flags*' wird nicht behandelt Warnung C4063: case '*bit32*' ist kein gültiger Wert für die switch\-Anweisung der Enumeration '*flags*' Warnung C4064: switch\-Aweisung für unvollständige Enumeration '*flags*' Warnung C4065: die „switch“\-Anweisung enthält 'default'\-Beschriftungen, aber keine 'case'\-Beschriftungen Warnung C4808: case '*value*' ist kein gültiger Wert für die switch\-Bedingung vom Typ '*bool*' Warnung C4809: Die switch\-Anweisung weist eine redundante 'default'\-Beschriftung auf; alle möglichen 'case'\-Beschriftungen wurden angegeben**     Beispiel für C4063 \(vorher\)  
  
    ```cpp  
    class settings { public: enum flags { bit0 = 0x1, bit1 = 0x2, ... }; ... }; int main() { auto val = settings::bit1; switch (val) { case settings::bit0: break; case settings::bit1: break;  case settings::bit0 | settings::bit1:  // warning C4063 break; } };  
    ```  
  
     Beispiel für C4063 \(nachher\)  
  
    ```cpp  
    class settings {...};  // as above int main() { // since C++11, use std::underlying_type to determine the underlying type of an enum typedef std::underlying_type<settings::flags>::type flags_t; auto val = settings::bit1; switch (static_cast<flags_t>(val)) { case settings::bit0: break; case settings::bit1: break; case settings::bit0 | settings::bit1:  // ok break; } };  
    ```  
  
     Beispiele für die anderen wiederhergestellten Warnungen stehen in deren Dokumentation zur Verfügung.  
  
-   **\#include: Verwendung des Bezeichners '..' für das übergeordnete Verzeichnis im Pfadnamen**  \(betrifft nur „\/Wall \/WX“\)  
  
     Frühere Versionen des Compilers haben die Verwendung des Bezeichners '..' für das übergeordnete Verzeichnis im Pfadnamen von `#include`\-Anweisungen nicht erkannt. Bei in dieser Weise erstelltem Code wird normalerweise die Absicht verfolgt, Header einzuschließen, die sich außerhalb des Projekts befinden, und dazu werden fälschlicherweise projektrelative Pfade verwendet. Bei diesem alten Verhalten ergab sich die Gefahr, dass das Programm möglicherweise mit Einschluss einer anderen als der vom Programmierer beabsichtigten Quelldatei compiliert wurde oder dass diese relativen Pfade nicht auf andere Buildumgebungen portiert werden konnten. Der Compiler erkennt jetzt in dieser Weise erstellten Code und benachrichtigt den Programmierer mit der optionalen Compilerwarnung C4464, sofern diese aktiviert ist.  
  
 **Warnung C4464: Der relative Includepfad enthält '..'**     Beispiel \(vorher\)  
  
    ```cpp  
    #include "..\headers\C4426.h"  // emits warning C4464  
    ```  
  
     Beispiel \(nachher\)  
  
    ```cpp  
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories  
    ```  
  
     Darüber hinaus empfehlen wir, auch wenn der Compiler dazu keine spezifischen Diagnosemeldungen ausgibt, den Bezeichner ".." für das übergeordnete Verzeichnis beim Angeben der Includeverzeichnisse des Projekts nicht zu verwenden.  
  
-   **\#pragma optimize\(\) erstreckt sich über das Ende der Headerdatei hinaus** \(betrifft nur „\/Wall \/WX“\)  
  
     In früheren Versionen wurden Änderungen an den Optimierungseinstellungen nicht erkannt, die zum Escapen einer in einer Übersetzungseinheit eingeschlossenen Headerddatei dienen. Der Compiler erkennt jetzt in dieser Weise erstellten Code und setzt den Programmierer mit der optionalen Compilerwarnung C4426 von der Position des `#include`\-Verstoßes in Kenntnis, sofern diese aktiviert ist. Diese Warnung wird nur ausgegeben, wenn die Änderungen im Konflikt mit den Optimierungseinstellungen stehen, die durch die Befehlszeilenargumente für den Compiler festgelegt wurden.  
  
 **Warnung C4426: Die Optimierungseinstellungen wurden nach dem Einschließen des Headers geändert, möglicherweise aufgrund von „\#pragma optimize\(\)“**     Beispiel \(vorher\)  
  
    ```cpp  
    // C4426.h #pragma optimize("g", off) ... // C4426.h ends // C4426.cpp #include "C4426.h"  // warning C4426  
    ```  
  
     Beispiel \(nachher\)  
  
    ```cpp  
    // C4426.h #pragma optimize("g", off) ... #pragma optimize("", on)  // restores optimization flags set via command-line arguments // C4426.h ends // C4426.cpp #include "C4426.h"  
    ```  
  
-   **Nicht übereinstimmende Festlegung von „\#pragma warning“\(push\)** und **„\#pragma warning“\(pop\)** \(betrifft nur „\/Wall \/WX“\)  
  
     Frühere Versionen des Compilers konnten keine `#pragma warning(push)`\-Statusänderungen erkennen, die in Kombination mit `#pragma warning(pop)`\-Statusänderungen in einer anderen Quelldatei auftraten, was selten beabsichtigt ist. Dieses alte Verhalten brachte die Gefahr mit sich, dass das Programm mit anderen Warnungseinstellungen als den vom Programmierer vorgesehenen kompiliert wurde, was möglicherweise zu einem schlechten Laufzeitverhalten führt. Der Compiler erkennt jetzt in dieser Weise erstellten Code und setzt den Programmierer mit der optionalen Compilerwarnung C5031 von der Position der `#pragma warning(pop)`\-Übereinstimmung in Kenntnis, sofern diese aktiviert ist. Diese Warnung enthält einen Hinweis, der auf die Position der entsprechenden \#pragma\-Warnung\(push\) verweist.  
  
 **Warnung C5031: „\#pragma warning“\(pop\): wahrscheinlich Fehlzuordnung, Pop\-Warnstatus in anderer Datei als Push**     Beispiel \(vorher\)  
  
    ```cpp  
    // C5031_part1.h #pragma warning(push) #pragma warning(disable:####) ... // C5031_part1.h ends without #pragma warning(pop) // C5031_part2.h ... #pragma warning(pop)  // pops a warning state not pushed in this source file ... // C5031_part1.h ends // C5031.cpp #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling' ... #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031 ...   
    ```  
  
     Beispiel \(nachher\)  
  
    ```cpp  
    // C5031_part1.h #pragma warning(push) #pragma warning(disable:####) ... #pragma warning(pop)  // pops the warning state pushed in this source file // C5031_part1.h ends without #pragma warning(pop) // C5031_part2.h #pragma warning(push)  // pushes the warning state pushed in this source file #pragma warning(disable:####) ... #pragma warning(pop) // C5031_part1.h ends // C5031.cpp #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order. ... #include "C5031_part2.h" ...   
    ```  
  
     Es ist zwar ungewöhnlich, aber in dieser Weise erstelltem Code liegt manchmal Absicht zugrunde. In dieser Weise erstellter Code ist empfindlich gegenüber Änderungen an der `#include`\-Reihenfolge; wir empfehlen, dass Quellcodedateien den Warnungsstatus nach Möglichkeit eigenständig verwalten sollten.  
  
-   **Nicht zugeordnete „\#pragma warning“ \(push\)** \(betrifft nur „\/Wall \/WX“\)  
  
     Frühere Versionen des Compilers haben nicht zugeordnete `#pragma warning(push)`\-Statusänderungen am Ende einer Übersetzungseinheit nicht erkannt. Der Compiler erkennt jetzt in dieser Weise erstellten Code und setzt den Programmierer mit der optionalen Compilerwarnung C5032 von der Position der nicht zugeordneten „\#pragma warning“\(push\) in Kenntnis, sofern diese aktiviert ist. Diese Warnung wird nur ausgegeben, wenn in der Übersetzungseinheit keine Kompilierfehler auftreten.  
  
 **Warnung C5032: „\#pragma warning“\(push\) ohne entsprechende „\#pragma warning“\(pop\) erkannt**     Beispiel \(vorher\)  
  
    ```cpp  
    // C5032.h #pragma warning(push) #pragma warning(disable:####) ... // C5032.h ends without #pragma warning(pop) // C5032.cpp #include "C5032.h" ... // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h  
    ```  
  
     Beispiel \(nachher\)  
  
    ```cpp  
    // C5032.h #pragma warning(push) #pragma warning(disable:####) ... #pragma warning(pop) // matches #pragma warning (push) on line 1 // C5032.h ends // C5032.cpp #include "C5032.h" ... // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)  
    ```  
  
-   **Möglicherweise werden weitere Warnungen als Folge der verbesserten Statusnachverfolgung bei „\#pragma warning“ angezeigt**  
  
     In früheren Versionen des Compilers wurden Statusänderungen bei „\#pragma warning“ nicht hinreichend gut nachverfolgt, um alle beabsichtigten Warnungen auszugeben. Durch dieses Verhalten bestand die Gefahr, dass bestimmte Warnungen unter anderen als den vom Programmierer beabsichtigten Umständen effektiv unterdrückt wurden. Die Nachverfolgung des Status von „\#pragma warning“ erfolgt nun stabiler – insbesondere im Zusammenhang mit „\#pragma warning“\-Statusänderungen in Vorlagen – und gibt optional die neuen Warnungen C5031 und C5032 aus, die den Programmierer bei der Suche nach unbeabsichtigter Verwendung von `#pragma warning(push)` und `#pragma warning(pop)` unterstützen sollen.  
  
     Als Ergebnis der verbesserten Nachverfolgung des Status von „\#pragma warning“ können jetzt Warnungen ausgegeben werden, die früher fälschlicherweise unterdrückt wurden oder mit falsch identifizierten Problemen zusammenhingen.  
  
-   **Verbesserte Erkennung von unerreichbarem Code**  
  
     Änderungen an der C\+\+\-Standardbibliothek und eine im Vergleich mit früheren Versionen des Compilers verbesserte Möglichkeit zur Inlineausführung von Funktionsaufrufen ermöglichen dem Compiler jetzt unter Umständen den Nachweis, dass bestimmter Code unerreichbar ist. Dieses neue Verhalten kann zu neuen und häufiger ausgegebenen Instanzen von Warnung C4720 führen.  
  
 **Warnung C4720: unerreichbarer Code**     In vielen Fällen wird diese Warnung nur beim Kompilieren mit aktivierten Optimierungen ausgegeben, da bei den Optimierungen mehr Funktionsaufrufe inline erfolgen, redundanter Code eliminiert wird oder auf andere Weise die Möglichkeit geschaffen wird, bestimmten Code als unerreichbar zu erkennen. Nach unseren Beobachtungen treten neue Instanzen von Warnung C4720 häufig in Try\/Catch\-Blöcken auf, insbesondere in Verbindung mit [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).  
  
     Beispiel \(vorher\)  
  
    ```cpp  
    try { auto iter = std::find(v.begin(), v.end(), 5); } catch(…) { do_something();  // ok }  
    ```  
  
     Beispiel \(nachher\)  
  
    ```cpp  
    try { auto iter = std::find(v.begin(), v.end(), 5); } catch(…) { do_something();  // warning C4702: unreachable code }  
    ```