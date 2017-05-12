---
title: "Gewusst wie: Programmgesteuertes &#214;ffnen vorhandener Dokumente"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Öffnen"
  - "Word [Office-Entwicklung in Visual Studio], Öffnen von Dokumenten"
ms.assetid: 08f7fe4b-d96d-4a0c-b32a-aa7fd7992316
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Gewusst wie: Programmgesteuertes &#214;ffnen vorhandener Dokumente
  Die <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>\-Methode öffnet ein vorhandenes Microsoft Office Word\-Dokument, das durch einen vollqualifizierten Pfad und Dateinamen angegeben ist.  Diese Methode gibt ein <xref:Microsoft.Office.Interop.Word.Document> zurück, das das geöffnete Dokument darstellt.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### So öffnen Sie ein Dokument  
  
-   Rufen Sie die <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>\-Methode der <xref:Microsoft.Office.Interop.Word.Documents>\-Auflistung auf, und geben Sie einen Pfad zum Dokument an.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_VstcoreWordAutomation#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#5)]  
  
### So öffnen Sie ein Dokument mit Schreibschutz  
  
-   Rufen Sie die <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>\-Methode auf, geben Sie einen Pfad zum Dokument an, und legen Sie das *ReadOnly*\-Argument im Methodenaufruf auf **True** fest.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreWordAutomation#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#6)]  
  
## Kompilieren des Codes  
 Für dieses Codebeispiel benötigen Sie Folgendes:  
  
-   Ein Dokument mit dem Namen "NewDocument.doc" muss in einem Verzeichnis mit dem Namen "Test" auf Laufwerk C vorhanden sein.  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Erstellen neuer Dokumente](../vsto/how-to-programmatically-create-new-documents.md)   
 [Gewusst wie: Programmgesteuertes Schließen von Dokumenten](../vsto/how-to-programmatically-close-documents.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  