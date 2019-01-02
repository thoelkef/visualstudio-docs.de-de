---
title: Optionen, Text-Editor, Alle Sprachen
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8fa208805a8d6861082793551dbbc595985fdc55
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52387987"
---
# <a name="options-text-editor-all-languages"></a>Optionen, Text-Editor, Alle Sprachen

Mit diesem Dialogfeld können Sie das Standardverhalten des Code-Editors ändern. Diese Einstellungen gelten auch für andere Editoren, die auf dem Code-Editor basieren, z.B. die Quellansicht des HTML-Designers. Um das Dialogfeld zu öffnen, klicken Sie auf **Optionen** im Menü **Tools**. Erweitern Sie innerhalb des Ordners **Text-Editor** den Unterordner **Alle Sprachen**, und klicken Sie dann auf **Allgemein**.

> [!CAUTION]
> Auf dieser Seite werden die Standardoptionen für alle Entwicklungssprachen festgelegt. Denken Sie daran, dass beim Zurücksetzen einer Option in diesem Dialogfeld die allgemeinen Optionen in allen Sprachen auf die hier ausgewählten Optionen zurückgesetzt werden. Um die Optionen des Text-Editors für nur eine Sprache zu ändern, erweitern Sie den Unterordner für diese Sprache, und wählen Sie seine Optionsseiten aus.

Wenn eine Option auf der Seite der allgemeinen Optionen für manche, aber nicht alle, Programmiersprachen aktiviert wurde, wird ein ausgegrautes Häkchen angezeigt.

## <a name="statement-completion"></a>Anweisungsvervollständigung

**Member automatisch auflisten**

Wenn aktiviert, werden Popuplisten verfügbarer Member, Eigenschaften, Werte oder Methoden von IntelliSense angezeigt, während Sie eine Eingabe machen. Wählen Sie aus der Popupliste ein Element aus, das in den Code eingefügt werden soll. Wenn Sie diese Option auswählen, wird die Option **Erweiterte Member ausblenden** aktiviert

**Erweiterte Member ausblenden**

Wenn aktiviert, werden die Popuplisten zur Anweisungsvervollständigung verkürzt, da nur die am häufigsten verwendeten Elemente angezeigt werden. Andere Elemente werden aus der Liste herausgefiltert.

**Parameterinformationen**

Wenn diese Option aktiviert ist, wird die vollständige Syntax der aktuellen Deklaration oder Prozedur mit allen verfügbaren Parametern unter der Einfügemarke im Editor angezeigt. Der nächste Parameter, den Sie zuweisen können, ist fett formatiert.

## <a name="settings"></a>Einstellungen

**Virtuellen Bereich aktivieren**

Wenn dieses Option aktiviert ist und **Zeilenumbruch** deaktiviert wurde, können Sie mit der Maus im Code-Editor auf eine beliebige Stelle nach einem Zeilenende klicken und mit der Eingabe beginnen. Diese Funktion kann verwendet werden, um Kommentare immer an derselben Stelle neben dem Code einzufügen.

**Zeilenumbruch**

Wenn aktiviert, wird der Teil einer Zeile, der über den horizontal sichtbaren Bereich des Editors hinausgeht, automatisch in der nächsten Zeile angezeigt. Wenn Sie diese Option auswählen, wird die Option **Visuelle Symbole für Zeilenumbruch** anzeigen aktiviert.

> [!NOTE]
> Die Funktion **Virtueller Bereich** ist deaktiviert, wenn **Zeilenumbruch** aktiviert ist.

**Visuelle Glyphen für Zeilenumbruch anzeigen**

Wenn aktiviert, wird beim Umbruch einer langen Zeile auf eine zweite Zeile ein Indikator in Form eines Rückwärtspfeils angezeigt.

![LineBreakSymbol-Bildschirmabbildung](../../ide/reference/media/linebreak.gif)

Deaktivieren Sie diese Option, wenn Sie diese Indikatoren nicht anzeigen möchten.

> [!NOTE]
> Diese zur Erinnerung dienenden Pfeile werden weder gedruckt noch dem Code hinzugefügt. Sie sind lediglich als Referenz gedacht.

**Zeilennummern**

Wenn aktiviert, wird eine Zeilennummer neben jeder Codezeile angezeigt.

> [!NOTE]
> Diese Zeilennummern werden weder gedruckt noch dem Code hinzugefügt. Sie sind lediglich als Referenz gedacht.

**Einfaches Klicken für URLs aktivieren**

Wenn aktiviert, nimmt der Cursor die Form einer Hand an, wenn er im Editor über eine URL bewegt wird. Sie können auf die URL klicken, um die angegebene Seite im Webbrowser anzuzeigen.

**Navigationsleiste**

Wenn aktiviert, wird die **Navigationsleiste** am oberen Rand des Code-Editors angezeigt. Mit den Dropdownlisten **Objekte** und **Member** können Sie ein bestimmtes Objekt in Ihrem Code auswählen, seine Member auswählen und zur Deklaration des ausgewählten Members im Code-Editor navigieren.

**Befehle zum Ausschneiden oder Kopieren bei fehlender Auswahl auf leere Zeilen anwenden**

Diese Option legt das Verhalten des Editors fest, wenn Sie die Einfügemarke in einer leeren Zeile positionieren, keine Auswahl vornehmen und anschließend einen Kopier- oder Ausschneidevorgang ausführen.

-   Wenn diese Option aktiviert ist, wird die Leerzeile kopiert oder ausgeschnitten. Beim anschließenden Einfügen wird eine neue leere Zeile eingefügt.

-   Wenn diese Option deaktiviert ist, entfernt das Ausschneiden leere Zeilen. Die Daten in der Zwischenablage werden allerdings beibehalten. Wenn Sie deshalb anschließend den Befehl „Einfügen“ verwenden, wird der zuletzt in die Zwischenablage kopierte Inhalt eingefügt. Wenn vorher nichts kopiert wurde, wird nichts eingefügt.

Wenn eine Zeile nicht leer ist, hat diese Einstellung keine Auswirkungen auf den Kopier- oder Ausschneidevorgang. Wenn nichts ausgewählt wurde, wird die gesamte Zeile kopiert oder ausgeschnitten. Beim anschließenden Einfügen werden der Text der gesamten Zeile sowie das Zeilenendezeichen eingefügt.

> [!TIP]
> Zur Unterscheidung von Zeilen mit Einzug und Leerzeilen können Indikatoren für Leerzeichen, Tabulatoren und Zeilenenden angezeigt werden. Wählen Sie dazu im Menü **Bearbeiten** die Option **Erweitert** und anschließend **Leerstelle anzeigen** aus.

## <a name="see-also"></a>Siehe auch

- [Optionen, Text-Editor, Alle Sprachen, Registerkarten](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md)
- [Verwenden von IntelliSense](../../ide/using-intellisense.md)