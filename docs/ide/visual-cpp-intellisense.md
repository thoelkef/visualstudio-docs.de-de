---
title: "Visual C++ Intellisense | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9d7c6414-4e6c-4889-a74c-a6033795eccc
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual C++ Intellisense
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In Visual Studio 2015 steht IntelliSense für einzelne Codedateien sowie für Dateien in Projekten zur Verfügung.  In plattformübergreifenden Projekten stehen einige IntelliSense\-Funktionen in CPP\- und C\-Dateien im gemeinsam genutzten Projektcode zur Verfügung, auch wenn Sie sich in einem Android\- oder iOS\-Kontext befinden.  
  
## IntelliSense\-Funktionen in C\+\+  
 IntelliSense ist ein Name für eine Gruppe von Funktionen, die die Codierung erleichtern.  Da verschiedene Personen unterschiedliche Vorstellungen dazu haben, was praktisch ist, können im Prinzip alle IntelliSense\-Funktionen auf der Eigenschaftenseite im **Text\-Editor, C\/C\+\+, Erweitert** aktiviert oder deaktiviert werden .  
  
 ![Tools, Optionen, Text&#45;Editor, C&#47;C&#43;&#43;, Erweitert](../ide/media/sintellisensecpptoolsoptions.png "sIntelliSenseCppToolsOptions")  
  
 Sie können die in der folgenden Abbildung aufgeführten Menüelemente und Tastenkombinationen für den Zugriff auf IntelliSense verwenden.  
  
 ![Visual C&#43;&#43;&#45;IntelliSense&#45;Menü](../ide/media/vs2015_cpp_intellisense_menu.png "vs2015\_cpp\_intellisense\_menu")  
  
### Anweisungsvervollständigung und Memberliste  
 Wenn Sie beginnen, ein Schlüsselwort, einen Typ, eine Funktion, einen Variablennamen oder ein anderes Programmelement einzugeben, das der Compiler erkennt, bietet der Editor die Vervollständigung des Worts an.  
  
 Eine Liste der Symbole und ihrer Bedeutungen finden Sie unter [Symbole in der Klassenansicht und im Objektbrowser](../ide/class-view-and-object-browser-icons.md).  
  
 ![Visual C&#43;&#43;&#45;Fenster „Wort vervollständigen“](../ide/media/vs2015_cpp_complete_word.png "vs2015\_cpp\_complete\_word")  
  
 Wenn zum ersten Mal die Memberliste aufgerufen wird, zeigt sie nur Member am, auf die für den aktuellen Kontext zugegriffen werden kann.  Wenn Sie danach **STRG\+J** verwenden, werden alle Member unabhängig vom Zugriff angezeigt.  Wenn Sie sie ein drittes Mal aufrufen, wird eine noch größere Liste der Programmelemente angezeigt.  Sie können die Anweisungsvervollständigung auf der Seite **C\/C\+\+ Allgemeine Optionen** deaktivieren.  
  
 ![Visual C&#43;&#43;&#45;Memberliste](../ide/media/vs2015_cpp_list_members.png "vs2015\_cpp\_list\_members")  
  
### Parameterhilfe  
 Wenn Sie eine öffnende geschweifte Klammer eines Funktionsaufrufs oder spitze Klammer in einer Variablendeklaration einer Klassenvorlage eingeben, zeigt der Editor ein kleines Fenster mit den Parametertypen für jede Überladung der Funktion oder des Konstruktors an.  Der „current“\-Parameter, der auf der Cursorposition basiert, wird in Fettschrift angezeigt.  Sie können die Anweisungsvervollständigung auf der Seite **C\/C\+\+ Allgemeine Optionen** deaktivieren.  
  
 ![Hilfe zu Visual C&#43;&#43;&#45;Parametern](../ide/media/vs_2015_cpp_param_help.png "vs\_2015\_cpp\_param\_help")  
  
### QuickInfo  
 Wenn Sie mit dem Mauszeiger auf eine Variable zeigen, wird ein kleines Fenster angezeigt, in dem die Informationen und der Header, in dem der Typ definiert wird, angezeigt werden.  Zeigen Sie auf einen Funktionsaufruf, um die Signatur der Funktion anzuzeigen.  Sie können die QuickInfo auf der Seite **Text\-Editor, C\/C\+\+, Erweitert** deaktivieren.  
  
 ![Visual C&#43;&#43;&#45;QuickInfo](../ide/media/vs2015_cpp_quickinfo.png "vs2015\_cpp\_quickInfo")  
  
## Fehlerwellenlinien  
 Wellenlinien unter einem Programmelement \(Variable, Schlüsselwort, geschweifte Klammer, Typname usw.\) weisen auf einen Fehler oder einen möglichen Fehler im Code hin.  Beim Schreiben einer Vorwärtsdeklaration wird eine grüne Wellenlinie eingeblendet, um Sie daran zu erinnern, dass Sie immer noch die Implementierung schreiben müssen.  Eine violette Wellenlinie wird in einem freigegebenen Projekt eingeblendet, wenn ein Fehler im Code vorliegt, der gerade nicht aktiv ist, z. B. wenn Sie im Windows\-Kontext arbeiten, aber etwas eingeben, das in einem Android\-Kontext einen Fehler auslösen würde.  Eine rote Wellenlinie weist auf einen Compilerfehler oder eine Warnung im aktiven Code hin, den bzw. die Sie behandeln müssen.  
  
 ![Visual C&#43;&#43;&#45;Fehlerwellenlinien](../ide/media/vs2015_cpp_error_quiggles.png "vs2015\_cpp\_error\_quiggles")  
  
## Farbliche Kennzeichnung von Code und Schriftarten  
 Die standardmäßigen Farben und Schriftarten können mithilfe der Eigenschaftenseite **Umgebung, Schriftarten und Farben** geändert werden.  Hier können Sie die Schriftarten für viele UI\-Fenster ändern, nicht nur für den Editor.  Die Einstellungen, die spezifisch für C\+\+ sind, beginnen mit „C\+\+“; die anderen Einstellungen gelten für alle Sprachen.  
  
## Plattformübergreifendes IntelliSense  
 In einem Projekt mit freigegebenem Code stehen einige IntelliSense\-Funktionen, wie z. B. Wellenlinien, sogar bei der Arbeit in einem Android\-Kontext zur Verfügung.  Wenn Sie Code schreiben, der zu einem Fehler in einem inaktiven Projekt führen würde, zeigt IntelliSense weiterhin Wellenlinien an, aber in einer anderen Farbe als Wellenlinien für Fehler im aktuellen Kontext.  
  
 Hier ist eine OpenGLES\-Anwendung, die zum Erstellen für Android und iOS konfiguriert ist.  Die Abbildung veranschaulicht den bearbeiteten freigegebenen Code.  In der ersten Abbildung stellt Android das aktive Projekt dar:  
  
 ![Das Android&#45;Projekt ist das aktive Projekt.](../ide/media/intellisensecppcrossplatform.png "IntelliSenseCppCrossPlatform")  
  
 Beachten Sie Folgendes:  
  
-   Die \#else\-Verzweigung in Zeile 8 ist ausgegraut und stellt den aktiven Bereich dar, da \_\_ANDROID\_\_ für das Android\-Projekt definiert ist.  
  
-   Die Variable für die Grußformel in Zeile 11 wird mit dem HELLO\-Bezeichner initialisiert, der eine violette Wellenlinie hat.  Der Grund hierfür ist, dass kein HELLO\-Bezeichner in dem aktuell inaktiven iOS\-Projekt definiert ist.  Während im Android\-Projekt Zeile 11 kompilieren wird, ist dies im iOS\-Projekt nicht der Fall.  Da es sich um freigegebenen Code handelt, sollten Sie diesen auch dann ändern, wenn er in der aktuell aktiven Konfiguration kompiliert wird.  
  
-   Zeile 12 weist eine rote Wellenlinie am BYE\-Bezeichner auf; dieser Bezeichner ist in dem aktuell ausgewählten aktiven Projekt nicht definiert.  
  
 Ändern Sie nun das aktive Projekt in iOS.StaticLibrary, und achten Sie auf die Änderungen an den Wellenlinien.  
  
 ![iOS ist als das aktive Projekt ausgewählt.](../ide/media/intellisensecppcrossplatform2.png "IntelliSenseCppCrossPlatform2")  
  
 Beachten Sie Folgendes:  
  
-   Die \#ifdef\-Verzweigung in Zeile 6 ist ausgegraut und stellt den inaktiven Bereich dar, da \_\_ANDROID\_\_ für das iOS\-Projekt nicht definiert ist.  
  
-   Die Variable für die Grußformel in Zeile 11 wird mit dem HELLO\-Bezeichner initialisiert, der nun eine rote Wellenlinie hat.  Der Grund hierfür ist, dass kein HELLO\-Bezeichner in dem aktuell aktiven iOS\-Projekt definiert ist.  
  
-   Zeile 12 weist der BYE\-Bezeichner eine violette Wellenlinie auf; dieser Bezeichner ist im aktuell inaktiven Android.NativeActivity\-Projekt nicht definiert.  
  
## IntelliSense mit Einzeldatei  
 Wenn Sie eine einzelne Datei außerhalb von Projekten öffnen, können Sie weiterhin IntelliSense verwenden.  Sie können bestimmte Funktionen aktivieren oder deaktivieren, indem Sie zu **Text\-Editor, C\/C\+\+, Erweitert** wechseln und IntelliSense\-Funktionen aktivieren oder deaktivieren.  Suchen Sie zum Konfigurieren von IntelliSense für einzelne Dateien, die nicht Teil eines Projekts sind, nach **IntelliSense und Suchen nach Nicht\-Projektdateien** in dem Abschnitt **Erweitert**.  Weitere Informationen finden Sie unter [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/de-de/499cb66f-7df1-45d6-8b6b-33d94fd1f17c).  
  
 ![Visual C&#43;&#43;IntelliSense mit Einzeldatei](../ide/media/vs2015_cpp_single_file_intellisense.png "vs2015\_cpp\_single\_file\_intellisense")  
  
 Standardmäßig verwendet eine einzelne IntelliSense\-Datei die standardmäßigen Includeverzeichnisse für die Suche nach Headerdateien.  Öffnen Sie zum Hinzufügen weiterer Verzeichnisse das Kontextmenü für den Knoten „Projektmappe“, und fügen Sie Ihr Verzeichnis zur Liste **Quellcode debuggen** hinzu, wie in der folgenden Abbildung dargestellt:  
  
 ![Hinzufügen eines Pfads in eine Headerdatei.](../ide/media/intellisensedebugyourcode.png "IntelliSenseDebugYourCode")  
  
## Siehe auch  
 [Verwenden von IntelliSense](../ide/using-intellisense.md)