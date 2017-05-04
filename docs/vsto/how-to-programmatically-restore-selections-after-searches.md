---
title: "Gewusst wie: Programmgesteuertes Wiederherstellen der Auswahl nach Suchvorg&#228;ngen | Microsoft Docs"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Wiederherstellen der Auswahl"
  - "Suchvorgänge, Wiederherstellen der Auswahl nach"
  - "Auswahl, Wiederherstellen nach einer Suche"
ms.assetid: 1e6131ad-0e5b-4189-be67-5b2ed87d193d
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Gewusst wie: Programmgesteuertes Wiederherstellen der Auswahl nach Suchvorg&#228;ngen
  Wenn Sie in einem Dokument nach Text suchen und diesen ersetzen, empfiehlt es sich, nach Abschluss des Vorgangs die ursprünglich vom Benutzer vorgenommene Markierung wiederherzustellen.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Im Code der Beispielprozedur werden zwei <xref:Microsoft.Office.Interop.Word.Range>\-Objekte verwendet.  Das eine speichert die aktuelle <xref:Microsoft.Office.Interop.Word.Selection>, und das andere legt das gesamte Dokument als Suchbereich fest.  
  
### So stellen Sie die ursprüngliche Markierung des Benutzers nach einem Suchvorgang wieder her  
  
1.  Erstellen Sie die <xref:Microsoft.Office.Interop.Word.Range>\-Objekte für das Dokument und die aktuelle Auswahl.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#83](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#83)]
     [!code-vb[Trin_VstcoreWordAutomation#83](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#83)]  
  
2.  Führen Sie den Such\- und Ersetzungsvorgang aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#84](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#84)]
     [!code-vb[Trin_VstcoreWordAutomation#84](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#84)]  
  
3.  Wählen Sie den Anfangsbereich aus, um die ursprüngliche Auswahl des Benutzers wiederherzustellen.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#85](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#85)]
     [!code-vb[Trin_VstcoreWordAutomation#85](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#85)]  
  
 Im folgenden Beispiel wird die vollständige Methode veranschaulicht.  
  
## Beispiel  
 [!code-csharp[Trin_VstcoreWordAutomation#82](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#82)]
 [!code-vb[Trin_VstcoreWordAutomation#82](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#82)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Suchen und Ersetzen von Text in Dokumenten](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Festlegen von Suchoptionen in Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Gewusst wie: Programmgesteuertes Durchlaufen gefundener Elemente in Dokumenten](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  