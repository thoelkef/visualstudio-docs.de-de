---
title: "Suchen und Ersetzen von Text | Microsoft Docs"
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
  - "vs.find"
  - "vs.findreplacecontrol"
  - "vs.findreplace.findsymbol"
  - "vs.findreplace.symbol"
  - "findresultswindow"
  - "vs.findreplace.quickreplace"
  - "vs.findsymbol"
  - "vs.findinfiles"
  - "vs.findresults1"
  - "vs,findsymbolwindow"
  - "vs.findreplace.quickfind"
  - "vs.lookin"
  - "vs.replace"
helpviewer_keywords: 
  - "find"
  - "Suchen und Ersetzen"
  - "In Dateien suchen (Dialogfeld)"
  - "Text suchen"
  - "find, Symbol"
  - "find, text"
  - "replace"
  - "Ersetzen (Dialogfeld)"
  - "In Dateien ersetzen (Dialogfeld)"
  - "Ersetzen von Text"
  - "Textsuche"
  - "Textsuche, Suchen und Ersetzen von Text"
  - "text, Suchen und Ersetzen"
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
caps.latest.revision: 31
caps.handback.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Suchen und Ersetzen von Text
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können das Suchen und Ersetzen von Text im Code\-Editor von Visual Studio und in bestimmten textbasierten Ausgabefenstern, wie das Fenster **Suchergebnisse**, mithilfe des Steuerelements **Suchen und Ersetzen** oder **In Dateien suchen\/In Dateien ersetzen** durchführen.  Sie können das Suchen und Ersetzen auch in einigen Designerfenstern, wie dem XAML\-Designer, dem Windows Forms\-Designer und den Toolfenstern, durchführen.  
  
 Sie können den Suchbereich auf das aktuelle Dokument, die aktuelle Projektmappe oder auf eine benutzerdefinierten Ordnersatz festlegen.  Ebenfalls können Sie einen Satz mit Dateinamenerweiterungen für Mehrdateiensuchen angeben.  Die Suchsyntax kann mit regulären .NET\-Ausdrücken angepasst werden.  
  
 Weitere Informationen zum Suchen und Ersetzen regulärer Ausdrücke finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
> [!TIP]
>  Das Feld **Suchen\/Befehl** ist als Symbolleisten\-Steuerelement weiterhin verfügbar, jedoch nicht mehr standardmäßig sichtbar.  Sie können das Feld **Suchen\/Befehl** anzeigen, indem Sie auf der Symbolleiste **Standard** die Option **Schaltflächen hinzufügen oder entfernen** und dann **Suchen** auswählen.  Weitere Informationen finden Sie unter [Such\/Befehlsfeld](../ide/find-command-box.md).  
  
## Steuerelement "Suchen und Ersetzen"  
 Das Steuerelement **Suchen und Ersetzen** wird in der rechten oberen Ecke des Fensters "Code\-Editor" angezeigt.  Durch das Steuerelement **Suchen und Ersetzen** wird jedes Vorkommen der angegebenen Suchzeichenfolge im aktuellen Dokument sofort hervorgehoben.  Sie können von einem Vorkommen zum nächsten navigieren, indem Sie auf dem Suchsteuerelement die Schaltfläche **Weitersuchen** oder **Vorheriges suchen** auswählen.  
  
 Über die Schaltfläche neben dem Textfeld **Suchen** können Sie auf Ersatzoptionen zugreifen.  Um Ersetzungen einzeln durchzuführen, klicken Sie neben dem Textfeld **Ersetzen** auf die Schaltfläche **Nächstes ersetzen**.  Wählen Sie die Schaltfläche **Alle ersetzen** aus, um alle Übereinstimmungen auf einmal zu ersetzen.  
  
 Um die Hervorhebungsfarbe für Übereinstimmungen zu ändern, klicken Sie im Menü **Extras** auf **Optionen**, und wählen Sie dann **Umgebung** und **Schriftarten und Farben** aus.  Klicken Sie in der Liste **Einstellungen anzeigen für** auf **Text\-Editor**, und wählen Sie dann in der Liste **Elemente anzeigen** die Option **Hervorhebung suchen \(Erweiterung\)** aus.  
  
### Toolfenster suchen  
 Sie können das Steuerelement **Suchen** in Code oder in Textfenstern verwenden, zum Beispiel in den Fenstern **Ausgabe** und **Suchergebnisse**, indem Sie im Menü **Bearbeiten** die Option **Suchen und Ersetzen** auswählen oder STRG\+F drücken.  
  
 Eine Version des Suchen\-Steuerelements ist auch in einigen Toolfenstern verfügbar.  Sie können jetzt beispielsweise die Liste der Steuerelemente im Fenster **Werkzeugkasten** filtern, indem Sie Text in das Suchfeld eingeben.  Andere Toolfenster, deren Inhalte Sie jetzt durchsuchen können, sind unter anderem der **Projektmappen\-Explorer**, das Fenster **Eigenschaften** und der **Team Explorer**.  
  
## In Dateien suchen\/In Dateien ersetzen  
 **In Dateien suchen\/In Dateien ersetzen** funktioniert wie das Steuerelement **Suchen und Ersetzen** mit dem Unterschied, dass Sie einen Bereich für die Suche definieren können.  Sie können nicht nur die aktuelle geöffnete Datei im Editor durchsuchen, sondern auch alle geöffneten Dokumente, die gesamte Projektmappe, das aktuelle Projekt und ausgewählte Ordnersätze.  Ebenfalls können Sie nach Dateinamenerweiterungen suchen.  Um auf das Dialogfeld **In Dateien suchen\/ersetzen** zuzugreifen, wählen Sie im Menü **Bearbeiten** die Option **Suchen und Ersetzen** aus, oder drücken Sie STRG\+UMSCHALT\+F.  
  
 Wenn Sie **Alle suchen** auswählen, erhalten Sie im Fenster **Suchergebnisse** eine Liste der Übereinstimmungen für Ihre Suche.  Wenn Sie ein Ergebnis in der Liste auswählen, wird die dazugehörige Datei mit hervorgehobenen Übereinstimmungen angezeigt.  Wenn die Datei nicht bereits zur Bearbeitung geöffnet ist, wird sie in einer Vorschauregisterkarte auf der rechten Seite der Registerkartenreihe geöffnet.  Sie können das **Suchen**\-Steuerelement verwenden, um die Liste **Suchergebnisse** zu durchsuchen.  
  
### Erstellen von benutzerdefinierten Suchordnersätzen  
 Sie können einen Suchbereich definieren, indem Sie die Schaltfläche **Suchordner auswählen** \(sie sieht so aus: **…**\) neben dem Feld **Suchen in** auswählen.  Im Dialogfeld **Suchordner auswählen** können Sie einen Satz mit Ordnern festlegen, der durchsucht werden soll, und Sie können die Spezifikation zur späteren Wiederverwendung speichern.  Sie können nur Ordner auf einem Remotecomputer festlegen, wenn Sie dem lokalen Computer das Laufwerk des Remotecomputers zugeordnet haben.  
  
### Erstellen von benutzerdefinierten Komponentensätzen  
 Sie können Komponentensätze als Suchbereich definieren, indem Sie auf die Schaltfläche **Benutzerdefinierten Komponentensatz bearbeiten** neben dem Feld **Suchen in** klicken.  Sie können installierte .NET\- oder COM\-Komponenten, in der Projektmappe enthaltene Visual Studio\-Projekte oder eine beliebige Assembly bzw. Typbibliothek \(eine DLL\-, TLB\-, OLB\-, EXE\- oder OCX\-Datei\) angeben.  Wählen Sie zur Suche nach Verweisen das Feld **In Verweisen suchen** aus.  
  
## Siehe auch  
 [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)