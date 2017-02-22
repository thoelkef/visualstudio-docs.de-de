---
title: "Schritt 1: Erstellen eines Projekts und Hinzuf&#252;gen einer Tabelle zum Formular | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Schritt 1: Erstellen eines Projekts und Hinzuf&#252;gen einer Tabelle zum Formular
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der erste Schritt beim Erstellen eines Vergleichsspiels besteht darin, das Projekt zu erstellen und dem Formular eine Tabelle hinzuzufügen.  Die Tabelle dient dazu, die Symbole in einem regelmäßigen 4x4\-Raster auszurichten.  Sie legen außerdem einige Eigenschaften fest, um die Darstellung des Spielfelds zu verbessern.  
  
### So erstellen Sie ein Projekt und fügen dem Formular eine Tabelle hinzu  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
2.  Wenn Sie nicht Visual Studio Express verwenden, müssen Sie zuerst eine Programmiersprache auswählen.  Wählen Sie in der Liste **Installierte Vorlagen** entweder **Visual C\#** oder **Visual Basic** aus.  
  
3.  Wählen Sie in der Liste der Projektvorlagen die Vorlage **Windows Forms\-Anwendung** aus, nennen Sie das Projekt "MatchingGame", und wählen Sie dann die Schaltfläche **OK** aus.  
  
4.  Legen Sie im Fenster **Eigenschaften** die folgenden Formulareigenschaften fest.  
  
    1.  Ändern Sie die **Text**\-Eigenschaft des Formulars von **Form1** in **Matching Game**.  Dieser Text wird oben im Spielfenster angezeigt.  
  
    2.  Legen Sie die Größe des Formulars auf eine Breite von 550 Pixeln und eine Höhe von 550 Pixeln fest.  Hierzu können Sie entweder die Eigenschaft **Size** auf **550, 550** festlegen oder die Ecke des Formulars ziehen, bis die richtige Größe in der rechten unteren Ecke der integrierten Entwicklungsumgebung \(IDE\) angezeigt wird.  
  
5.  Zeigen Sie den Werkzeugkasten an, indem Sie die Registerkarte **Werkzeugkasten** auf der linken Seite der IDE auswählen.  
  
6.  Ziehen Sie ein `TableLayoutPanel`\-Steuerelement aus der Kategorie **Container** des Werkzeugkastens, und legen Sie dann die folgenden Eigenschaften dafür fest.  
  
    1.  Legen Sie die **BackColor**\-Eigenschaft auf **CornflowerBlue** fest.  Dazu öffnen Sie das Dialogfeld **BackColor** mit dem Dropdownpfeil neben der Eigenschaft **BackColor** im Fenster **Eigenschaften**.  Anschließend wählen Sie die Registerkarte **Web** im Dialogfeld **BackColor**, um eine Liste verfügbarer Farbnamen anzuzeigen.  
  
        > [!NOTE]
        >  Die Farben sind nicht alphabetisch geordnet, und CornflowerBlue steht fast am Ende der Liste.  
  
    2.  Legen Sie die **Dock**\-Eigenschaft auf **Fill** fest, indem Sie neben der Eigenschaft die Dropdownschaltfläche und dann die große mittlere Schaltfläche wählen.  Dadurch wird die Tabelle so vergrößert, dass sie das gesamte Formular ausfüllt.  
  
    3.  Legen Sie die Eigenschaft **CellBorderStyle** auf **Inset** fest.  Dadurch werden die Zellen auf dem Spielfeld mit Rahmen angezeigt.  
  
    4.  Wählen Sie in der oberen rechten Ecke von TableLayoutPanel die dreieckige Schaltfläche, um das Aufgabenmenü anzuzeigen.  
  
    5.  Wählen Sie im Aufgabenmenü zweimal **Zeile hinzufügen**, um zwei weitere Zeilen hinzuzufügen, und wählen Sie dann zweimal **Spalte hinzufügen**, um zwei weitere Spalten hinzuzufügen.  
  
    6.  Wählen Sie im Aufgabenmenü **Zeilen und Spalten bearbeiten**, um das Fenster **Spalten\- und Zeilenstile** anzuzeigen.  Wählen Sie jede einzelne Spalten aus, wählen Sie die Schaltfläche **Prozent**, und legen Sie dann die Breite jeder Spalte auf 25 Prozent der Gesamtbreite fest.  Wählen Sie anschließend am oberen Fensterrand im Dropdownfeld die Option **Zeilen** aus, und legen Sie die Höhe der einzelnen Zeilen auf 25 Prozent fest.  Wählen Sie anschließend die Schaltfläche **OK**.  
  
     TableLayoutPanel sollte nun ein 4x4\-Raster sein, mit sechzehn quadratischen Zellen gleicher Größe.  In diesen Zeilen und Spalten werden später die Symbolbilder angezeigt.  
  
7.  Stellen Sie sicher, dass TableLayoutPanel im Formular\-Editor ausgewählt ist.  **tableLayoutPanel1** sollte oben im Fenster **Eigenschaften** angezeigt werden.  Wenn das TableLayoutPanel\-Steuerelement nicht ausgewählt ist, wählen Sie es auf dem Formular oder im Dropdownfeld oben in **Eigenschaften** aus.  
  
     Während das TableLayoutPanel\-Steuerelement ausgewählt ist, öffnen Sie den Werkzeugkasten und fügen ein **Bezeichnung**\-Steuerelement \(aus der Kategorie **Allgemeine Steuerelemente** \) in der oberen linken TableLayoutPanel\-Zelle hinzu.  Das `Label`\-Steuerelement sollte jetzt in der IDE ausgewählt sein.  Legen Sie die folgenden Eigenschaften für das Bezeichnungsfeld fest:  
  
    1.  Stellen Sie sicher, dass die **BackColor**\-Eigenschaft des Bezeichnungsfelds auf **CornflowerBlue** festgelegt ist.  
  
    2.  Legen Sie die **AutoSize**\-Eigenschaft auf **False** fest.  
  
    3.  Legen Sie die **Dock**\-Eigenschaft auf **Ausfüllen** fest.  
  
    4.  Legen Sie die **TextAlign**\-Eigenschaft auf **MiddleCenter** fest, indem Sie neben der Eigenschaft erst die Dropdownschaltfläche und dann die mittlere Schaltfläche wählen.  Dadurch wird sichergestellt, dass das Symbol in der Mitte der Zelle angezeigt wird  
  
    5.  Wählen Sie die **Font**\-Eigenschaft.  Eine Schaltfläche mit einem Auslassungszeichen \(…\) wird angezeigt.  
  
    6.  Wählen Sie die Schaltfläche mit dem Auslassungszeichen und legen Sie **Font** auf **Webdings**, **Font Style** auf **Bold** und **Size** auf **72** fest.  
  
    7.  Geben Sie für die Eigenschaft **Text** des Bezeichnungsfelds den Buchstaben **c** ein.  
  
         Die linke obere Zelle im TableLayoutPanel sollte jetzt einen großen schwarzen Kasten enthalten, der mittig in einem blauen Hintergrund zentriert ist.  
  
        > [!NOTE]
        >  Die Schriftart Webdings ist eine Symbolschriftart, die mit dem Betriebssystem Windows geliefert wird.  Im Vergleichsspiel muss der Spieler Symbolpaare finden, und deshalb zeigen Sie die entsprechenden Symbole mithilfe dieser Schriftart an.  Probieren Sie anstelle von **c** für die **Text**\-Eigenschaft andere Buchstaben aus, um herauszufinden, welche Symbole angezeigt werden.  Ein Ausrufezeichen ist eine Spinne, ein großes N ist ein Auge, und ein Komma ist eine Chilischote.  
  
8.  Wählen Sie das Bezeichnungsfeld\-Steuerelement aus und kopieren Sie es in die nächste Zelle im TableLayoutPanel. \(Wählen Sie die Tasten STRG\+C oder **Bearbeiten**, **Kopieren** auf der Menüleiste.\) Fügen Sie das Steuerelement anschließend ein. \(Wählen Sie die Tasten STRG\+V oder **Bearbeiten**, **Einfügen** auf der Menüleiste.\) Eine Kopie des ersten Bezeichnungsfelds wird in der zweiten Zelle im TableLayoutPanel angezeigt.  Fügen Sie das Steuerelement erneut ein. In der dritten Zelle wird eine weitere Bezeichnung angezeigt.  Fahren Sie mit dem Einfügen der `Label`\-Steuerelemente fort, bis alle Zellen ausgefüllt sind.  
  
    > [!NOTE]
    >  Wenn Sie zu viele Einfügungen vornehmen, fügt die IDE dem TableLayoutPanel eine neue Zeile für das neue Bezeichnungsfeld\-Steuerelement hinzu.  Sie können dies rückgängig machen.  Um die neue Zelle zu entfernen, wählen Sie die Tasten STRG\+Z oder **Bearbeiten**, **Rückgängig** auf der Menüleiste.  
  
     Als Nächstes wird das Formular angelegt.  Es sollte aussehen wie die folgende Abbildung.  
  
     ![Anfangszustand des Formulars für das Vergleichsspiel](../ide/media/express_tut4step1.png "Express\_Tut4Step1")  
Anfangszustand des Formulars für das Spiel  
  
### So fahren Sie fort oder überprüfen die Angaben  
  
-   Um zum nächsten Schritt des Lernprogramms zu wechseln, klicken Sie auf [Schritt 2: Hinzufügen eines zufällig ausgewählten Objekts und einer Liste von Symbolen](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).  
  
-   Um zum Thema mit der Übersicht zurückzukehren, klicken Sie auf [Lernprogramm 3: Erstellen eines Vergleichsspiels](../ide/tutorial-3-create-a-matching-game.md).