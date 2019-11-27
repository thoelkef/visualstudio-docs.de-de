---
title: Verwenden der C++ wichtigsten Leitfäden für Richtlinien | Microsoft-Dokumentation
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: ccc44b77c4524e7d707ce3fe407d204d729017ff
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291239"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Verwenden der Überprüfungen für C++ Core Guidelines
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die C++ wichtigsten Richtlinien sind ein portabler Satz an Richtlinien, Regeln und bewährten Methoden zum C++ Programmieren C++ in, die von Experten und Designern erstellt werden.  Visual Studio unterstützt jetzt Add-in-Pakete, die zusätzliche Regeln für die Code Analysetools erstellen, um Ihren Code auf C++ Konformität mit den grundlegenden Richtlinien zu überprüfen und Verbesserungen vorzuschlagen.  
  
## <a name="the-c-core-guidelines-project"></a>Das C++ Kern Leitlinien-Projekt  
 Die C++ grundlegenden Richtlinien werden von Bjarne Stroustrup und anderen erstellt und sind ein Leitfaden C++ zur sicheren und effektiven Verwendung von modern. Die Richtlinien betonen die statische Typsicherheit und die Ressourcensicherheit. Sie identifizieren Möglichkeiten, um die Fehler anfälligsten Teile der Sprache zu eliminieren oder zu minimieren, und legen fest, wie Sie Ihren Code auf zuverlässige Weise einfacher und leistungsfähiger machen können. Diese Richtlinien werden von der Standard C++ Foundation verwaltet. Weitere Informationen finden Sie in der Dokumentation, [ C++ den grundlegenden Richtlinien](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)und C++ dem Zugriff auf die Dokumentationsprojekt Dateien der wichtigsten Richtlinien auf [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
 Microsoft unterstützt C++ den Kern Leitlinien Aufwand C++ durch die Erstellung von Kerncode Analyse-Regelsätzen, die Sie Ihren Projekten mithilfe eines nuget-Pakets hinzufügen können. Das Paket heißt "Microsoft. cppcorecheck" und ist unter [https://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck)verfügbar. Für dieses Paket ist mindestens Visual Studio 2015 mit installiertem Update 1 erforderlich.  
  
 Das Paket installiert auch ein anderes Paket als Abhängigkeit, eine nur-Header-Richtlinien-Unterstützungs Bibliothek (GSL). Die GSL ist auch auf GitHub unter [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)verfügbar.  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Aktivieren der C++ grundlegenden Check-Richtlinien in der Code Analyse  
 Installieren Sie das C++ nuget-Paket "Microsoft. cppcorecheck" in jedem C++ Projekt, das Sie in Visual Studio überprüfen möchten, um die Analysetools für die Kern Überprüfung zu aktivieren.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>So fügen Sie dem Projekt das Microsoft. cppcorecheck-Paket hinzu  
  
1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf, um das Kontextmenü Ihres Projekts in der Projekt Mappe zu öffnen, der Sie das Paket hinzufügen möchten. Wählen Sie **nuget-Pakete verwalten** , um den **nuget-Paket-Manager**zu öffnen.  
  
2. Suchen Sie im Fenster **nuget-Paket-Manager** nach Microsoft. cppcorecheck.  
  
    ![Das Fenster des nuget-Paket-Managers zeigt das cppcorecheck-Paket](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Wählen Sie das Paket Microsoft. cppcorecheck aus, und klicken Sie dann auf die Schaltfläche **Installieren** , um die Regeln zu Ihrem Projekt hinzuzufügen.  
  
   Das nuget-Paket fügt dem Projekt eine zusätzliche MSBuild. targets-Datei hinzu, die aufgerufen wird, wenn Sie die Code Analyse für Ihr Projekt aktivieren. Diese targets-Datei fügt die C++ grundlegenden Prüfregeln als zusätzliche Erweiterung zum Visual Studio-Code Analysetool hinzu.  
  
   Sie können die Code Analyse für Ihr Projekt aktivieren, indem Sie im Dialogfeld " **Code Analyse** " des Dialog Felds " **Eigenschaften Seiten** " für Ihr Projekt das Kontrollkästchen " **Code Analyse in Build aktivieren" aktivieren** .  
  
   ![Eigenschaften Seite für allgemeine Code Analyse Einstellungen](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   Die C++ Regeln für die Kern Prüfung werden Teil der Standardregel Sätze, die ausgeführt werden, wenn die Code Analyse aktiviert ist. Da sich C++ die grundlegenden Prüfregeln in der Entwicklung befinden, sind einige Regeln möglicherweise nicht für den gesamten Code einsatzbereit, können aber während der Entwicklung informativ sein. Diese Regeln werden als experimentell veröffentlicht. Sie können auswählen, ob Sie die veröffentlichten oder experimentellen Regeln in den Eigenschaften für das Projekt ausführen möchten.  
  
   ![Eigenschaften Seite für die Einstellungen für die Code Analyse Erweiterungen](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Öffnen Sie das Dialogfeld C++ **Eigenschaften Seiten** für das Projekt, um die kernregel Sätze für die Prüfung zu aktivieren oder zu deaktivieren. Erweitern Sie unter **Konfigurations Eigenschaften**die Option **Code Analyse**, **Erweiterungen**. Wählen Sie im Dropdown-Steuer **Element C++ neben enable Core Check (veröffentlicht)** oder **enable C++ Core Check (experimentell)** die Option **Ja** oder **Nein**aus. Wählen Sie **OK** oder **anwenden** aus, um die Änderungen zu speichern.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Überprüfen von Typen, Begrenzungen und Lebens dauern  
 Das C++ Core-Überprüfungspaket enthält derzeit die Prüf Punkt Informationen für die Profile für die [Typsicherheit](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), die [Begrenzungen](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)und die [Lebensdauer Sicherheit](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) .  
  
 Im folgenden finden Sie ein Beispiel für die Art der Probleme C++ , die die grundlegenden Prüfregeln finden können:  
  
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
  
 In diesem Beispiel werden einige der Warnungen veranschaulicht, die C++ die grundlegenden Prüfregeln finden können:  
  
- C26494 ist vom Regeltyp. 5: Initialisieren Sie immer ein Objekt.  
  
- C26485 ist Regel Begrenzungen. 3: kein Array-zu-Zeiger-Zerfall.  
  
- C26481 ist Regel Begrenzungen. 1: Verwenden Sie keine Zeigerarithmetik. Verwenden Sie stattdessen `span` .  
  
  Wenn die C++ Code Analyse-Regelsätze der Kern Überprüfung installiert und aktiviert sind, wenn Sie diesen Code kompilieren, werden die ersten beiden Warnungen ausgegeben, das dritte wird jedoch unterdrückt. Dies ist die Buildausgabe des Beispielcodes:  
  
**1 >------Build wurde gestartet: Projekt: corecheckexample, Konfiguration: Debuggen von Win32--**  
**----**  
**1 > corecheckexample. cpp**  
**1 > corecheckexample. vcxproj-> c:\users\username\documents\visual Studio 2015 \ P**  
**rojecung\corecheckexample\debug \ corecheckexample.exe**  
**1 > corecheckexample. vcxproj-> c:\users\username\documents\visual Studio 2015 \ P**  
**rojecz\corecheckexample\debug \ corecheckexample.pdb (vollständige PDB-Datei)**  
**c:\users\username\documents\visual Studio 2015 \ project\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (6): Warnung C26494: die Variable ' arr ' ist nicht Initialisierer.**  
**Ed. Initialisieren Sie immer ein-Objekt. (Type. 5: https://go.microsoft.com/fwlink/p/?Link**  
**ID = 620421)**  
**c:\users\username\documents\visual Studio 2015 \ project\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (7): Warnung C26485: Ausdruck ' arr ': kein Array für**  
**Zeiger Verfall. (Begrenzungen. 3: https://go.microsoft.com/fwlink/p/?LinkID=620415)**  
= = = = = = = = = = **Build: 1 erfolgreich, 0 fehlgeschlagen, 0 aktuell, 0 übersprungen = =** = = = = = = = = = Die C++ wichtigsten Richtlinien sind vorhanden, die Ihnen helfen, besseren und sichereren Code zu schreiben. Wenn Sie jedoch über eine Instanz verfügen, bei der eine Regel oder ein Profil nicht angewendet werden sollte, ist es einfach, Sie direkt im Code zu unterdrücken. Sie können das `gsl::suppress`-Attribut verwenden, C++ um zu verhindern, dass die Kern Überprüfung eine Verletzung einer Regel im folgenden Codeblock erkennt und meldet. Sie können einzelne Anweisungen markieren, um bestimmte Regeln zu unterdrücken. Sie können sogar das gesamte Begrenzungen-Profil unterdrücken, indem Sie `[[gsl::suppress(bounds)]]` ohne Angabe einer bestimmten Regel Nummer schreiben.  
  
## <a name="use-the-guideline-support-library"></a>Verwenden der Unterstützungs Bibliothek für Richtlinien  
 Das nuget-Paket Microsoft. cppcorecheck installiert auch ein Paket, das die Microsoft-Implementierung der Richtlinien-Unterstützungs Bibliothek (GSL) enthält. Die GSL ist auch im eigenständigen Formular unter [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl)verfügbar. Diese Bibliothek ist hilfreich, wenn Sie den grundlegenden Richtlinien folgen möchten. Die GSL enthält Definitionen, mit denen Sie fehleranfällige Konstrukte durch sicherere Alternativen ersetzen können. Beispielsweise können Sie ein `T*, length` Parameter paar durch den `span<T>`-Typ ersetzen. Die GSL ist Open Source. Wenn Sie also die Bibliothek Quellen, den Kommentar oder einen Beitrag ansehen möchten, finden Sie das Projekt unter [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).
