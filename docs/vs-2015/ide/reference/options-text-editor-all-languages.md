---
title: Optionen, Text-Editor, Alle Sprachen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- vs.toolsoptionspages.text_editor.all_languages.scrollbars
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ebe2da1dec9917a792f3e4e02516a79cff605c80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662404"
---
# <a name="options-text-editor-all-languages"></a>Optionen, Text-Editor, Alle Sprachen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mit diesem Dialogfeld können Sie das Standardverhalten des Code-Editors ändern. Diese Einstellungen gelten auch für andere Editoren, die auf dem Code-Editor basieren, z.B. die Quellansicht des HTML-Designers. Um das Dialogfeld zu öffnen, klicken Sie auf **Optionen** im Menü **Tools**. Erweitern Sie innerhalb des Ordners **Text-Editor** den Unterordner **Alle Sprachen**, und klicken Sie dann auf **Allgemein**.

> [!CAUTION]
> Auf dieser Seite werden die Standardoptionen für alle Entwicklungssprachen festgelegt. Denken Sie daran, dass beim Zurücksetzen einer Option in diesem Dialogfeld die allgemeinen Optionen in allen Sprachen auf die hier ausgewählten Optionen zurückgesetzt werden. Um die Optionen des Text-Editors für nur eine Sprache zu ändern, erweitern Sie den Unterordner für diese Sprache, und wählen Sie seine Optionsseiten aus.

 Wenn eine Option auf der Seite der allgemeinen Optionen für manche, aber nicht alle, Programmiersprachen aktiviert wurde, wird ein ausgegrautes Häkchen angezeigt.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="statement-completion"></a>Anweisungsabschluss
 Automatisches Auflisten von Membern, wenn Sie ausgewählt sind, werden Popup Listen mit verfügbaren Membern, Eigenschaften, Werten oder Methoden von IntelliSense angezeigt, wenn Sie im Editor eingeben. Wählen Sie ein Element aus der Popupliste aus, um es in Ihren Code einzufügen. Wenn Sie diese Option auswählen, wird die Option **Erweiterte Member ausblenden** aktiviert

 Erweiterte Member ausblenden wenn diese Option ausgewählt ist, werden Popup Anweisungs Vervollständigungs Listen verkürzt, indem nur die am häufigsten verwendeten Elemente angezeigt werden. Die anderen Elemente werden aus der Liste gefiltert.

 Parameter Informationen wenn Sie diese Option auswählen, wird die vollständige Syntax für die aktuelle Deklaration bzw. Prozedur unter der Einfügemarke im Editor mit allen verfügbaren Parametern angezeigt. Der nächste Parameter, den Sie zuweisen können, ist fett formatiert.

## <a name="settings"></a>Einstellungen
 Virtuellen Bereich aktivieren Wenn diese Option ausgewählt ist und Zeilenumbruch deaktiviert ist, können Sie im Code-Editor auf eine beliebige Stelle außerhalb des Zeilen Endes **klicken und eingeben** . Diese Funktion kann verwendet werden, um Kommentare immer an derselben Stelle neben dem Code einzufügen.

 Zeilenumbruch wenn diese Option ausgewählt ist, wird jeder Teil einer Zeile, der über den sichtbaren Editor Bereich hinaus horizontal erweitert wird, automatisch in der nächsten Zeile angezeigt. Wenn Sie diese Option auswählen, wird die Option **Visuelle Symbole für Zeilenumbruch** anzeigen aktiviert.

> [!NOTE]
> Die Funktion **Virtueller Bereich** ist deaktiviert, wenn **Zeilenumbruch** aktiviert ist.

 Visuelle Symbole für Zeilenumbruch anzeigen, wenn diese Option ausgewählt ist, wird ein Rückgabe Pfeil Indikator angezeigt, bei dem eine lange Zeile auf eine zweite Zeile umbrochen wird.

 ![LineBreakSymbol-Bildschirmabbildung](../../ide/reference/media/linebreak.gif "linebreak")

 Deaktivieren Sie diese Option, wenn Sie diese Indikatoren nicht anzeigen möchten.

> [!NOTE]
> Diese zur Erinnerung dienenden Pfeile werden weder gedruckt noch dem Code hinzugefügt. Sie dienen lediglich als Hinweis.

 Befehle zum Ausschneiden oder Kopieren auf leere Zeilen anwenden, wenn keine Auswahl vorhanden ist, wird mit dieser Option das Verhalten des Editors festgelegt, wenn Sie die Einfügemarke in einer leeren Zeile platzieren, nichts auswählen und dann kopieren oder Ausschneiden.

- Wenn diese Option aktiviert ist, wird die Leerzeile kopiert oder ausgeschnitten. Beim anschließenden Einfügen wird eine neue leere Zeile eingefügt.

- Wenn diese Option deaktiviert ist, entfernt das Ausschneiden leere Zeilen. Die Daten in der Zwischenablage werden allerdings beibehalten. Wenn Sie deshalb anschließend den Befehl „Einfügen“ verwenden, wird der zuletzt in die Zwischenablage kopierte Inhalt eingefügt. Wenn Sie zuvor nichts kopiert haben, wird kein Inhalt eingefügt.

  Wenn eine Zeile nicht leer ist, hat diese Einstellung keine Auswirkungen auf den Kopier- oder Ausschneidevorgang. Wenn nichts ausgewählt ist, wird die gesamte Zeile kopiert oder ausgeschnitten. Beim anschließenden Einfügen werden der Text der gesamten Zeile sowie das Zeilenendezeichen eingefügt.

> [!TIP]
> Zur Unterscheidung von Zeilen mit Einzug und Leerzeilen können Indikatoren für Leerzeichen, Tabulatoren und Zeilenenden angezeigt werden. Wählen Sie dazu im Menü **Bearbeiten** die Option **Erweitert** und anschließend **Leerstelle anzeigen** aus.

## <a name="display"></a>Anzeige
 Zeilennummern wenn diese Option ausgewählt ist, wird neben jeder Codezeile eine Zeilennummer angezeigt.

> [!NOTE]
> Diese Zeilennummern werden weder gedruckt noch dem Code hinzugefügt. Sie dienen lediglich als Hinweis.

 Single-Click-URL-Navigation aktivieren, wenn diese Option aktiviert ist, ändert sich der Mauszeiger in eine zeilige Hand, wenn er im Editor über eine URL bewegt wird. Sie können auf die URL klicken, um die angegebene Seite im Webbrowser anzuzeigen.

 Navigationsleiste zeigt die **Navigationsleiste** am oberen Rand des Code-Editors an, wenn Sie ausgewählt ist. Mit den Dropdownlisten **Objekte** und **Member** können Sie ein bestimmtes Objekt in Ihrem Code auswählen, seine Member auswählen und zur Deklaration des ausgewählten Members im Code-Editor navigieren.

## <a name="see-also"></a>Weitere Informationen
 [Optionen, Text-Editor, alle Sprachen, Registerkarten](../../ide/reference/options-text-editor-all-languages-tabs.md) [Allgemein, Umgebung, Dialog Feld "Optionen](../../ide/reference/general-environment-options-dialog-box.md) " unter [Verwendung von IntelliSense](../../ide/using-intellisense.md)
