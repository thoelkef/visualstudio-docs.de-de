---
title: Bearbeiten von TableAdapters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.dbtablefunctionwizard
- vs.datasource.datacomponentquerywizard
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data component queries
- data [Visual Studio], TableAdapters
- TableAdapter Query Configuration Wizard
- data [Visual Studio], table adapter queries
ms.assetid: 8c06b306-24d0-4521-948d-07e3b7badd95
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 995c1cfb5b125437847f364a01b66f3e551b8b4e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522817"
---
# <a name="editing-tableadapters"></a>Bearbeiten von TableAdapters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Möglicherweise möchten das Schema der Tabelle des Adapters ändern. Zu diesem Zweck ändern Sie den Adapter der primäre `Fill` Methode. TableAdapter-Erstellung mit einer primären `Fill` -Methode, die das Schema der zugeordneten Datentabelle definiert. Die Main `Fill` Methode basiert auf der Abfrage oder gespeicherte Prozedur Sie eingegeben haben, wenn Sie den TableAdapter ursprünglich konfiguriert; es ist die erste (oberste)-Methode in der Datentabelle, auf die [erstellen und Bearbeiten typisierter Datasets](../data-tools/creating-and-editing-typed-datasets.md).  
  
 ![TableAdapter mit mehreren Abfragen](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Alle Änderungen, die Sie dem TableAdapter vornehmen Hauptthread `Fill` Methode werden in das Schema der zugeordneten Datentabelle wiedergegeben. Z. B. das Entfernen einer Spalte aus der Abfrage auf dem hauptblatt `Fill` Methode wird auch die Spalte aus der zugeordneten Datentabelle entfernt. Außerdem entfernen Sie die Spalte aus dem Hauptknoten `Fill` Methode entfernt die Spalte aus etwaigen zusätzlichen Abfragen für diesen TableAdapter.  
  
 Sie können die **Konfigurations-Assistenten für TableAdapter-Abfragen** erstellen und Bearbeiten zusätzliche Abfragen für den TableAdapter. Diese zusätzlichen Abfragen müssen das Tabellenschema entsprechen, wenn sie einen skalaren Wert zurückgeben.  Die zusätzlichen Abfragen haben einen Namen, den Sie angeben (z. B. `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`.)  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Zum Starten des TableAdapter-Abfrage-Konfigurations-Assistenten mit einer neuen Abfrage  
  
1.  Öffnen Sie das Dataset in den **Dataset-Designer**.  
  
2.  Wenn Sie eine neue Abfrage erstellen, ziehen Sie eine **Abfrage** -Objekt aus der **DataSet** auf der Registerkarte die **Toolbox** auf eine <xref:System.Data.DataTable>, oder wählen Sie **AbfrageHinzufügen**im Kontextmenü des TableAdapter. Sie können auch ziehen eine **Abfrage** Objekt auf einen leeren Bereich, der die **Dataset-Designer**, erstellt einen TableAdapter ohne einen zugehörigen <xref:System.Data.DataTable>. Diese Abfragen sind beschränkt auf einzelne Werte (Skalarwert) zurückgeben oder Ausführen von Update-, INSERT- oder DELETE-Befehle für die Datenbank. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen von globalen Abfragen zu einem TableAdapter](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).  
  
3.  Auf der **wählen Sie Ihre Datenverbindung** Seite wählen oder erstellen Sie die Verbindung der Abfrage verwendet wird.  
  
    > [!NOTE]
    >  Auf dieser Seite wird nur angezeigt, wenn der Designer nicht die richtige zu verwendende Verbindung bestimmen kann, oder wenn keine Verbindungen verfügbar sind.  
  
4.  Auf der **wählen Sie einen Befehlstyp aus** Seite aus der folgenden Methoden zum Abrufen von Daten aus der Datenbank:  
  
    -   **Verwenden von SQL-Anweisungen** ermöglicht es Ihnen, geben Sie eine SQL-Anweisung, um die Daten aus der Datenbank auszuwählen.  
  
    -   **Erstellen Sie neue gespeicherte Prozedur** – wählen Sie diese Option, damit der Assistent eine neue gespeicherte Prozedur (in der Datenbank), der basierend auf der angegebenen SELECT-Anweisung zu erstellen.  
  
    -   **Vorhandene gespeicherte Prozeduren verwenden** – wählen Sie diese Option, um eine vorhandene gespeicherte Prozedur ausgeführt werden soll, wenn die Abfrage ausgeführt.  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Zum Starten des TableAdapter-Abfrage-Konfigurations-Assistenten auf eine vorhandene Abfrage  
  
-   Wenn Sie eine vorhandene TableAdapter-Abfrage bearbeiten, mit der rechten Maustaste in der Abfrage aus, und wählen **konfigurieren** aus dem Kontextmenü.  
  
    > [!NOTE]
    >  Mit der rechten Maustaste in der Hauptabfrage des TableAdapter wird den TableAdapter und <xref:System.Data.DataTable> Schema, während eine weitere Abfrage für einen TableAdapter einen Rechtsklick auf nur konfiguriert die ausgewählte Abfrage. Die **TableAdapter-Konfigurations-Assistenten** wird die TableAdapter-Definition, die **Konfigurations-Assistenten für TableAdapter-Abfragen** wird nur die ausgewählte Abfrage.  
  
## <a name="running-the-wizard"></a>Ausführen des Assistenten  
 Ziehen Sie Abfragen auf die **Dataset-Designer**, oder konfigurieren Sie vorhandene Abfragen (jede Abfrage, die unterhalb der ersten Abfrage aufgeführt).  
  
 Bei der ersten Abfrage in einem TableAdapter handelt es sich um die Hauptabfrage des TableAdapter. Diese Hauptabfrage bearbeiten Öffnet die **TableAdapter-Konfigurations-Assistenten** und das Schema der Datentabelle des TableAdapter bearbeitet. Alle unterhalb der Hauptabfrage aufgeführten Abfragen sind zusätzliche Abfragen und werden mithilfe von konfiguriert die **Konfigurations-Assistenten für TableAdapter-Abfragen**. Weitere Informationen zum Ausführen des Assistenten finden Sie unter [Vorgehensweise: Starten Sie den Konfigurations-Assistenten für TableAdapter-Abfrage](http://msdn.microsoft.com/library/fc7b468e-3417-48a4-a8aa-cace8f99c24a).  
  
## <a name="choose-your-data-connection"></a>Wählen Sie Ihre Datenverbindung aus  
 Wählen Sie eine vorhandene Verbindung aus der Liste der Verbindungen oder klicken Sie auf **neue Verbindung** um eine Verbindung mit Ihrer Datenbank zu erstellen.  
  
 Nach Abschluss der **Verbindungseigenschaften** im Dialogfeld die **Verbindungsdetails** Bereich zeigt schreibgeschützte Informationen zu den ausgewählten Anbieter sowie die Verbindungszeichenfolge.  
  
## <a name="save-the-connection-string-to-the-application-configuration-file"></a>Speichern der Verbindungszeichenfolge in der Anwendungskonfigurationsdatei  
 Wählen Sie **Ja, Verbindung speichern unter** zum Speichern der Verbindungszeichenfolge in der Konfigurationsdatei der Anwendung. Geben Sie einen Namen für die Verbindung ein, oder verwenden Sie den angegebenen Standardnamen.  
  
 Das Speichern von Verbindungszeichenfolgen in der Anwendungskonfigurationsdatei vereinfacht das Verwalten der Anwendung, falls die Datenbankverbindung geändert wird. Wenn sich die Datenbankverbindung ändert, können Sie die Verbindungszeichenfolge in der Anwendungskonfigurationsdatei bearbeiten. Auf diese Weise müssen Sie den Quellcode nicht bearbeiten und Ihre Anwendung nicht erneut kompilieren. Weitere Informationen zum Bearbeiten einer Verbindungszeichenfolge in der Anwendungskonfigurationsdatei befindet, finden Sie unter [Vorgehensweise: Speichern und Bearbeiten von Verbindungszeichenfolgen](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
> [!IMPORTANT]
>  In der Anwendungskonfigurationsdatei werden alle Informationen als Nur-Text gespeichert. Um die Möglichkeit eines unberechtigten Zugriffs auf vertrauliche Daten einzuschränken, empfiehlt es sich, die Daten zu verschlüsseln. Weitere Informationen finden Sie unter [verschlüsseln und Entschlüsseln von Daten](http://msdn.microsoft.com/en-us/22812ae8-e082-4eb1-a29b-21b6ee00c6b5).  
  
## <a name="use-sql-statements"></a>SQL-Anweisungen verwenden  
 In diesem Abschnitt wird erläutert, wie zum Abschließen der **Konfigurations-Assistenten für TableAdapter-Abfragen** bei der Auswahl der **SQL-Anweisungen** Option.  
  
## <a name="choose-a-query-type"></a>Abfragetyp auswählen  
 In Abhängigkeit von den Anforderungen der Anwendung erstellt der Assistent mehrere Typen von Abfragen. Sie können SELECT-Abfragen auswählen, die Datenzeilen zurückgeben (Datentabelle), oder Sie können SELECT-Abfragen auswählen, die einen Skalarwert zurückgeben (einen Einzelwert wie `Count` oder `Sum`).  
  
 Auf der **Abfragetyp auswählen** Seite, wählen Sie den Typ der Abfrage aus der Liste der verfügbaren Abfragen erstellt.  
  
> [!NOTE]
>  Das Erstellen von INSERT-, UPDATE- oder DELETE-Anweisungen ist kein Ersatz für die TableAdapter-Befehle, die beim Aufrufen der `Update`-Methode des TableAdapter verwendet werden. Wenn Sie z. B.den Abfragetyp UPDATE auswählen, wird eine neue Abfrage mit einem Namen erstellt, den Sie zu einem späteren Zeitpunkt im Assistenten angeben. Sie führen diese Abfrage aus, indem Sie diese benannte Methode des TableAdapter aufrufen. Wenn Sie die `Update`-Methode des TableAdapter aufrufen, werden Anweisungen ausgeführt, die bei der ursprünglichen Konfiguration des TableAdapter erstellt wurden.  
  
## <a name="specify-a-sql-query-type-statement"></a>Geben Sie eine SQL \<Abfragetyp >-Anweisung  
 Auf der **Geben Sie eine SQL-Anweisung** geben die SQL-Anweisung, die bei Aufrufen der Abfrage.  
  
> [!TIP]
>  Der Assistent ermöglicht den Zugriff auf die **Abfragegenerator**, ein visuelles Tool zum Erstellen von SQL-Abfragen. Um es zu öffnen, klicken Sie auf die **Abfragegenerator** Schaltfläche.  
  
## <a name="choose-methods-to-generate"></a>Methode zum Generieren auswählen  
 Auf dieser Seite finden Sie Optionen, mit denen Sie auswählen können, welche Methoden der Assistent für die Abfrage generieren soll.  
  
 **DataTable füllen**  
 Erstellt eine Methode zum Füllen der Datentabelle. Sie übergeben den Namen der Datentabelle als Parameter, wenn Sie diese Methode aufrufen, um die Datentabelle mit den zurückgegebenen Daten zu füllen.  
  
 Optional können Sie den Standardnamen im Ändern der **Methodenname** Feld. für die Verwendung von dieser Abfrage im Code kann es hilfreich sein, einen aussagekräftigen Namen anzugeben.  
  
 **DataTable zurückgeben**  
 Erstellt eine Methode zum Zurückgeben einer gefüllten Datentabelle. In bestimmten Anwendungen kann es sinnvoller sein, gefüllte Datentabellen zurückzugeben, als vorhandene Datentabellen mit Daten zu füllen.  
  
 Optional können Sie den Standardnamen im Ändern der **Methodenname** Feld.  
  
## <a name="choose-function-name"></a>Funktionsnamen wählen  
 Geben Sie einen Namen für die Funktion ein. Beim Erstellen einer TableAdapter-Abfrage wird dem TableAdapter eine Methode mit dem hier angegebenen Namen hinzugefügt. Rufen Sie diese Methode auf, um die Abfrage auszuführen. für die Verwendung von dieser Abfrage im Code ist es hilfreich, einen aussagekräftigen Namen anzugeben.  
  
> [!NOTE]
>  Wenn Sie neue gespeicherte Prozeduren erstellen, werden Sie aufgefordert, zwei Namen einzugeben. Der erste Name ist der Name der in der Datenbank erstellten gespeicherten Prozedur. Der zweite Name ist der Name der Methode für den TableAdapter, die bei einem entsprechenden Aufruf die gespeicherte Prozedur ausführt.  
  
## <a name="create-new-stored-procedures"></a>Neue gespeicherte Prozeduren erstellen  
 In diesem Abschnitt wird erläutert, wie zum Abschließen der **Konfigurations-Assistenten für TableAdapter-Abfragen** bei der Auswahl der **neue gespeicherte Prozeduren erstellen** Option.  
  
1.  In der **gespeicherte Prozeduren generieren** geben die SQL-Anweisung, die bei Aufrufen der gespeicherten Prozedur.  
  
    > [!NOTE]
    >  Der Assistent ermöglicht den Zugriff auf die **Abfragegenerator**, ein visuelles Tool zum Erstellen von SQL-Abfragen. Um es zu öffnen, klicken Sie auf die **Abfragegenerator** Schaltfläche.  
  
2.  In der **gespeicherte Prozeduren erstellen** Seite, gehen Sie folgendermaßen vor:  
  
    1.  Geben Sie einen Namen für die neue gespeicherte Prozedur ein.  
  
    2.  Geben Sie an, ob die gespeicherte Prozedur in der zugrunde liegenden Datenbank erstellt werden soll.  
  
        > [!NOTE]
        >  Die Möglichkeit zum Erstellen einer gespeicherten Prozedur in der Datenbank ist von den Sicherheitseinstellung der betreffenden Datenbank abhängig.  
  
     Die **Assistentenergebnisse anzeigen** Seite zeigt die Ergebnisse der Erstellung der TableAdapter-Abfrage. Wenn im Assistenten Probleme auftreten, werden auf dieser Seite die Fehlerinformationen angezeigt.  
  
## <a name="use-existing-stored-procedures"></a>Vorhandene gespeicherte Prozeduren verwenden  
 In diesem Abschnitt wird erläutert, wie zum Abschließen der **Konfigurations-Assistenten für TableAdapter-Abfragen** bei der Auswahl der **vorhandene gespeicherte Prozeduren verwenden** Option.  
  
1.  Wählen Sie eine vorhandene gespeicherte Prozedur aus der Dropdown-Liste auf die **wählen Sie eine vorhandene gespeicherte Prozedur** Seite des Assistenten.  
  
     Die **Parameter** und **Ergebnisse** für die ausgewählte gespeicherte Prozedur zu Referenzzwecken angezeigt werden.  
  
2.  Klicken Sie auf **Weiter**.  
  
## <a name="choose-the-shape-of-data-returned-by-the-stored-procedure"></a>Von der gespeicherten Prozedur zurückgegebene Form der Daten auswählen  
 Der Typ der von der ausgewählten gespeicherten Prozedur zurückgegebenen Daten bestimmt, wie der Assistent die TableAdapter-Methoden erstellt.  
  
 Wählen Sie den Datentyp aus, der von dieser Abfrage zurückgegeben werden soll.  
  
-   Auswählen von **Tabellendaten** öffnet die **zu generierende Methode auswählen** -Seite (oben beschrieben, auf dieser Hilfeseite), die Sie angeben, die Typen von Methoden, Methodennamen und Unterstützung von Paging erstellt werden kann.  
  
-   Auswählen von **einen einzelnen Wert** erstellt eine typisierte Methode, die einen einzelnen Wert zurückgibt. Diese Option öffnet der **Funktionsnamen wählen** Seite (auf dieser Hilfeseite an früherer Stelle beschrieben).  
  
-   Auswählen von **kein Wert** erstellt eine typisierte Methode, die die gespeicherte Prozedur ausführt und erwartet, dass keine Daten zurückgegeben werden. Diese Option öffnet der **Funktionsnamen wählen** Seite (auf dieser Hilfeseite an früherer Stelle beschrieben).  
  
## <a name="view-wizards-results"></a>Anzeigen der Assistentenergebnisse  
 Die **Assistentenergebnisse anzeigen** Seite zeigt die Ergebnisse der Erstellung der TableAdapter-Abfrage. Wenn im Assistenten Probleme aufgetreten sind, werden die entsprechenden Details auf dieser Seite angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Vorgehensweise: Bearbeiten von TableAdapter-Abfragen](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Exemplarische Vorgehensweisen für Daten](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen einer Verbindung mit Daten in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung zum Empfangen von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Abrufen von Daten für Ihre Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in Ihrer Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Speichern von Daten](../data-tools/saving-data.md)