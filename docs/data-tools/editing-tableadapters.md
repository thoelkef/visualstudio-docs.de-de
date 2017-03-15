---
title: "TableAdapter-Abfragekonfigurations-Assistent | Microsoft Docs"
ms.custom: ""
ms.date: "09/22/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.dbtablefunctionwizard"
  - "vs.datasource.datacomponentquerywizard"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Daten [Visual Studio], Datenkomponenten-Abfragen"
  - "Daten [Visual Studio], TableAdapter-Abfragen"
  - "Daten [Visual Studio], TableAdapters"
  - "TableAdapter-Abfragekonfigurations-Assistent"
ms.assetid: 8c06b306-24d0-4521-948d-07e3b7badd95
caps.latest.revision: 24
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# TableAdapter-Abfragekonfigurations-Assistent
Mit dem **Konfigurations\-Assistenten für TableAdapter\-Abfragen** können Sie auf einfache Weise zusätzliche Abfragen erstellen und bearbeiten, die Sie TableAdapters hinzufügen können.  Bei einer TableAdapter\-Abfrage handelt es sich um eine gültige SQL\-Abfrage oder gespeicherte Prozedur, die einen Skalarwert oder Daten zurückgibt, die demselben Schema entsprechen wie die mit dem TableAdapter verknüpfte Datentabelle.  Nach Beendigung des Assistenten wird dem TableAdapter eine Methode hinzugefügt, die bei Aufruf die Abfrage ausführt.  \(Beispiel: `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`\)  
  
## Ausführen des Assistenten  
 Ziehen Sie Abfragen auf den **Dataset\-Designer**, oder konfigurieren Sie vorhandene Abfragen \(jede Abfrage, die unterhalb der ersten Abfrage aufgeführt ist\).  
  
 Bei der ersten Abfrage in einem TableAdapter handelt es sich um die Hauptabfrage des TableAdapter.  Wenn Sie diese Hauptabfrage bearbeiten, wird der **TableAdapter\-Konfigurations\-Assistent** geöffnet und das Schema für die Datentabelle des TableAdapter bearbeitet.  Alle unterhalb der Hauptabfrage aufgeführten Abfragen sind zusätzliche Abfragen, die mit dem **Konfigurations\-Assistenten für TableAdapter\-Abfragen** konfiguriert werden.  Weitere Informationen zum Ausführen des Assistenten finden Sie unter [Gewusst wie: Starten des Konfigurations\-Assistenten für TableAdapter\-Abfragen](../Topic/How%20to:%20Start%20the%20TableAdapter%20Query%20Configuration%20Wizard.md).  
  
## Wählen Sie Ihre Datenverbindung aus  
 Wählen Sie eine vorhandene Verbindung aus der Liste der Verbindungen oder klicken Sie **Neue Verbindung** und erstellen Sie eine Verbindung zur Datenbank.  
  
 Nach Beendigung des Dialogfelds **Verbindungseigenschaften** werden im Bereich **Verbindungsdetails** schreibgeschützte Informationen zum ausgewählten Anbieter sowie zur Verbindungszeichenfolge angezeigt.  
  
## Speichern der Verbindungszeichenfolge in der Anwendungskonfigurationsdatei  
 Wählen Sie **Ja, Verbindung speichern unter** aus, um die Verbindungszeichenfolge in der Anwendungskonfigurationsdatei zu speichern.  Geben Sie einen Namen für die Verbindung ein, oder verwenden Sie den angegebenen Standardnamen.  
  
 Das Speichern von Verbindungszeichenfolgen in der Anwendungskonfigurationsdatei vereinfacht das Verwalten der Anwendung, falls die Datenbankverbindung geändert wird.  Wenn sich die Datenbankverbindung ändert, können Sie die Verbindungszeichenfolge in der Anwendungskonfigurationsdatei bearbeiten.  Auf diese Weise müssen Sie den Quellcode nicht bearbeiten und Ihre Anwendung nicht erneut kompilieren.  Informationen zum Bearbeiten einer Verbindungszeichenfolge in der Anwendungskonfigurationsdatei finden Sie unter [Gewusst wie: Speichern und Bearbeiten von Verbindungszeichenfolgen](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md).  
  
> [!IMPORTANT]
>  In der Anwendungskonfigurationsdatei werden alle Informationen als Nur\-Text gespeichert.  Um die Möglichkeit eines unberechtigten Zugriffs auf vertrauliche Daten einzuschränken, empfiehlt es sich, die Daten zu verschlüsseln.  Weitere Informationen finden Sie unter [Encrypting and Decrypting Data](http://msdn.microsoft.com/de-de/22812ae8-e082-4eb1-a29b-21b6ee00c6b5).  
  
## SQL\-Anweisungen verwenden  
 In diesem Abschnitt wird erläutert, wie Sie den **Konfigurations\-Assistenten für TableAdapter\-Abfragen** bei Auswahl der Option **SQL\-Anweisungen verwenden** ausführen.  
  
## Abfragetyp auswählen  
 In Abhängigkeit von den Anforderungen der Anwendung erstellt der Assistent mehrere Typen von Abfragen.  Sie können SELECT\-Abfragen auswählen, die Datenzeilen zurückgeben \(Datentabelle\), oder Sie können SELECT\-Abfragen auswählen, die einen Skalarwert zurückgeben \(einen Einzelwert wie `Count` oder `Sum`\).  
  
 Wählen Sie auf der Seite **Abfragetyp auswählen** die Art der Abfrage aus, die aus der Liste der verfügbaren Abfragen erstellt werden soll.  
  
> [!NOTE]
>  Das Erstellen von INSERT\-, UPDATE\- oder DELETE\-Anweisungen ist kein Ersatz für die TableAdapter\-Befehle, die beim Aufrufen der `Update`\-Methode des TableAdapter verwendet werden.  Wenn Sie z. B.den Abfragetyp UPDATE auswählen, wird eine neue Abfrage mit einem Namen erstellt, den Sie zu einem späteren Zeitpunkt im Assistenten angeben.  Sie führen diese Abfrage aus, indem Sie diese benannte Methode des TableAdapter aufrufen.  Wenn Sie die `Update`\-Methode des TableAdapter aufrufen, werden Anweisungen ausgeführt, die bei der ursprünglichen Konfiguration des TableAdapter erstellt wurden.  
  
## SQL\-\<Query Type\>\-Anweisung angeben  
 Geben Sie auf der Seite **SQL\-Anweisung angeben** die SQL\-Anweisung ein, die beim Aufrufen der Abfrage ausgeführt werden soll.  
  
> [!TIP]
>  Der Assistent ermöglicht den Zugriff auf den **Abfrage\-Generator**, ein visuelles Tool für die Erstellung von SQL\-Abfragen.  Klicken Sie zum Öffnen auf die Schaltfläche **Abfrage\-Generator**.  
  
## Methode zum Generieren auswählen  
 Auf dieser Seite finden Sie Optionen, mit denen Sie auswählen können, welche Methoden der Assistent für die Abfrage generieren soll.  
  
 **DataTable füllen**  
 Erstellt eine Methode zum Füllen der Datentabelle.  Sie übergeben den Namen der Datentabelle als Parameter, wenn Sie diese Methode aufrufen, um die Datentabelle mit den zurückgegebenen Daten zu füllen.  
  
 Optional können Sie den Standardnamen im Feld **Methodenname** ändern.  für die Verwendung von dieser Abfrage im Code kann es hilfreich sein, einen aussagekräftigen Namen anzugeben.  
  
 **DataTable zurückgeben**  
 Erstellt eine Methode zum Zurückgeben einer gefüllten Datentabelle.  In bestimmten Anwendungen kann es sinnvoller sein, gefüllte Datentabellen zurückzugeben, als vorhandene Datentabellen mit Daten zu füllen.  
  
 Optional können Sie den Standardnamen im Feld **Methodenname** ändern.  
  
## Funktionsnamen wählen  
 Geben Sie einen Namen für die Funktion ein.  Beim Erstellen einer TableAdapter\-Abfrage wird dem TableAdapter eine Methode mit dem hier angegebenen Namen hinzugefügt.  Rufen Sie diese Methode auf, um die Abfrage auszuführen.  für die Verwendung von dieser Abfrage im Code ist es hilfreich, einen aussagekräftigen Namen anzugeben.  
  
> [!NOTE]
>  Wenn Sie neue gespeicherte Prozeduren erstellen, werden Sie aufgefordert, zwei Namen einzugeben.  Der erste Name ist der Name der in der Datenbank erstellten gespeicherten Prozedur. Der zweite Name ist der Name der Methode für den TableAdapter, die bei einem entsprechenden Aufruf die gespeicherte Prozedur ausführt.  
  
## Neue gespeicherte Prozeduren erstellen  
 In diesem Abschnitt wird erläutert, welche Schritte im **Konfigurations\-Assistent für TableAdapter\-Abfragen** auszuführen sind, wenn die Option **Neue gespeicherte Prozeduren erstellen** ausgewählt wird.  
  
1.  Geben Sie auf der Seite **Gespeicherte Prozeduren generieren** die SQL\-Anweisung ein, die beim Aufrufen der gespeicherten Prozedur ausgeführt werden soll.  
  
    > [!NOTE]
    >  Der Assistent ermöglicht den Zugriff auf den **Abfrage\-Generator**, ein visuelles Tool für die Erstellung von SQL\-Abfragen.  Klicken Sie zum Öffnen auf die Schaltfläche **Abfrage\-Generator**.  
  
2.  Gehen Sie auf der Seite **Gespeicherte Prozeduren erstellen** folgendermaßen vor:  
  
    1.  Geben Sie einen Namen für die neue gespeicherte Prozedur ein.  
  
    2.  Geben Sie an, ob die gespeicherte Prozedur in der zugrunde liegenden Datenbank erstellt werden soll.  
  
        > [!NOTE]
        >  Die Möglichkeit zum Erstellen einer gespeicherten Prozedur in der Datenbank ist von den Sicherheitseinstellung der betreffenden Datenbank abhängig.  
  
     Auf der Seite **Assistentenergebnisse anzeigen** werden die Ergebnisse für das Erstellen der TableAdapter\-Abfrage angezeigt.  Wenn im Assistenten Probleme auftreten, werden auf dieser Seite die Fehlerinformationen angezeigt.  
  
## Vorhandene gespeicherte Prozeduren verwenden  
 In diesem Abschnitt wird erläutert, welche Schritte im **Konfigurations\-Assistent für TableAdapter\-Abfragen** auszuführen sind, wenn die Option **Vorhandene gespeicherte Prozeduren verwenden** ausgewählt wird.  
  
1.  Wählen Sie auf der Seite **Vorhandene gespeicherte Prozedur auswählen** des Assistenten eine vorhandene gespeicherte Prozedur aus der Dropdownliste aus.  
  
     Zu Referenzzwecken werden die **Parameter** und die **Ergebnisse** für die ausgewählte gespeicherte Prozedur angezeigt.  
  
2.  Klicken Sie auf **Weiter**.  
  
## Von der gespeicherten Prozedur zurückgegebene Form der Daten auswählen  
 Der Typ der von der ausgewählten gespeicherten Prozedur zurückgegebenen Daten bestimmt, wie der Assistent die TableAdapter\-Methoden erstellt.  
  
 Wählen Sie den Datentyp aus, der von dieser Abfrage zurückgegeben werden soll.  
  
-   Wenn Sie **Tabellendaten** auswählen, wird die Seite **Zu generierende Methode auswählen** geöffnet \(auf dieser Hilfeseite an früherer Stelle beschrieben\). Hier können Sie die zu erstellenden Typen und Namen von Methoden angeben sowie die Pagingunterstützung festlegen.  
  
-   Wenn Sie **Einzelner Wert** auswählen, wird eine typisierte Methode erstellt, die einen einzelnen Wert zurückgibt.  Mit dieser Option wird die Seite **Funktionsnamen wählen** geöffnet \(auf dieser Hilfeseite an früherer Stelle beschrieben\).  
  
-   Wenn Sie **Kein Wert** auswählen, wird eine typisierte Methode erstellt, die die gespeicherte Prozedur ausführt und keine Datenrückgabe erwartet.  Mit dieser Option wird die Seite **Funktionsnamen wählen** geöffnet \(auf dieser Hilfeseite an früherer Stelle beschrieben\).  
  
## Anzeigen der Assistentenergebnisse  
 Auf der Seite **Assistentenergebnisse anzeigen** werden die Ergebnisse für das Erstellen der TableAdapter\-Abfrage angezeigt.  Wenn im Assistenten Probleme aufgetreten sind, werden die entsprechenden Details auf dieser Seite angezeigt.  
  
## Siehe auch  
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Gewusst wie: Bearbeiten von TableAdapter\-Abfragen](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)