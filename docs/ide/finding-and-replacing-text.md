---
title: Suchen und Ersetzen von Text
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- Find in Files dialog box
- text searches, finding and replacing text
- text, finding and replacing
- find and replace
- find text
- replace text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7051b90dde45965b76e8a9e08b33b5326ff2848c
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106751"
---
# <a name="find-and-replace-text"></a>Suchen und Ersetzen von Text

Sie können Text im Visual Studio-Editor mit [Suchen und Ersetzen](#find-and-replace-control) oder mit [In Dateien suchen/In Dateien ersetzen](#find-in-files-and-replace-in-files) suchen und ersetzen.

> [!TIP]
> Wenn Sie Codesymbole wie Variablen und Methoden umbenennen, ist es besser, anstelle von Suchen und Ersetzen eine *[Umgestaltung](../ide/reference/rename.md)* zu verwenden. Die Umgestaltung ist eine intelligente Funktion, die den Projektumfang berücksichtigt, während Suchen und Ersetzen alle Instanzen blind ersetzt.

Die Funktion Suchen und Ersetzen steht im Editor, in bestimmten anderen textbasierten Fenstern wie z.B. in **Suchergebnis**-Fenstern, in Designerfenstern wie z.B. XAML-Designer und Windows Forms-Designer und in Toolfenstern zur Verfügung.

Sie können den Suchbereich auf das aktuelle Dokument, die aktuelle Projektmappe oder auf eine benutzerdefinierten Ordnersatz festlegen. Ebenfalls können Sie einen Satz mit Dateinamenerweiterungen für Mehrdateiensuchen angeben. Die Suchsyntax kann mit [regulären .NET-Ausdrücken](../ide/using-regular-expressions-in-visual-studio.md) angepasst werden.

> [!TIP]
> Das Feld [Find/Command](../ide/find-command-box.md) (Suchen/Befehl) ist weiterhin als Symbolleisten-Steuerelement verfügbar, wird standardmäßig aber nicht angezeigt. Sie können das Feld **Find/Command** (Suchen/Befehl) einblenden, indem Sie in der **Standard**-Symbolleiste zunächst **Schaltflächen hinzufügen oder entfernen** auswählen und anschließend **Suchen** auswählen.

## <a name="find-and-replace-control"></a>Steuerelement "Suchen und Ersetzen"

Das Steuerelement **Suchen und Ersetzen** finden Sie in der rechten oberen Ecke des Code-Editors. Durch das Steuerelement **Suchen und Ersetzen** wird jedes Vorkommen des angegebenen Suchbegriffs im aktuellen Dokument sofort hervorgehoben. Sie können von einem Vorkommen zum nächsten navigieren, indem Sie auf dem Steuerelement „Suche“ auf **Weitersuchen** oder **Vorheriges suchen** auswählen.

![Steuerelement "Suchen und Ersetzen"](media/find-and-replace-box.png)

Über die Schaltfläche neben dem Textfeld **Suchen** können Sie auf die Optionen für das Ersetzen zugreifen. Um Ersetzungen einzeln durchzuführen, klicken Sie neben dem Textfeld **Ersetzen** auf **Nächstes ersetzen**. Klicken Sie auf **Alle ersetzen**, um alle Übereinstimmungen auf einmal zu ersetzen.

Um die Hervorhebungsfarbe für Übereinstimmungen zu ändern, klicken Sie im Menü **Extras** auf **Optionen**, und wählen Sie dann **Umgebung** und **Schriftarten und Farben** aus. Klicken Sie in der Liste **Einstellungen anzeigen für** auf **Text-Editor**, und wählen Sie dann in der Liste **Elemente anzeigen** die Option **Hervorhebung suchen (Erweiterung)** aus.

### <a name="search-tool-windows"></a>Suchen in Toolfenstern

Sie können das Steuerelement **Suchen** in Code- oder Textfenstern wie beispielsweise den Fenstern **Ausgabe** und **Suchergebnisse** verwenden, indem Sie **Bearbeiten** > **Suchen und Ersetzen** auswählen oder **STRG+F** drücken.

Eine Version des Steuerelements **Suchen** ist auch in einigen Toolfenstern verfügbar. Sie können beispielsweise die Liste der Steuerelemente im Fenster **Toolbox** filtern, indem Sie Text in das Suchfeld eingeben. Andere Toolfenster, deren Inhalte Sie durchsuchen können, sind unter anderem der **Projektmappen-Explorer**, das Fenster **Eigenschaften** und der **Team Explorer**.

## <a name="find-in-files-and-replace-in-files"></a>In Dateien suchen und In Dateien ersetzen

**In Dateien suchen/In Dateien ersetzen** funktioniert wie das Steuerelement **Suchen und Ersetzen** mit dem Unterschied, dass Sie einen Bereich für die Suche definieren können. Sie können nicht nur die aktuell geöffnete Datei im Editor durchsuchen, sondern auch alle geöffneten Dokumente, die gesamte Projektmappe, das aktuelle Projekt und ausgewählte Ordnersätze. Ebenfalls können Sie nach Dateierweiterungen suchen. Um auf das Dialogfeld **In Dateien suchen/In Dateien ersetzen** zuzugreifen, wählen Sie im Menü **Bearbeiten** die Option **Suchen und Ersetzen** aus, oder drücken Sie **Strg+Umschalt+F**.

![In Dateien suchen (Dialogfeld)](media/find-in-files-box.png)

### <a name="find-results"></a>Suchergebnisse

Wenn Sie **Alle suchen** auswählen, erhalten Sie im Fenster **Suchergebnisse** eine Liste der Übereinstimmungen für Ihre Suche. Wenn Sie ein Ergebnis in der Liste auswählen, wird die dazugehörige Datei mit hervorgehobenen Übereinstimmungen angezeigt. Wenn die Datei nicht bereits zur Bearbeitung geöffnet ist, wird sie in einer Vorschauregisterkarte auf der rechten Seite der Registerkartenreihe geöffnet. Sie können das Steuerelement **Suchen** verwenden, um die Liste **Suchergebnisse** zu durchsuchen.

### <a name="create-custom-search-folder-sets"></a>Erstellen benutzerdefinierter Suchordnersätze

Sie können einen Suchbereich definieren, indem Sie die Schaltfläche **Suchordner auswählen** (sie sieht so aus: **…**) neben dem Feld **Suchen in** auswählen. Im Dialogfeld **Suchordner auswählen** können Sie einen zu durchsuchenden Ordnersatz angeben, und Sie können die Spezifikation zur späteren Wiederverwendung speichern.

> [!TIP]
> Wenn Sie Ihrem lokalen Computer ein Remotecomputer-Laufwerk zugeordnet haben, können Sie Ordner für die Suche auf dem Remotecomputer angeben.

### <a name="create-custom-component-sets"></a>Erstellen benutzerdefinierter Komponentensätze

Sie können Komponentensätze als Suchbereich definieren, indem Sie auf die Schaltfläche **Benutzerdefinierten Komponentensatz bearbeiten** neben dem Feld **Suchen in** klicken. Sie können installierte .NET- oder COM-Komponenten, in der Projektmappe enthaltene Visual Studio-Projekte oder eine beliebige Assembly bzw. Typbibliothek (*DLL*, *TLB*, *OLB*, *EXE* oder *OCX*) angeben. Wählen Sie zur Suche nach Verweisen das Feld **In Verweisen suchen** aus.

## <a name="see-also"></a>Siehe auch

- [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Refactoring von Code in Visual Studio](../ide/refactoring-in-visual-studio.md)