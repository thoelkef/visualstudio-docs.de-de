---
title: Verwenden den C++ Core Guidelines-Überprüfungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9f7813659f63e14c22ee40dc28eaa5b2d029288e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509408"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Verwenden den C++ Core Guidelines-Überprüfungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [mithilfe der C++ Core Guidelines-Überprüfungen](https://docs.microsoft.com/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).  
  
Der C++ Core Guidelines sind eine portable Gruppe von Richtlinien, Regeln und bewährten Methoden zum Schreiben von Code in C++, die von Experten für C++ und Designern erstellt.  Visual Studio unterstützt jetzt die Add-in-Pakete, die zusätzliche Regeln für den Code Analysetools erstellen, überprüfen Sie Ihren Code für die Kompatibilität mit den C++ Core Guidelines und Verbesserungen vorschlagen.  
  
## <a name="the-c-core-guidelines-project"></a>Projizieren den C++ Core Guidelines  
 Bjarne Stroustrup und andere erstellt haben, werden den C++ Core Guidelines eine Anleitung zur Verwendung von modernem C++ problemlos und effektiv. Die Richtlinien Betonen Sie statische typsicherheit und Sicherheit der Ressource. Sie identifizieren Möglichkeiten zum beseitigen oder minimieren die am häufigsten fehleranfälligen Teile der Sprache, und es empfiehlt sich, wie Sie Ihren Code vereinfachen und bieten eine bessere Leistung auf zuverlässige Weise. Diese Richtlinien werden von der Standard C++ Foundation verwaltet. Weitere Informationen finden Sie in der Dokumentation, [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines), und der Zugriff auf die Projektdateien der C++ Core Guidelines-Dokumentation auf [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
 Microsoft unterstützt den C++ Core Guidelines Aufwand dazu von C++ Core Check Codeanalyse-Regelsätze legt fest, dass Sie Ihre Projekte mithilfe eines Nuget-Pakets hinzufügen können. Das Paket den Namen Microsoft.CppCoreCheck, und es finden Sie unter [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Dieses Paket ist erforderlich, dass Sie mindestens Visual Studio 2015 mit Update 1 installiert haben.  
  
 Das Paket wird auch ein anderes Paket als Abhängigkeit, eine nur-Header-Guideline Support Library (GSL) installiert. GSL steht auch auf GitHub unter [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Aktivieren Sie die C++ Core Check-Richtlinien in der Codeanalyse  
 Um den C++ Core Check Tool zur Codeanalyse zu aktivieren, installieren Sie das Microsoft.CppCoreCheck NuGet-Paket jedes C++-Projekt, das Sie in Visual Studio überprüfen möchten.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Das Microsoft.CppCoreCheck-Paket Ihrem Projekt hinzufügen  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste das Kontextmenü des Projekts in der Projektmappe zu öffnen, die das Paket hinzugefügt werden soll. Wählen Sie **NuGet-Pakete verwalten** zum Öffnen der **NuGet Package Manager**.  
  
2.  In der **NuGet Package Manager** Fenster, suchen Sie nach Microsoft.CppCoreCheck.  
  
     ![NuGet-Paket-Manager-Fenster zeigt CppCoreCheck-Paket](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3.  Wählen Sie das Paket Microsoft.CppCoreCheck, und wählen Sie dann die **installieren** , um die Regeln zu Ihrem Projekt hinzuzufügen.  
  
 Das NuGet-Paket Fügt eine zusätzliche MSBuild .targets-Datei zu Ihrem Projekt, das aufgerufen wird, wenn Sie die Codeanalyse auf Ihr Projekt aktivieren. Diese TARGETS-Datei hinzugefügt das Codeanalysetool in Visual Studio die C++ Core Check Regeln als eine zusätzliche Erweiterung.  
  
 Sie können die Codeanalyse auf Ihr Projekt aktivieren, indem Sie auswählen der **Codeanalyse für Build aktivieren** Kontrollkästchen in der **Codeanalyse** Teil der **Eigenschaftenseiten** Dialogfeld für Ihr Projekt.  
  
 ![Eigenschaftenseite für Code Analysis allgemeinen webanwendungseinstellungen](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
 Die C++ Core Check-Regeln werden die Standard-Regelsätze, die ausgeführt werden, wenn die Codeanalyse aktiviert ist. Da die C++ Core Check-Regeln in der Entwicklungsphase befinden, einige Regeln, möglicherweise nicht zur Verwendung in allen bereit, aber Sie werden möglicherweise während der Entwicklung informativ. Diese Regeln werden als experimentelle veröffentlicht. Sie können auswählen, ob die freigegebenen oder experimentellen Regeln in den Eigenschaften für Ihr Projekt auszuführen.  
  
 ![Eigenschaftenseite "Code Analysis Extensions-Einstellungen für](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
 Öffnen Sie zum Aktivieren oder deaktivieren den C++ Core Check Regelsätze, die **Eigenschaftenseiten** -Dialogfeld für Ihr Projekt. Klicken Sie unter **Konfigurationseigenschaften**, erweitern Sie **Codeanalyse**, **Erweiterungen**. Steuern Sie in der Dropdownliste neben **aktivieren C++ Core Check (freigegeben)** oder **aktivieren C++ Core Check (experimentell)**, wählen Sie **Ja** oder **keine**. Wählen Sie **OK** oder **übernehmen** zum Speichern der Änderungen.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Überprüfen Sie Typen, Grenzen und Lebensdauer  
 Der C++ Core Check-Paket enthält derzeit Überprüfungen für die [Typsicherheit](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), [umschließt Sicherheit](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds), und [Lebensdauer Sicherheit](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) Profile.  
  
 Hier ist ein Beispiel der Art von Problemen, die die C++ Core Check-Regeln finden können:  
  
```cpp  
// CoreCheckExample.cpp  
// Add CppCoreCheck package and enable code analysis in build for warnings.  
  
int main()  
{  
    int arr[10];           // warning C26494  
    int* p = arr;          // warning C26485  
  
    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1  
    {  
        int* q = p + 1;    // warning C26481 (suppressed)  
        p = q++;           // warning C26481 (suppressed)  
    }  
  
    return 0;  
}  
```  
  
 Dieses Beispiel zeigt ein Paar der Warnungen, die die C++ Core Check-Regeln finden können:  
  
-   C26494 ist Regel Type.5: immer ein Objekt zu initialisieren.  
  
-   C26485 ist Regel Bounds.3: kein Verfall von Array in einen Zeiger.  
  
-   C26481 ist Regel Bounds.1: Verwenden Sie keine Zeigerarithmetik. Verwenden Sie stattdessen `span`.  
  
 Wenn die C++ Core Check Code Analysis Rulesets sind installiert und aktiviert, wenn Sie diesen Code kompilieren, die ersten beiden Warnungen werden ausgegeben, aber die dritte unterdrückt wird. Hier ist die Buildausgabe aus dem Beispielcode:  
  
 **1 >---Erstellen gestartet: Projekt: CoreCheckExample, Konfiguration: Debug Win32:**  
**----**  
**1 > CoreCheckExample.cpp**  
**1 > CoreCheckExample.vcxproj-C:\Users\username\documents\visual Studio 2015\P >.**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1 > CoreCheckExample.vcxproj-C:\Users\username\documents\visual Studio 2015\P >.**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.PDB (vollständige PDB)**  
**c:\users\username\documents\visual Studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(6): Warnung C26494: Variable 'Arr' ist Uninitializ**  
**ED immer ein Objekt initialisiert werden. (type.5: http://go.microsoft.com/fwlink/p/?Link**  
**ID = 620421)**  
**c:\users\username\documents\visual Studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(7): C26485 Warnung: der Ausdruck 'Arr': kein Array zu**  
 **zeigerverfall. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)**  
**==== Build: 1 erfolgreich, 0 fehlerhaft, 0 aktuell, 0 übersprungen ====** der C++ Core Guidelines gibt es lassen sich besser und sicherer Code zu schreiben. Wenn Sie eine Instanz verfügen, in denen eine Regel oder ein Profil nicht angewendet werden sollte, ist es jedoch einfach direkt im Code unterdrückt werden sollen. Sie können die `gsl::suppress` Attribut C++ Core Check verhindern, erkennen und die berichterstellung einer Verletzung einer Regel in den folgenden Codeblock. Sie können einzelne Anweisungen aus, um bestimmte Regeln unterdrücken kennzeichnen. Können Sie auch das gesamte begrenzungsprofil unterdrücken, durch das Schreiben von `[[gsl::suppress(bounds)]]` ohne eine spezielle regelzahl.  
  
## <a name="use-the-guideline-support-library"></a>Verwenden Sie die Richtlinie-Unterstützungsbibliothek  
 Das Microsoft.CppCoreCheck NuGet-Paket wird auch ein Paket mit Microsoft Implementierung von Guideline Support Library (GSL) installiert. GSL steht auch in eigenständiger Form an [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). Diese Bibliothek ist hilfreich, wenn Sie den Core Guidelines möchten. GSL enthält die Definitionen, mit denen Sie die Fehler verursachenden Konstrukte mit sicherer Alternativen zu ersetzen. Sie können z. B. Ersetzen einer `T*, length` -Paar von Parametern mit dem `span<T>` Typ. GSL ist open Source, deshalb sollten Sie einen Blick auf die Bibliothekquellen, kommentieren oder beitragen können, das Projekt finden Sie unter [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).



