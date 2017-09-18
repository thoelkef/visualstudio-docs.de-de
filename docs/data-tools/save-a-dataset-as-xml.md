---
title: "Gewusst wie: Speichern eines Datasets als XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "Daten [Visual Studio], Speichern als XML"
  - "Datasets [Visual Basic], Speichern als XML"
  - "Speichern von Daten"
  - "XML [Visual Basic], Datasets"
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Speichern eines Datasets als XML
Sie können auf die XML\-Daten in einem Dataset zugreifen, indem Sie die für das Dataset verfügbaren XML\-Methoden aufrufen.  Um die Daten in XML\-Format zu speichern, können Sie entweder die <xref:System.Data.DataSet.GetXml%2A>\-Methode oder die <xref:System.Data.DataSet.WriteXml%2A>\-Methode eines <xref:System.Data.DataSet> aufrufen.  
  
 Durch Aufrufen der <xref:System.Data.DataSet.GetXml%2A>\-Methode wird eine Zeichenfolge zurückgegeben, die die Daten aus allen Datentabellen im Dataset enthält, die als XML formatiert sind.  
  
 Durch Aufrufen der <xref:System.Data.DataSet.WriteXml%2A>\-Methode werden die XML\-formatierten Daten an eine von Ihnen angegebene Datei gesendet.  
  
### So speichern Sie die Daten in einem Dataset als XML in einer Variablen  
  
-   Die <xref:System.Data.DataSet.GetXml%2A>\-Methode gibt einen <xref:System.String> zurück, sodass Sie eine Variable vom Typ <xref:System.String> deklarieren und ihr das Ergebnis der <xref:System.Data.DataSet.GetXml%2A>\-Methode zuweisen müssen.  
  
     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-cs[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]  
  
### So speichern Sie die Daten in einem Dataset als XML in einer Datei  
  
-   Die <xref:System.Data.DataSet.WriteXml%2A>\-Methode verfügt über mehrere Überladungen.  Der folgende Code zeigt, wie die Daten in einer Datei gespeichert werden. Deklarieren Sie also eine Variable, und weisen Sie ihr einen gültigen Pfad zum Speichern der Datei zu.  
  
     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-cs[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]  
  
## Siehe auch  
 [DataSets, DataTables und DataViews](../Topic/DataSets,%20DataTables,%20and%20DataViews.md)   
 [XML\-Tools in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)