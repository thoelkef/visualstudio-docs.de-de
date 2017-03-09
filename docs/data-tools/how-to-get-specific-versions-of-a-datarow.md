---
title: "Gewusst wie: Abrufen spezifischer Versionen einer DataRow | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "DataRow-Objekt"
  - "Zeilenzustände"
  - "Aktualisieren von Datasets, Zeilenzustände"
ms.assetid: d7cde25e-cef5-4559-b994-be00e258ac1f
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Gewusst wie: Abrufen spezifischer Versionen einer DataRow
Wenn an Datenzeilen Änderungen vorgenommen werden, werden im Dataset sowohl die ursprüngliche \(<xref:System.Data.DataRowVersion>\) als auch die neue \(<xref:System.Data.DataRowVersion>\) Version der Zeile beibehalten.  Vor dem Aufruf der `AcceptChanges`\-Methode kann die Anwendung z. B. auf die verschiedenen \(in der <xref:System.Data.DataRowVersion>\-Enumeration definierten\) Versionen eines Datensatzes zugreifen und die Änderungen entsprechend verarbeiten.  
  
> [!NOTE]
>  Verschiedene Versionen einer Zeile sind nur verfügbar, wenn diese schon bearbeitet, die `AcceptChanges`\-Methode jedoch noch nicht aufgerufen wurde.  Nach dem Aufruf der `AcceptChanges`\-Methode sind die ursprüngliche und die aktuelle Version identisch.  
  
 Wenn Sie den <xref:System.Data.DataRowVersion>\-Wert zusammen mit dem Spaltenindex \(oder dem Spaltennamen als Zeichenfolge\) übergeben, wird der Wert der spezifischen Zeilenversion aus dieser Spalte zurückgegeben.  Die geänderte Spalte wird während der Ausführung des <xref:System.Data.DataTable.ColumnChanging>\-Ereignisses und des <xref:System.Data.DataTable.ColumnChanged>\-Ereignisses identifiziert. Dies ist darum der geeignete Zeitpunkt, um die unterschiedlichen Zeilenversionen zu Validierungszwecken zu untersuchen.  Wenn Sie Einschränkungen jedoch vorübergehend deaktiviert haben, werden diese Ereignisse nicht ausgelöst, sodass die geänderten Spalten programmgesteuert ermittelt werden müssen.  Sie können dazu die <xref:System.Data.DataTable.Columns%2A>\-Auflistung durchlaufen und die unterschiedlichen <xref:System.Data.DataRowVersion>\-Werte vergleichen.  
  
## Zugreifen auf die ursprüngliche Version einer DataRow  
  
#### So rufen Sie die ursprüngliche Datensatzversion ab  
  
-   Greifen Sie auf den Wert einer Spalte zu, und übergeben Sie die <xref:System.Data.DataRowVersion> der Zeile, die zurückgegeben werden soll.  
  
     Das folgende Beispiel veranschaulicht, wie Sie mithilfe eines <xref:System.Data.DataRowVersion>\-Werts den ursprünglichen Wert eines `CompanyName`\-Felds in einer <xref:System.Data.DataRow> abrufen:  
  
     [!code-cs[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/how-to-get-specific-versions-of-a-datarow_1.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/how-to-get-specific-versions-of-a-datarow_1.vb)]  
  
## Zugreifen auf die aktuelle Version einer DataRow  
  
#### So rufen Sie die aktuelle Datensatzversion ab  
  
-   Greifen Sie auf einen Spaltenwert zu, und fügen Sie dem Index einen Parameter hinzu, durch den die zurückzugebende Zeilenversion angegeben wird.  
  
     Im folgenden Beispiel wird veranschaulicht, wie Sie mithilfe eines <xref:System.Data.DataRowVersion>\-Werts den aktuellen Wert eines `CompanyName`\-Felds in einer <xref:System.Data.DataRow> abrufen:  
  
     [!code-cs[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/how-to-get-specific-versions-of-a-datarow_2.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/how-to-get-specific-versions-of-a-datarow_2.vb)]  
  
## Siehe auch  
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)   
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)