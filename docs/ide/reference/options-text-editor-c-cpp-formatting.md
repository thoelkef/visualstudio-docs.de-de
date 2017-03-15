---
title: "Optionen, Text-Editor, C/C++, Formatierung | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Text-Editor-Optionen (Dialogfeld), Formatierung"
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Optionen, Text-Editor, C/C++, Formatierung
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ermöglicht es Ihnen, das Standardverhalten des Code\-Editors zu ändern, wenn Sie in C oder C\+\+ programmieren.  
  
 Um diese Seite zu öffnen, klicken Sie im linken Fenster auf das Dialogfeld **Optionen**, erweitern Sie den **Text\-Editor** und **C\/C\+\+** und klicken dann auf **Formatieren**.  
  
> [!NOTE]
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Die von Ihnen verwendete Visual Studio\-Edition und die Einstellungen legen diese Elemente fest.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## C\/C\+\+\-Optionen  
 **Automatische QuickInfos aktivieren**  
 Aktiviert oder deaktiviert die IntelliSense\-Funktion QuickInfo.  
  
## Inaktiver Code  
 **Inaktive Codeblöcke anzeigen**  
 Code, der aufgrund von `#ifdef`\-Deklarationen inaktiv ist, wird eingefärbt, damit inaktiver Code besser erkennbar ist.  
  
 **Inaktive Codedeckkraft deaktivieren**  
 Inaktiver Code kann mit Farbe statt Transparenz gekennzeichnet werden.  
  
 **Deckkraftprozentsatz für inaktiven Code**  
 Der Deckkraftgrad für inaktive Codeblöcke kann angepasst werden.  
  
## Indentation  
 **Geschweifte Klammern einrücken**  
 Sie können konfigurieren, wie geschweifte Klammern ausgerichtet werden, wenn Sie die EINGABETASTE drücken, nachdem Sie einen Codeblock, z. B. eine Funktion oder eine `for`\-Schleife, begonnen haben.  Die geschweiften Klammern können entweder am ersten Zeichen des Codeblocks ausgerichtet oder eingezogen sein.  
  
 **Automatischer Einzug auf Registerkarte**  
 Sie können konfigurieren, was auf der aktuellen Codezeile geschieht, wenn Sie die TAB\-TASTE drücken.  Entweder wird die Zeile eingezogen oder ein Tabulator eingefügt.  
  
## Verschiedenes  
 **Bemerkungen im Fenster Aufgabenliste auflisten**  
 Der Editor kann geöffnete Quelldateien in den Kommentaren nach voreingestellten Wörtern scannen.  Er erstellt einen Eintrag im Fenster **Aufgabenliste** für beliebige Schlüsselwörter, die gefunden werden.  
  
 **Zugehörige Token hervorheben**  
 Wenn sich der Cursor neben einer geschweiften Klammer befindet, kann der Editor die entsprechende geschweifte Klammer hervorheben, damit Sie den enthaltenen Code leichter sehen können.  
  
## Gliedern  
 **Beim Öffnen von Dateien in Gliederungsmodus wechseln**  
 Wenn Sie eine Datei im Text\-Editor öffnen, können Sie die Gliederungsfunktion aktivieren.  Weitere Informationen finden Sie unter [Gliedern](../../ide/outlining.md).  Wenn diese Option ausgewählt ist, wird die Gliederungsfunktion beim Öffnen einer Datei aktiviert.  
  
 **Automatische Gliederung von \#pragma\-Bereich\-Blöcken**  
 Wenn diese Option aktiviert wird, wird die automatische Gliederung für [Pragma\-Direktiven](/visual-cpp/preprocessor/pragma-directives-and-the-pragma-keyword) aktiviert.  Damit können Sie Pragmabereichsblocks im gegliederten Modus erweitern oder reduzieren.  
  
 **Automatische Gliederung von Anweisungsblöcken**  
 Wenn diese Option ausgewählt ist, wird die automatische Gliederung für die folgenden Anweisungskonstrukte aktiviert:  
  
-   [if\-else](/dotnet/csharp/language-reference/keywords/if-else)  
  
-   [switch\-Anweisung \(C\+\+\)](/visual-cpp/cpp/switch-statement-cpp)  
  
-   [while\-Anweisung \(C\+\+\)](/visual-cpp/cpp/while-statement-cpp)  
  
## Siehe auch  
 [Allgemein, Umgebung, Dialogfeld "Optionen"](../../ide/reference/general-environment-options-dialog-box.md)   
 [Verwenden von IntelliSense](../../ide/using-intellisense.md)