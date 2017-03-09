---
title: "Gewusst wie: Ausf&#252;hren eines Commit f&#252;r &#196;nderungen in einem Dataset | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataSet.AcceptChanges"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Datasets [Visual Basic], Übernehmen von Änderungen"
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Gewusst wie: Ausf&#252;hren eines Commit f&#252;r &#196;nderungen in einem Dataset
Während Sie die Datensätze in einem Dataset ändern, indem Sie Datensätze aktualisieren, einfügen und löschen, werden im Dataset ursprüngliche und aktuelle Versionen der einzelnen Datensätze abgelegt.  Außerdem verfolgt die <xref:System.Data.DataRow.RowState%2A>\-Eigenschaft jeder Zeile, ob die Datensätze im ursprünglichen Zustand vorliegen oder ob sie aktualisiert, eingefügt oder gelöscht wurden.  Diese Informationen sind bei der Suche nach einer bestimmten Zeilenversion von Nutzen.  Normalerweise würden Sie eine Teilmenge aller geänderten Datensätze abrufen, die an einen anderen Prozess gesendet werden sollen.  Weitere Informationen finden Sie unter [Gewusst wie: Abrufen von geänderten Zeilen](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md).  Nachdem Sie alle geänderten Zeilen verarbeitet haben, können Sie einen Commit für die Änderungen ausführen. Rufen Sie dazu die `AcceptChanges`\-Methode von <xref:System.Data.DataSet>, <xref:System.Data.DataTable> oder <xref:System.Data.DataRow> auf.  Die `AcceptChanges`\-Methode wird automatisch aufgerufen, wenn die Update\-Methoden von einem [TableAdapter](../data-tools/tableadapter-overview.md) oder einem Datenadapter aufgerufen werden.  Rufen Sie `AcceptChanges` auf, nachdem Sie die Änderungen an eine Datenbank gesendet haben.  
  
 Wenn Sie <xref:System.Data.DataSet.AcceptChanges%2A> für <xref:System.Data.DataSet> aufrufen, werden die Bearbeitungsvorgänge von allen <xref:System.Data.DataRow>\-Objekten erfolgreich beendet, die sich noch im Bearbeitungsmodus befinden.  Die <xref:System.Data.DataRow.RowState%2A>\-Eigenschaft jeder <xref:System.Data.DataRow> ändert sich ebenfalls, <xref:System.Data.DataRowState>\-Zeilen und <xref:System.Data.DataRowState>\-Zeilen werden <xref:System.Data.DataRowState>, und <xref:System.Data.DataRowState>\-Zeilen werden entfernt.  
  
 Wenn <xref:System.Data.DataSet> <xref:System.Data.ForeignKeyConstraint>\-Objekte enthält, tritt durch Aufrufen der <xref:System.Data.DataSet.AcceptChanges%2A>\-Methode auch die <xref:System.Data.AcceptRejectRule> in Kraft.  
  
### So führen Sie einen Commit für Änderungen in einem Dataset aus  
  
-   Rufen Sie die `AcceptChanges`\-Methode entweder an <xref:System.Data.DataSet>, an <xref:System.Data.DataTable> oder an <xref:System.Data.DataRow> auf, um den Commit für die Änderungen in diesen Objekten auszuführen.  
  
     Im folgenden Beispiel wird gezeigt, wie die `AcceptChanges`\-Methode aufgerufen wird, um einen Commit für Änderungen in der `Customers`\-Tabelle auszuführen, nachdem eine Datenquelle aktualisiert wurde:  
  
     [!code-cs[VbRaddataEditing#11](../data-tools/codesnippet/CSharp/how-to-commit-changes-in-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#11](../data-tools/codesnippet/VisualBasic/how-to-commit-changes-in-a-dataset_1.vb)]  
  
## Siehe auch  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [Speichern von Daten](../data-tools/saving-data.md)   
 [Gewusst wie: Abrufen von geänderten Zeilen](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md)