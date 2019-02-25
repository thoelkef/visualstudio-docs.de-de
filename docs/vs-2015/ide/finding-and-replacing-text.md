---
title: Suchen und Ersetzen von Text | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
- find, text
- Find in Files dialog box
- find
- text searches, finding and replacing text
- Replace dialog box
- text, finding and replacing
- find, symbol
- find and replace
- replace
- find text
- replacing text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4a0edc40a8a6523c76a6b6f8074a108219152c06
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54756877"
---
# <a name="finding-and-replacing-text"></a>Finding and Replacing Text
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Funktion zum Suchen und Ersetzen von Text lässt sich im Visual Studio Code-Editor und bestimmten textbasierten Ausgabefenstern verwenden, z.B. dem Fenster **Suchergebnisse**. Rufen Sie sie über das Steuerelement **Suchen und Ersetzen** oder über **Suchen/Ersetzen in Dateien** auf. Sie können das Suchen und Ersetzen auch in einigen Designerfenstern, wie dem XAML-Designer, dem Windows Forms-Designer und den Toolfenstern, durchführen.  
  
 Sie können den Suchbereich auf das aktuelle Dokument, die aktuelle Projektmappe oder auf eine benutzerdefinierten Ordnersatz festlegen. Ebenfalls können Sie einen Satz mit Dateinamenerweiterungen für Mehrdateiensuchen angeben. Die Suchsyntax kann mit regulären .NET-Ausdrücken angepasst werden.  
  
 Informationen zum Suchen und Ersetzen von regulären Ausdrücken finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
> [!TIP]
>  Das Feld **Find/Command** (Suchen/Befehl) ist weiterhin als Steuerelement für die Symbolleiste verfügbar, wird standardmäßig aber nicht mehr angezeigt. Sie können das Feld **Find/Command** (Suchen/Befehl) einblenden, indem Sie in der Symbolleiste**Standard** auf **Schaltflächen hinzufügen oder entfernen** klicken und anschließend auf **Suchen** klicken. Weitere Informationen finden Sie unter [Such-/Befehlsfeld](../ide/find-command-box.md).  
  
## <a name="find-and-replace-control"></a>Steuerelement "Suchen und Ersetzen"  
 Das Steuerelement **Suchen und Ersetzen** finden Sie in der rechten oberen Ecke des Code-Editors. Durch das Steuerelement **Suchen und Ersetzen** wird jedes Vorkommen des angegebenen Suchbegriffs im aktuellen Dokument sofort hervorgehoben. Sie können von einem Vorkommen zum nächsten navigieren, indem Sie auf dem Steuerelement „Suche“ auf **Weitersuchen** oder **Vorheriges suchen** auswählen.  
  
 Über die Schaltfläche neben dem Textfeld **Suchen** können Sie auf die Optionen für das Ersetzen zugreifen. Um Ersetzungen einzeln durchzuführen, klicken Sie neben dem Textfeld **Ersetzen** auf **Nächstes ersetzen**. Klicken Sie auf **Alle ersetzen**, um alle Übereinstimmungen auf einmal zu ersetzen.  
  
 Um die Hervorhebungsfarbe für Übereinstimmungen zu ändern, klicken Sie im Menü **Extras** auf **Optionen**, und wählen Sie dann **Umgebung** und **Schriftarten und Farben** aus. Klicken Sie in der Liste **Einstellungen anzeigen für** auf **Text-Editor**, und wählen Sie dann in der Liste **Elemente anzeigen** die Option **Hervorhebung suchen (Erweiterung)** aus.  
  
### <a name="searching-tool-windows"></a>Toolfenster suchen  
 Sie können das Steuerelement **Suchen** in Code oder in Textfenstern verwenden, zum Beispiel in den Fenstern **Ausgabe** und **Suchergebnisse**, indem Sie im Menü **Bearbeiten** die Option **Suchen und Ersetzen** auswählen oder STRG+F drücken.  
  
 Eine Version des Suchen-Steuerelements ist auch in einigen Toolfenstern verfügbar. Sie können jetzt beispielsweise die Liste der Steuerelemente im Fenster **Toolbox** filtern, indem Sie Text in das Suchfeld eingeben. Andere Toolfenster, deren Inhalte Sie jetzt durchsuchen können, sind unter anderem der **Projektmappen-Explorer**, das Fenster **Eigenschaften** und der **Team Explorer**.  
  
## <a name="findreplace-in-files"></a>In Dateien suchen/In Dateien ersetzen  
 **In Dateien suchen/In Dateien ersetzen** funktioniert wie das Steuerelement **Suchen und Ersetzen** mit dem Unterschied, dass Sie einen Bereich für die Suche definieren können. Sie können nicht nur die aktuelle geöffnete Datei im Editor durchsuchen, sondern auch alle geöffneten Dokumente, die gesamte Projektmappe, das aktuelle Projekt und ausgewählte Ordnersätze. Ebenfalls können Sie nach Dateierweiterungen suchen. Um auf das Dialogfeld **In Dateien suchen/ersetzen** zuzugreifen, wählen Sie im Menü **Bearbeiten** die **Option Suchen und Ersetzen** aus, oder drücken Sie STRG+UMSCHALT+F.  
  
 Wenn Sie **Alle suchen** auswählen, erhalten Sie im Fenster **Suchergebnisse** eine Liste der Übereinstimmungen für Ihre Suche. Wenn Sie ein Ergebnis in der Liste auswählen, wird die dazugehörige Datei mit hervorgehobenen Übereinstimmungen angezeigt. Wenn die Datei nicht bereits zur Bearbeitung geöffnet ist, wird sie in einer Vorschauregisterkarte auf der rechten Seite der Registerkartenreihe geöffnet. Sie können das Steuerelement **Suchen** verwenden, um die Liste **Suchergebnisse** zu durchsuchen.  
  
### <a name="creating-custom-search-folder-sets"></a>Erstellen von benutzerdefinierten Suchordnersätzen  
 Sie können einen Suchbereich definieren, indem Sie auf die Schaltfläche **Suchordner auswählen** (sie sieht so aus: **…**) neben dem Feld **Suchen in** klicken. Im Dialogfeld **Suchordner auswählen** können Sie einen Satz mit Ordnern festlegen, der durchsucht werden soll, und Sie können die Spezifikation zur späteren Wiederverwendung speichern. Sie können nur Ordner auf einem Remotecomputer festlegen, wenn Sie dem lokalen Computer das Laufwerk des Remotecomputers zugeordnet haben.  
  
### <a name="creating-custom-component-sets"></a>Erstellen von benutzerdefinierten Komponentensätzen  
 Sie können Komponentensätze als Suchbereich definieren, indem Sie auf die Schaltfläche **Benutzerdefinierten Komponentensatz bearbeiten** neben dem Feld **Suchen in** klicken. Sie können installierte .NET- oder COM-Komponenten, in der Projektmappe enthaltene Visual Studio-Projekte oder eine beliebige Assembly bzw. Typbibliothek (eine DLL-, TLB-, OLB-, EXE- oder OCX-Datei) angeben. Wählen Sie zur Suche nach Verweisen das Feld **In Verweisen suchen** aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
