---
title: "Ausdr&#252;cke im Debugger | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
f1_keywords: 
  - "vs.debug.expressions"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VBScript"
helpviewer_keywords: 
  - "Debugger, Auswerten von Ausdrücken"
  - "Debuggen [Visual Studio], Ausdrucksauswertung"
  - "Debuggen [Visual Studio], Ausdrücke"
  - "Debuggen [Visual Studio], Variablenauswertung"
  - "Ausdrucksauswertung, Debuggerauswertung"
  - "Ausdrucksauswertungen"
  - "Ausdrücke [Debugger]"
  - "Systemeigene Ausdrucksauswertung"
ms.assetid: 70f9b531-44c7-4d77-980d-5eddbf2bff41
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ausdr&#252;cke im Debugger
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Visual Studio\-Debugger beinhaltet eine Ausdrucksauswertung, die aktiv wird, wenn Sie einen Ausdruck in das Dialogfeld **Schnellüberwachung**, in das Fenster **Überwachen** oder in das Fenster **Direkt** eingeben. Die Ausdruckauswertung ist auch im Fenster **Haltepunkte** sowie an vielen anderen Stellen im Debugger aktiv.  
  
 Die folgenden Abschnitte enthalten Informationen zu Ausdrücken in verschiedenen Sprachen.  
  
## F\#\-Ausdrücke werden nicht unterstützt.  
 F\#\-Ausdrücke werden nicht erkannt. Wenn Sie F\#\-Code debuggen, müssen Sie die Ausdrücke vor dem Eingeben in ein Debuggerfenster oder ein Dialogfeld in C\#\-Syntax übersetzen. Wenn Sie Ausdrücke aus F\# in C\# übersetzen, beachten Sie, dass C\# den `==`\-Operator für Gleichheitstests verwendet, wohingegen F\# ein einfaches Gleichheitszeichen \(`=`\) verwendet.  
  
## C\+\+\-Ausdrücke  
 Informationen zum Verwenden von Kontextoperatoren mit Ausdrücken in C\+\+ finden Sie unter [Kontextoperator \(C\+\+\)](../debugger/context-operator-cpp.md).  
  
### Nicht unterstützte Ausdrücke in C\+\+  
  
#### Konstruktoren, Destruktoren und Konvertierungen  
 Einen Konstruktor oder Destruktor für ein Objekt können Sie weder explizit noch implizit aufrufen. Mit folgendem Ausdruck wird ein Konstruktor beispielsweise explizit aufgerufen, was eine Fehlermeldung zur Folge hat:  
  
```cpp  
my_date( 2, 3, 1985 )  
```  
  
 Sie können keine Konvertierungsfunktion aufrufen, wenn es sich beim Ziel der Konvertierung um eine Klasse handelt. Eine solche Konvertierung impliziert die Erstellung eines Objekts. Wenn `myFraction` beispielsweise eine Instanz von `CFraction` ist, durch die der Konvertierungsfunktionsoperator `FixedPoint` definiert wird, verursacht der folgende Ausdruck einen Fehler:  
  
```cpp  
(FixedPoint)myFraction  
```  
  
 Sie können den new\- oder delete\-Operator nicht aufrufen. Beispielsweise wird der folgende Ausdruck nicht unterstützt:  
  
```cpp  
new Date(2,3,1985)  
```  
  
#### Präprozessormakros  
 Präprozessormakros werden im Debugger nicht unterstützt. Wenn beispielsweise eine Konstante `VALUE` als  `#define VALUE 3` deklariert wird, können Sie `VALUE` im Fenster **Überwachen** nicht verwenden. Um diese Einschränkung zu vermeiden, sollten Sie `#define` nach Möglichkeit durch Enumerationen und Funktionen ersetzen.  
  
### "using namespace"\-Deklarationen  
 Sie können keine `using namespace`\-Deklarationen verwenden.  Um auf einen Typnamen oder eine Variable außerhalb des aktuellen Namespace zugreifen zu können, müssen Sie den vollqualifizierten Namen verwenden.  
  
### Anonyme Namespaces  
 Anonyme Namespaces werden nicht unterstützt. Bei folgendem Code können Sie `test` im Fenster "Überwachen" nicht hinzufügen:  
  
```cpp  
namespace mars { namespace { int test = 0; } } int main() { // Adding a watch on test does not work. mars::test++; return 0; }  
  
```  
  
###  <a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> Verwenden der systeminternen Funktionen des Debuggers zur Beibehaltung des Zustands  
 Die systeminternen Debugger\-Funktionen geben Ihnen eine Möglichkeit, zum Aufruf bestimmter C\/C\+\+\-Funktionen in Ausdrücken ohne den Zustand der Anwendung zu ändern.  
  
 Systeminterne Debugger\-Funktionen:  
  
-   Diese sind garantiert sicher: durch das Ausführen einer systeminternen Debugger\-Funktion wird der Prozess, der debuggt wird, nicht beschädigt.  
  
-   Sie sind in allen Ausdrücken zulässig, sogar in Szenarien, in denen Nebeneffekte und Funktionsauswertung nicht gestattet ist.  
  
-   Sie arbeiten in Szenarien, in denen reguläre Funktionsaufrufe nicht möglich sind, z. B. das Debuggen eines Minidumps.  
  
 Mit systeminternen Debugger\-Funktionen kann die Auswertung von Ausdrücken bequemer werden. Beispielsweise ist `strncmp(str, “asd”)` viel einfacher in einer Haltepunktbedingung zu schreiben als `str[0] == ‘a’ && str[1] == ‘s’ && str[2] == ‘d’`. \)  
  
|Bereich|Systeminterne Funktionen|  
|-------------|------------------------------|  
|**Zeichenfolgenlänge**|strlen, wcslen, strnlen, wcsnlen|  
|**Zeichenfolgenvergleich**|strcmp, wcscmp, stricmp, \_stricmp, \_strcmpi, wcsicmp, \_wcscmpi, \_wcsnicmp, strncmp, wcsncmp, strnicmp, wcsnicmp|  
|**Zeichenfolgensuche**|strchr, wcschr, strstr, wcsstr|  
|**Win32**|GetLastError\(\), TlsGetValue\(\)|  
|**Windows 8**|WindowsGetStringLen\(\), WindowsGetStringRawBuffer\(\)<br /><br /> Für diese Funktionen muss der Prozess, der debuggt wird, auf Windows. 8 ausgeführt werden. Das Debuggen von Dumpdateien, die von einem Windows 8\-Gerät generiert werden, erfordert auch, dass auf dem Visual Studio\-Computer Windows 8 ausgeführt wird. Wenn Sie für ein Windows 8\-Gerät Remotedebuggen durchführen, kann auf dem Visual Studio\-Computer Windows 7 ausgeführt werden.|  
|**Sonstiges**|\_\_log2<br /><br /> Gibt die Protokollbasis 2 einer angegebenen ganzen Zahl auf die nächste kleinere ganze Zahl gerundet zurück.|  
  
## C\+\+\/CLI – Nicht unterstützte Ausdrücke  
  
-   Typumwandlungen mit Zeigern oder benutzerdefinierten Typumwandlungen werden nicht unterstützt.  
  
-   Vergleiche und Zuweisungen von Objekten werden nicht unterstützt.  
  
-   Überladene Operatoren und überladene Funktionen werden nicht unterstützt.  
  
-   Boxing und Unboxing werden nicht unterstützt.  
  
-   Der `Sizeof`\-Operator wird nicht unterstützt.  
  
## C\# – Nicht unterstützte Ausdrücke  
  
### Dynamische Objekte  
 Sie können Variablen in Debuggerausdrücken verwenden, die statisch als dynamisch typisiert sind. Wenn Objekte, die die [IDynamicMetaObjectProvider Schnittstelle](../Topic/IDynamicMetaObjectProvider%20Interface.md) implementieren, im Überwachungsfenster ausgewertet werden, wird ein dynamischer Ansichtsknoten hinzugefügt. Der dynamische Ansichtsknoten zeigt Member an, ermöglicht aber keine Bearbeitung der Memberwerte.  
  
 Die folgenden Funktionen dynamischer Objekte werden nicht unterstützt:  
  
-   Die zusammengesetzten Operatoren `+=`, `-=`, `%=`, `/=` und `*=`  
  
-   Viele Umwandlungen, einschließlich numerischer Umwandlungen und Typargumentumwandlungen  
  
-   Methodenaufrufe mit mehr als zwei Argumenten  
  
-   Eigenschaftengetter mit mehr als zwei Argumenten  
  
-   Eigenschaftensetter mit Argumenten  
  
-   Zuweisen zu einem Indexer  
  
-   Boolesche Operatoren `&&` und `||`  
  
### Anonyme Methoden  
 Die Erstellung neuer anonymer Methoden wird nicht unterstützt.  
  
## Visual Basic – Nicht unterstützte Ausdrücke  
  
### Dynamische Objekte  
 Sie können Variablen in Debuggerausdrücken verwenden, die statisch als dynamisch typisiert sind. Wenn Objekte, die die [IDynamicMetaObjectProvider Schnittstelle](../Topic/IDynamicMetaObjectProvider%20Interface.md) implementieren, im Überwachungsfenster ausgewertet werden, wird ein dynamischer Ansichtsknoten hinzugefügt. Der dynamische Ansichtsknoten zeigt Member an, ermöglicht aber keine Bearbeitung der Memberwerte.  
  
 Die folgenden Funktionen dynamischer Objekte werden nicht unterstützt:  
  
-   Die zusammengesetzten Operatoren `+=`, `-=`, `%=`, `/=` und `*=`  
  
-   Viele Umwandlungen, einschließlich numerischer Umwandlungen und Typargumentumwandlungen  
  
-   Methodenaufrufe mit mehr als zwei Argumenten  
  
-   Eigenschaftengetter mit mehr als zwei Argumenten  
  
-   Eigenschaftensetter mit Argumenten  
  
-   Zuweisen zu einem Indexer  
  
-   Boolesche Operatoren `&&` und `||`  
  
### Lokale Konstanten  
 Lokale Konstanten werden nicht unterstützt.  
  
### Importaliase  
 Importaliase werden nicht unterstützt.  
  
### Variablendeklarationen  
 Neue Variablen können in Debuggerfenstern nicht explizit deklariert werden. Allerdings sind Zuweisungen neuer impliziter Variablen im Fenster **Direkt** möglich. Diese impliziten Variablen sind auf die Debugsitzung beschränkt und können von außerhalb des Debuggers nicht aufgerufen werden. Die Anweisung `o = 5` beispielsweise erstellt implizit eine neue `o`\-Variable und weist dieser den Wert 5 zu. Solche impliziten Variablen sind vom Typ **Object**, sofern der Typ nicht durch den Debugger abgeleitet werden kann.  
  
### Nicht unterstützte Schlüsselwörter  
  
-   `AddressOf`  
  
-   `End`  
  
-   `Error`  
  
-   `Exit`  
  
-   `Goto`  
  
-   `On Error`  
  
-   `Resume`  
  
-   `Return`  
  
-   `Select/Case`  
  
-   `Stop`  
  
-   `SyncLock`  
  
-   `Throw`  
  
-   `Try/Catch/Finally`  
  
-   `With`  
  
-   Schlüsselwörter der Namespace\- oder Modulebene, wie `End Sub` oder `Module`.  
  
## Siehe auch  
 [Formatbezeichner in C\+\+](../debugger/format-specifiers-in-cpp.md)   
 [Kontextoperator \(C\+\+\)](../debugger/context-operator-cpp.md)   
 [Formatbezeichner in C\#](../debugger/format-specifiers-in-csharp.md)   
 [Pseudovariablen](../debugger/pseudovariables.md)