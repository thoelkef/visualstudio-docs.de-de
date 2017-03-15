---
title: "Gewusst wie: Erstellen von TableAdapter-Abfragen | Microsoft Docs"
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
  - "Daten [Visual Studio], TableAdapter-Abfragen"
  - "Abfragen [Visual Studio], Erstellen"
  - "Abfragen [Visual Studio], TableAdapters"
  - "TableAdapters, Erstellen von Abfragen"
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Gewusst wie: Erstellen von TableAdapter-Abfragen
TableAdapter\-Abfragen sind SQL\-Anweisungen oder gespeicherte Prozeduren, die von der Anwendung für eine Datenbank ausgeführt werden können.  
  
 Fügen Sie einem TableAdapter so viele Abfragen wie für die Anwendung erforderlich hinzu.  TableAdapter\-Abfragen werden in einem TableAdapter als Methoden angezeigt.  Wenn Sie die Abfrage `FillByCity` erstellen, die einen Parameter annimmt, der den Wert für den Ort darstellt, wird die Abfrage dem TableAdapter hinzugefügt.  Sie wird als typisierte Methode hinzugefügt, die den richtigen Parametertyp als Argument annimmt, in diesem Falle eine Zeichenfolge, die den Wert für den Ort darstellt.  Sie rufen die TableAdapter\-Abfrage einfach wie jede andere Methode für ein beliebiges Objekt auf.  Der folgende Code führt z. B. die `FillByCity`\-Abfrage aus und füllt die `Customers`\-Tabelle mit allen Kunden mit dem Ortswert `Seattle` auf:  
  
 [!code-vb[VbRaddataTableAdapters#1](../data-tools/codesnippet/VisualBasic/how-to-create-tableadapter-queries_1.vb)]
 [!code-cs[VbRaddataTableAdapters#1](../data-tools/codesnippet/CSharp/how-to-create-tableadapter-queries_1.cs)]  
  
 TableAdapter\-Abfragen können Datentabellen füllen \(`Fill`\-Abfrage und `FillBy`\-Abfrage\) oder neue Datentabellen zurückgeben, die mit den Daten aufgefüllt sind, die von der Abfrage \(`GetData`\-Abfrage und `GetDataBy`\-Abfrage\) zurückgegeben werden.  
  
 Sie können vorhandenen TableAdapters Abfragen hinzufügen, indem Sie den [TableAdapter\-Abfragekonfigurations\-Assistent](../data-tools/editing-tableadapters.md) ausführen.  \(Klicken Sie mit der rechten Maustaste auf einen beliebigen TableAdapter, und wählen Sie **Abfrage hinzufügen** aus.\)  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Erstellen einer Abfrage im Dataset\-Designer  
  
#### So fügen Sie einem TableAdapter im Dataset\-Designer eine Abfrage hinzu  
  
1.  Öffnen Sie ein Dataset im **Dataset\-Designer**.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen eines Datasets im DataSet\-Designer](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Klicken Sie mit der rechten Maustaste auf den gewünschten TableAdapter, und wählen Sie **Abfrage hinzufügen** aus.  
  
     \- oder \-  
  
3.  Ziehen Sie in der **Toolbox** aus der Registerkarte **DataSet** eine **Abfrage** auf eine Tabelle im Designer.  
  
     Der **Konfigurations\-Assistent für TableAdapter\-Abfragen** wird geöffnet.  
  
4.  Stellen Sie den Assistenten fertig. Die Abfrage wird dem TableAdapter hinzugefügt.  
  
## Direktes Erstellen einer Abfrage auf einem Formular in der Windows\-Anwendung  
 Wenn auf dem Formular eine Instanz eines TableAdapter vorhanden ist, können Sie in der [Dialogfeld "Suchkriterien\-Generator"](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md) eine Abfrage hinzufügen, womit dem Formular ein <xref:System.Windows.Forms.ToolStrip>\-Steuerelement, das alle von der Abfrage angeforderten Eingabeparameter akzeptiert, sowie eine Schaltfläche zum Ausführen der Abfrage hinzugefügt werden.  
  
#### So fügen Sie einem TableAdapter über das Dialogfeld Suchkriterien eine Abfrage hinzu  
  
1.  Wählen Sie einen TableAdapter auf der Komponentenleiste aus.  
  
2.  Klicken Sie auf das Smarttag des TableAdapter, und wählen Sie **Abfrage hinzufügen** aus.  
  
3.  Füllen Sie das Dialogfeld aus. Die Abfrage wird dann dem TableAdapter hinzugefügt.  Weitere Informationen finden Sie unter [Dialogfeld "Suchkriterien\-Generator"](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
## Siehe auch  
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Gewusst wie: Bearbeiten von TableAdapter\-Abfragen](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md)   
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)   
 [Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Gewusst wie: Datennavigation mithilfe des DataNavigator\-Steuerelements in Windows Forms](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)   
 [Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Exemplarische Vorgehensweise: Erstellen eines TableAdapter mit mehreren Abfragen](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)