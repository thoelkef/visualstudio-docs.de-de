---
title: "Optionen, Text-Editor, Alle Sprachen | Microsoft Docs"
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
  - "VS.ToolsOptionsPages.Text_Editor.JavaScript.General"
  - "VS.ToolsOptionsPages.Text_Editor.ResJSON.General"
  - "vs.toolsoptionspages.text_editor.all_languages.scrollbars"
helpviewer_keywords: 
  - "Text-Editor-Optionen (Dialogfeld)"
  - "Anweisungsvervollständigung"
  - "Zeilenumbruch"
  - "Allgemein (Dialogfeld)"
  - "Zeilennummern"
  - "Virtueller Bereich"
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Optionen, Text-Editor, Alle Sprachen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In diesem Dialogfeld können Sie das Standardverhalten des Code\-Editors ändern.  Diese Einstellungen betreffen auch andere Editoren, die auf dem Code\-Editor basieren, z. B. die Quellansicht des HTML\-Designers.  Wählen Sie im Menü **Extras** die Option **Optionen**, um dieses Dialogfeld zu öffnen.  Erweitern Sie im Ordner **Text\-Editor** den Unterordner **Alle Sprachen**, und wählen Sie dann **Allgemein** aus.  
  
> [!CAUTION]
>  Auf dieser Seite werden Standardoptionen für alle Entwicklungssprachen festgelegt.  Beachten Sie, dass durch das Zurücksetzen einer Option in diesem Dialogfeld die Optionen unter Allgemein unabhängig von den dort aktivierten Optionen für alle Programmiersprachen zurückgesetzt werden.  Um Text\-Editor\-Optionen für nur eine Sprache zu ändern, erweitern Sie den Unterordner für diese Sprache und wählen die zugehörigen Optionsseiten aus.  
  
 Wenn eine Option auf den Optionsseiten Allgemein für einige Programmiersprachen ausgewählt wurde, für andere jedoch nicht, wird ein graues Häkchen angezeigt.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Anweisungsvervollständigung  
 Member automatisch auflisten  
 Bei Auswahl dieser Option werden von IntelliSense Popuplisten der verfügbaren Member, Eigenschaften, Werte oder Methoden angezeigt, sobald Sie im Editor mit der Eingabe beginnen.  Wählen Sie aus der Popupliste ein beliebiges Element aus, das in den Code eingefügt werden soll.  Durch Auswahl dieser Option wird die Option **Erweiterte Member ausblenden** aktiviert.  
  
 Erweiterte Member ausblenden  
 Bei Auswahl dieser Option werden die Popuplisten zur Anweisungsvervollständigung verkürzt, indem nur die am häufigsten verwendeten Elemente angezeigt werden.  Andere Elemente werden aus der Liste herausgefiltert.  
  
 Parameterinformationen  
 Bei Auswahl dieser Option wird die vollständige Syntax für die aktuelle Deklaration oder Prozedur neben der Einfügemarke des Editors mit allen verfügbaren Parametern angezeigt.  Der nächste Parameter, den Sie zuweisen können, ist fett formatiert.  
  
## Einstellungen  
 Virtuellen Bereich aktivieren  
 Wenn diese Option ausgewählt und **Zeilenumbruch** deaktiviert wurde, können Sie im Code\-Editor auf eine beliebige Stelle nach einem Zeilenende klicken und Zeichen eingeben.  Dieses Feature kann verwendet werden, um Kommentare immer an derselben Stelle neben dem Code einzufügen.  
  
 Zeilenumbruch  
 Bei Auswahl dieser Option wird der Teil einer Zeile, der horizontal über den sichtbaren Bereich des Editors hinausgeht, automatisch in der nächsten Zeile angezeigt.  Wenn Sie diese Option auswählen, wird die Option **Visuelle Symbole für Zeilenumbruch anzeigen** aktiviert.  
  
> [!NOTE]
>  Das Feature **Virtueller Bereich** ist deaktiviert, während **Zeilenumbruch** aktiviert ist.  
  
 Visuelle Symbole für Zeilenumbruch anzeigen  
 Wenn ausgewählt, wird beim Umbruch einer langen Zeile in eine zweite Zeile ein Indikator in Form eines Rückwärtspfeils angezeigt.  
  
 Deaktivieren Sie diese Option, wenn Sie diese Indikatoren nicht anzeigen möchten.  
  
> [!NOTE]
>  Diese zur Erinnerung dienenden Pfeile werden weder gedruckt noch dem Code hinzugefügt.  Sie sind lediglich als Referenz gedacht.  
  
 Befehle zum Ausschneiden oder Kopieren bei fehlender Auswahl auf leere Zeilen anwenden  
 Diese Option legt das Verhalten des Editors fest, wenn Sie die Einfügemarke in einer leeren Zeile positionieren, keine Auswahl vornehmen und anschließend den Vorgang Kopieren oder Ausschneiden ausführen.  
  
-   Wenn diese Option aktiviert ist, wird die Leerzeile kopiert bzw. ausgeschnitten.  Beim anschließenden Einfügen wird eine neue Leerzeile eingefügt.  
  
-   Wenn diese Option deaktiviert ist, entfernt der Befehl Ausschneiden Leerzeilen.  Die Daten in der Zwischenablage werden jedoch beibehalten.  Wenn Sie anschließend den Befehl Einfügen verwenden, wird der zuletzt in die Zwischenablage kopierte Inhalt eingefügt.  Wenn vorher nichts kopiert wurde, wird nichts eingefügt.  
  
 Wenn eine Zeile nicht leer ist, hat diese Einstellung keine Auswirkungen auf die Befehle Kopieren oder Ausschneiden.  Wenn nichts ausgewählt wurde, wird die gesamte Zeile kopiert oder ausgeschnitten.  Beim anschließenden Einfügen werden der Text der gesamten Zeile sowie das Zeilenendezeichen eingefügt.  
  
> [!TIP]
>  Zur Unterscheidung von Zeilen mit Einzug und Leerzeilen können Indikatoren für Leerzeichen, Tabulatoren und Zeilenenden angezeigt werden. Wählen Sie dazu im Menü **Bearbeiten** die Option **Erweitert** und anschließend **Leerraum anzeigen** aus.  
  
## Anzeige  
 Zeilennummern  
 Bei Auswahl dieser Option wird neben jeder Codezeile eine Zeilennummer angezeigt.  
  
> [!NOTE]
>  Diese Zeilennummern werden weder gedruckt noch dem Code hinzugefügt.  Sie sind lediglich als Referenz gedacht.  
  
 Einfaches Klicken für URLs aktivieren  
 Bei Auswahl dieser Option nimmt der Mauscursor die Form einer Hand an, wenn er im Editor über eine URL bewegt wird.  Sie können auf die URL klicken, um die angegebene Seite im Webbrowser anzuzeigen.  
  
 Navigationsleiste  
 Bei Auswahl dieser Option wird am oberen Rand des Code\-Editors die **Navigationsleiste** angezeigt.  Über die Dropdownlisten **Objekte** und **Member** können Sie ein bestimmtes Objekt im Code auswählen, aus seinen Membern auswählen und zur Deklaration des ausgewählten Members im Code\-Editor navigieren.  
  
## Siehe auch  
 [Optionen, Text\-Editor, Alle Sprachen, Registerkarten](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [Allgemein, Umgebung, Dialogfeld "Optionen"](../../ide/reference/general-environment-options-dialog-box.md)   
 [Verwenden von IntelliSense](../../ide/using-intellisense.md)