---
title: "Gewusst wie: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Daten [Office-Entwicklung in Visual Studio], Zwischenspeichern"
  - "Zwischenspeichern von Daten [Office-Entwicklung in Visual Studio], Programmgesteuert"
  - "Datasets [Office-Entwicklung in Visual Studio], Zwischenspeichern"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Daten"
  - "StartCaching-Methode"
ms.assetid: 70b3fc06-7534-407e-898b-36f84e9a7516
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Gewusst wie: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument
  Sie können dem Datencache in einem Dokument programmgesteuert ein Datenobjekt hinzufügen, indem Sie die `StartCaching`\-Methode eines Hostelements aufrufen \(also z. B. in einem <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook> oder <xref:Microsoft.Office.Tools.Excel.Worksheet>\).  Entfernen Sie ein Datenobjekt aus dem Datencache, indem Sie die `StopCaching`\-Methode eines Hostelements aufrufen.  
  
 Die `StartCaching`\-Methode und die `StopCaching`\-Methode sind private\-Methoden, sie werden jedoch in IntelliSense angezeigt.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Wenn Sie die `StartCaching`\-Methode für das Hinzufügen eines Datenobjekts zum Datencache verwenden, muss das Datenobjekt nicht mit dem <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>\-Attribut deklariert werden.  Das Datenobjekt muss jedoch bestimmte Anforderungen erfüllen, damit es dem Datencache hinzugefügt werden kann.  Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).  
  
### So können Sie ein Datenobjekt programmgesteuert im Cache zwischenspeichern  
  
1.  Deklarieren Sie das Datenobjekt auf Klassenebene und nicht innerhalb einer Methode.  In diesem Beispiel wird davon ausgegangen, dass Sie ein <xref:System.Data.DataSet> mit dem Namen `dataSet1` deklarieren, das Sie programmgesteuert zwischenspeichern möchten.  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#12)]  
  
2.  Instanziieren Sie das Datenobjekt. Rufen Sie anschließend die `StartCaching`\-Methode der Dokument\- bzw. Arbeitsblattinstanz auf, und übergeben Sie den Namen des Datenobjekts.  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#13)]  
  
### So beenden Sie das Zwischenspeichern eines Datenobjekts  
  
1.  Rufen Sie die `StopCaching`\-Methode der Dokument\- oder der Arbeitsblattinstanz auf, und übergeben Sie den Namen des Datenobjekts.  In diesem Beispiel wird davon ausgegangen, dass ein <xref:System.Data.DataSet> mit der Bezeichnung `dataSet1` vorliegt, dessen Zwischenspeicherung Sie beenden möchten.  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  Rufen Sie `StopCaching` nicht im Ereignishandler für das `Shutdown`\-Ereignis eines Dokuments oder eines Arbeitsblattes auf.  Sobald das `Shutdown`\-Ereignis ausgelöst wurde, kann der Datencache nicht mehr geändert werden.  Weitere Informationen zum `Shutdown`\-Ereignis finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).  
  
## Siehe auch  
 [Zwischenspeichern von Daten](../vsto/caching-data.md)   
 [Gewusst wie: Zwischenspeichern von Daten zur Offlineverwendung oder zur Verwendung auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Gewusst wie: Zwischenspeichern von Daten in einem kennwortgeschützten Dokument](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Speichern von Daten](../data-tools/saving-data.md)  
  
  