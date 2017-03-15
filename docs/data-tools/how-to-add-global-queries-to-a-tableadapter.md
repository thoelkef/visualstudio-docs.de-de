---
title: "Gewusst wie: Hinzuf&#252;gen von globalen Abfragen zu einem Dataset | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Daten [Visual Studio], TableAdapters"
  - "Datasets [Visual Basic], Globale Funktionen"
  - "Datasets [Visual Basic], Skalare Funktionen"
  - "Globale Funktionen, Datasets"
  - "Abfragen [Visual Studio], TableAdapters"
  - "Skalare Funktionen, Datasets"
  - "TableAdapter-Abfragen"
  - "TableAdapter-Abfragekonfigurations-Assistent"
  - "TableAdapters, Globale Abfragen"
ms.assetid: 4abffd6b-2e9f-4ef3-99b2-6e9ae4ad4679
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Gewusst wie: Hinzuf&#252;gen von globalen Abfragen zu einem Dataset
*Globale Abfragen* sind SQL\-Abfragen, die entweder einen einzelnen Wert \(Skalarwert\) oder keinen Wert zurückgeben.  Globale Funktionen führen normalerweise Datenbankoperation wie Einfüge\-, Aktualisierungs\- und Löschvorgänge sowie das Sammeln von Informationen aus. Beispielsweise geben sie eine Anzahl von Kunden in einer Tabelle zurück oder die Gesamtkosten für alle Posten eines bestimmten Auftrags.  
  
 Globale Abfragen werden hinzugefügt, indem der **Konfigurations\-Assistent für TableAdapter\-Abfragen** innerhalb des **DataSet\-Designers** ausgeführt wird.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### So fügen Sie einem Dataset eine globale Abfrage hinzu  
  
1.  Öffnen Sie ein Dataset im **Dataset\-Designer**.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen eines Datasets im DataSet\-Designer](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Ziehen Sie eine **Abfrage** von der Registerkarte **DataSet** der **Toolbox** auf einen leeren Bereich im **DataSet\-Designer**.  
  
     Der [TableAdapter\-Abfragekonfigurations\-Assistent](../data-tools/editing-tableadapters.md) wird geöffnet.  
  
3.  Wählen Sie eine Verbindung für die gewünschte Abfrage aus.  Sie können entweder eine Abfrage aus der Liste auswählen oder eine neue Verbindung erstellen.  Wenn Sie eine neue Verbindung erstellen, können Sie diese in der Anwendungskonfigurationsdatei speichern.  Weitere Informationen finden Sie unter [Gewusst wie: Speichern und Bearbeiten von Verbindungszeichenfolgen](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md).  
  
4.  Wählen Sie aus, ob Sie SQL\-Anweisungen oder gespeicherte Prozeduren verwenden möchten.  
  
5.  Wählen Sie zu verwendende gespeicherte Prozedur aus, oder wählen Sie auf der Seite **Abfragetyp auswählen** des Assistenten den gewünschten Typ der Abfrage aus, und klicken Sie dann auf **Weiter**.  
  
6.  Stellen Sie eine Abfrage bereit, die die gewünschte Aufgabe ausführt, z. B. `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  Wenn Sie eine Abfrage direkt auf den **DataSet\-Designer** ziehen, wird eine Methode erstellt, die nur einen Skalarwert \(einzelnen Wert\) zurückgibt.  Die ausgewählte Abfrage oder gespeicherte Prozedur gibt möglicherweise mehr als einen einzelnen Wert zurück, die vom Assistenten erstellte Methode gibt aber nur einen einzelnen Wert zurück.  Zum Beispiel kann die Abfrage die erste Spalte der ersten Zeile der zurückgegebenen Daten zurückgeben.  
  
7.  Beenden Sie den Assistenten. Die Abfrage wird dem **DataSet\-Designer** hinzugefügt.  Informationen zum Ausführen der Abfrage finden Sie unter [Gewusst wie: Ausführen von TableAdapter\-Abfragen](../Topic/How%20to:%20Execute%20TableAdapter%20Queries.md).  
  
## Siehe auch  
 [Gewusst wie: Erstellen von TableAdapters](../data-tools/create-and-configure-tableadapters.md)   
 [Gewusst wie: Erstellen von TableAdapter\-Abfragen](../data-tools/how-to-create-tableadapter-queries.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md)   
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)   
 [Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Gewusst wie: Datennavigation mithilfe des DataNavigator\-Steuerelements in Windows Forms](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)   
 [Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)