---
title: Optionen, Text-Editor, C/C++, Formatierung | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs: CPP
helpviewer_keywords: Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5a96a88ca7edd21989764c843f57c01a7bf03b0a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="options-text-editor-cc-formatting"></a>Optionen, Text-Editor, C/C++, Formatierung
Ermöglicht es Ihnen, das Standardverhalten des Code-Editors zu ändern, wenn Sie in C oder C++ programmieren.  
  
 Um diese Seite zu öffnen, klicken Sie im linken Fenster auf das Dialogfeld **Optionen**, erweitern Sie den **Text-Editor** und **C/C++** und klicken dann auf **Formatieren**.  
  
> [!NOTE]
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="cc-options"></a>C/C++-Optionen  
 **Automatische QuickInfos aktivieren**  
 Aktiviert oder deaktiviert die IntelliSense-Funktion QuickInfo.  
  
## <a name="inactive-code"></a>Inaktiver Code  
 **Inaktive Codeblöcke anzeigen**  
 Code, der aufgrund von `#ifdef`-Deklarationen inaktiv ist, wird eingefärbt, damit inaktiver Code besser erkennbar ist.  
  
 **Inaktive Codedeckkraft deaktivieren**  
 Inaktiver Code kann mit Farbe statt Transparenz gekennzeichnet werden.  
  
 **Deckkraftprozentsatz für inaktiven Code**  
 Der Deckkraftgrad für inaktive Codeblöcke kann angepasst werden.  
  
## <a name="indentation"></a>Indentation  
 **Geschweifte Klammern einrücken**  
 Sie können konfigurieren, wie geschweifte Klammern ausgerichtet werden, wenn Sie die EINGABETASTE drücken, nachdem Sie einen Codeblock, z. B. eine Funktion oder eine `for`-Schleife, begonnen haben. Die geschweiften Klammern können entweder am ersten Zeichen des Codeblocks ausgerichtet oder eingezogen sein.  
  
 **Automatischer Einzug auf Registerkarte**  
 Sie können konfigurieren, was auf der aktuellen Codezeile geschieht, wenn Sie die TAB-TASTE drücken. Entweder wird die Zeile eingezogen oder ein Tabulator eingefügt.  
  
## <a name="miscellaneous"></a>Verschiedenes  
 **Bemerkungen im Fenster Aufgabenliste auflisten**  
 Der Editor kann geöffnete Quelldateien in den Kommentaren nach voreingestellten Wörtern scannen. Er erstellt einen Eintrag im Fenster **Aufgabenliste** für beliebige Schlüsselwörter, die gefunden werden.  
  
 **Zugehörige Token hervorheben**  
 Wenn sich der Cursor neben einer geschweiften Klammer befindet, kann der Editor die entsprechende geschweifte Klammer hervorheben, damit Sie den enthaltenen Code leichter sehen können.  
  
## <a name="outlining"></a>Gliedern  
 **Beim Öffnen von Dateien in Gliederungsmodus wechseln**  
 Wenn Sie eine Datei im Text-Editor öffnen, können Sie die Gliederungsfunktion aktivieren. Weitere Informationen finden Sie unter [Gliedern](../../ide/outlining.md). Wenn diese Option ausgewählt ist, wird die Gliederungsfunktion beim Öffnen einer Datei aktiviert.  
  
 **Automatische Gliederung von #pragma-Bereich-Blöcken**  
 Wenn diese Option aktiviert wird, wird die automatische Gliederung für [Pragma-Anweisungen](/cpp/preprocessor/pragma-directives-and-the-pragma-keyword) aktiviert. Damit können Sie Pragmabereichsblocks im gegliederten Modus erweitern oder reduzieren.  
  
 **Automatische Gliederung von Anweisungsblöcken**  
 Wenn diese Option ausgewählt ist, wird die automatische Gliederung für die folgenden Anweisungskonstrukte aktiviert:  
  
-   [if-else](/dotnet/csharp/language-reference/keywords/if-else)  
  
-   [switch-Anweisung (C++)](/cpp/cpp/switch-statement-cpp)  
  
-   [while-Anweisung (C++)](/cpp/cpp/while-statement-cpp)  
  
## <a name="see-also"></a>Siehe auch  
 [Allgemein, Umgebung, Dialogfeld „Optionen“](../../ide/reference/general-environment-options-dialog-box.md)   
 [Verwenden von IntelliSense](../../ide/using-intellisense.md)