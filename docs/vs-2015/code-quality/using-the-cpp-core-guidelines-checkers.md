---
title: Verwenden der C++ Core Guidelines Checker | Microsoft-Dokumentation
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: fffa4cec6a2bd7a340b90776ac20dc486f28045b
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173554"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Verwenden der Überprüfungen für C++ Core Guidelines
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die C++ Core Guidelines sind ein portabler Satz an Richtlinien, Regeln und bewährten Methoden zum Programmieren in C++, die von C++-Experten und-Designern erstellt werden.  Visual Studio unterstützt jetzt Add-in-Pakete, die zusätzliche Regeln für die Code Analysetools erstellen, um Ihren Code auf die Konformität mit dem C++ Core Guidelines zu überprüfen und Verbesserungen vorzuschlagen.  
  
## <a name="the-c-core-guidelines-project"></a>Das C++ Core Guidelines Projekt  
 Die C++ Core Guidelines von Bjarne Stroustrup und anderen erstellt, sind ein Leitfaden zur sicheren und effektiven Verwendung moderner C++. Die Richtlinien betonen die statische Typsicherheit und die Ressourcensicherheit. Sie identifizieren Möglichkeiten, um die Fehler anfälligsten Teile der Sprache zu eliminieren oder zu minimieren, und legen fest, wie Sie Ihren Code auf zuverlässige Weise einfacher und leistungsfähiger machen können. Diese Richtlinien werden von der Standard mäßigen C++ Foundation verwaltet. Weitere Informationen finden Sie in der Dokumentation, [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)und Zugriff auf die C++ Core Guidelines Dokumentationsprojekt Dateien auf [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
 Microsoft unterstützt den C++ Core Guidelines Aufwand, indem C++ Core Check Regelsätze für die Code Analyse vorgenommen werden, die Sie Ihren Projekten mithilfe eines nuget-Pakets hinzufügen können. Das Paket heißt "Microsoft. cppcorecheck" und ist unter verfügbar [https://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck) . Für dieses Paket ist mindestens Visual Studio 2015 mit installiertem Update 1 erforderlich.  
  
 Das Paket installiert auch ein anderes Paket als Abhängigkeit, eine nur-Header-Richtlinien-Unterstützungs Bibliothek (GSL). Die GSL ist auch auf GitHub unter verfügbar [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Aktivieren der C++ Core Check Richtlinien in der Code Analyse  
 Um die C++ Core Check Code Analysetools zu aktivieren, installieren Sie das nuget-Paket "Microsoft. cppcorecheck" in jedem C++-Projekt, das Sie in Visual Studio überprüfen möchten.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>So fügen Sie dem Projekt das Microsoft. cppcorecheck-Paket hinzu  
  
1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf, um das Kontextmenü Ihres Projekts in der Projekt Mappe zu öffnen, der Sie das Paket hinzufügen möchten. Wählen Sie **nuget-Pakete verwalten** , um den **nuget-Paket-Manager**zu öffnen.  
  
2. Suchen Sie im Fenster **nuget-Paket-Manager** nach Microsoft. cppcorecheck.  
  
    ![Das Fenster des nuget-Paket-Managers zeigt das cppcorecheck-Paket](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Wählen Sie das Paket Microsoft. cppcorecheck aus, und klicken Sie dann auf die Schaltfläche **Installieren** , um die Regeln zu Ihrem Projekt hinzuzufügen.  
  
   Das nuget-Paket fügt dem Projekt eine zusätzliche MSBuild. targets-Datei hinzu, die aufgerufen wird, wenn Sie die Code Analyse für Ihr Projekt aktivieren. Diese targets-Datei fügt die C++ Core Check Regeln als zusätzliche Erweiterung zum Visual Studio-Code Analysetool hinzu.  
  
   Sie können die Code Analyse für Ihr Projekt aktivieren, indem Sie im Dialogfeld " **Code Analyse** " des Dialog Felds " **Eigenschaften Seiten** " für Ihr Projekt das Kontrollkästchen " **Code Analyse in Build aktivieren" aktivieren** .  
  
   ![Eigenschaften Seite für allgemeine Code Analyse Einstellungen](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   Die C++ Core Check Regeln werden Teil der Standardregel Sätze, die ausgeführt werden, wenn die Code Analyse aktiviert ist. Da sich die C++ Core Check Regeln in der Entwicklungsphase befinden, können einige Regeln möglicherweise nicht für den gesamten Code verwendet werden, sind während der Entwicklung jedoch möglicherweise informativ. Diese Regeln werden als experimentell veröffentlicht. Sie können auswählen, ob Sie die veröffentlichten oder experimentellen Regeln in den Eigenschaften für das Projekt ausführen möchten.  
  
   ![Eigenschaften Seite für die Einstellungen für die Code Analyse Erweiterungen](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Öffnen Sie das Dialogfeld **Eigenschaften Seiten** für das Projekt, um die C++ Core Check Regelsätze zu aktivieren oder zu deaktivieren. Erweitern Sie unter **Konfigurations Eigenschaften**die Option **Code Analyse**, **Erweiterungen**. Wählen Sie im Dropdown-Steuerelement neben **C++ Core Check aktivieren (freigegeben)** oder **C++ Core Check aktivieren (experimentell)** die Option **Ja** oder **Nein**aus. Wählen Sie **OK** oder **anwenden** aus, um die Änderungen zu speichern.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Überprüfen von Typen, Begrenzungen und Lebens dauern  
 Das C++ Core Check-Paket enthält derzeit für die Profile für die [Typsicherheit](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), die [Sicherheits](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)Stufe und die [Lebensdauer Sicherheit](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) .  
  
 Im folgenden finden Sie ein Beispiel für die Art der Probleme, die die C++ Core Check Regeln finden können:  
  
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
  
 In diesem Beispiel werden einige der Warnungen veranschaulicht, die die C++ Core Check Regeln finden können:  
  
- C26494 ist vom Regeltyp. 5: Initialisieren Sie immer ein Objekt.  
  
- C26485 ist Regel Begrenzungen. 3: kein Array-zu-Zeiger-Zerfall.  
  
- C26481 ist Regel Begrenzungen. 1: Verwenden Sie keine Zeigerarithmetik. Verwenden Sie stattdessen `span`.  
  
  Wenn die C++ Core Check Code Analyse-RuleSets installiert und aktiviert sind, wenn Sie diesen Code kompilieren, werden die ersten beiden Warnungen ausgegeben, das dritte wird jedoch unterdrückt. Dies ist die Buildausgabe des Beispielcodes:  
  
**1>------Build wurde gestartet: Projekt: corecheckexample, Konfiguration: Debuggen von Win32--**  
**----**  
**1> corecheckexample. cpp**  
**1> corecheckexample. vcxproj-> c:\users\username\documents\visual Studio 2015 \ P**  
**rojecung\corecheckexample\debug \ corecheckexample.exe**  
**1> corecheckexample. vcxproj-> c:\users\username\documents\visual Studio 2015 \ P**  
**rojecz\corecheckexample\debug \ corecheckexample.pdb (vollständige PDB-Datei)**  
**c:\users\username\documents\visual Studio 2015 \ project\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (6): Warnung C26494: die Variable ' arr ' ist nicht Initialisierer.**  
**Ed. Initialisieren Sie immer ein-Objekt. (Type. 5: https: \/ /go.Microsoft.com/fwlink/p/?Link**  
**ID = 620421)**  
**c:\users\username\documents\visual Studio 2015 \ project\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (7): Warnung C26485: Ausdruck ' arr ': kein Array für**  
**Zeiger Verfall. (Bounds. 3: https: \/ /go.Microsoft.com/fwlink/p/?linkid=620415)**  
**========== Build: 1 erfolgreich, 0 fehlerhaft, 0 aktuell, 0 übersprungen ==========** 

Die C++ Core Guidelines sind vorhanden, damit Sie besseren und sichereren Code schreiben können. Wenn Sie jedoch über eine Instanz verfügen, bei der eine Regel oder ein Profil nicht angewendet werden sollte, ist es einfach, Sie direkt im Code zu unterdrücken. Sie können das- `gsl::suppress` Attribut verwenden, um zu verhindern, dass C++ Core Check jegliche Verstöße gegen eine Regel im folgenden Codeblock erkennen und melden. Sie können einzelne Anweisungen markieren, um bestimmte Regeln zu unterdrücken. Sie können sogar das gesamte Begrenzungen-Profil unterdrücken, indem Sie schreiben, `[[gsl::suppress(bounds)]]` ohne eine bestimmte Regel Nummer einzubeziehen.  
  
## <a name="use-the-guideline-support-library"></a>Verwenden der Unterstützungs Bibliothek für Richtlinien  
 Das nuget-Paket Microsoft. cppcorecheck installiert auch ein Paket, das die Microsoft-Implementierung der Richtlinien-Unterstützungs Bibliothek (GSL) enthält. Die GSL ist auch im eigenständigen Formular unter verfügbar [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl) . Diese Bibliothek ist hilfreich, wenn Sie den grundlegenden Richtlinien folgen möchten. Die GSL enthält Definitionen, mit denen Sie fehleranfällige Konstrukte durch sicherere Alternativen ersetzen können. Beispielsweise können Sie ein `T*, length` Parameter paar durch den `span<T>` Typ ersetzen. Die GSL ist Open Source. Wenn Sie also die Bibliothek Quellen, den Kommentar oder einen Beitrag ansehen möchten, finden Sie das Projekt unter [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .
