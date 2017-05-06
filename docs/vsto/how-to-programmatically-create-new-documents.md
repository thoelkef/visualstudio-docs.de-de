---
title: "Gewusst wie: Programmgesteuertes Erstellen neuer Dokumente"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Erstellen"
  - "Vorlagen [Office-Entwicklung in Visual Studio], Benutzerdefiniertes Dokument"
  - "Word [Office-Entwicklung in Visual Studio], Erstellen von Dokumenten"
ms.assetid: c24bb8a3-1303-438e-9b33-ba8b00b29c3b
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Gewusst wie: Programmgesteuertes Erstellen neuer Dokumente
  Wenn Sie ein Dokument programmgesteuert erstellen, ist das neue Dokument ein systemeigenes <xref:Microsoft.Office.Interop.Word.Document>\-Objekt.  Dieses Objekt verfügt nicht über die zusätzlichen Ereignisse und Datenbindungsfunktionen eines <xref:Microsoft.Office.Tools.Word.Document>\-Hostelements.  Weitere Informationen finden Sie unter [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Wenn Sie ein Projekt auf Dokumentebene entwickeln, können Sie Ihrem Projekt nicht programmgesteuert <xref:Microsoft.Office.Tools.Word.Document>\-Hostelemente hinzufügen.  In einem VSTO\-Add\-In\-Projekt Sie beliebige <xref:Microsoft.Office.Interop.Word.Document>\-Objekte zur Laufzeit in <xref:Microsoft.Office.Tools.Word.Document>\-Hostelements konvertieren.  Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### So erstellen Sie ein neues Dokument basierend auf der Vorlage "NORMAL.DOT"  
  
-   Verwenden Sie die Methode <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> der Auflistung <xref:Microsoft.Office.Interop.Word.Documents> zum Erstellen eines neuen Dokuments auf der Grundlage der Vorlage "NORMAL.DOT".  Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` oder `ThisAddIn` in Ihrem Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreWordAutomation#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#1)]  
  
## Verwenden von benutzerdefinierten Vorlagen  
 Die Methode <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> besitzt ein optionales Argument *Template* zum Erstellen eines neuen Dokuments auf der Grundlage einer anderen Vorlage als der Vorlage "NORMAL.DOT".  Sie müssen den Dateinamen und den vollqualifizierten Pfad der Vorlage angeben.  
  
#### So erstellen Sie ein neues Dokument basierend auf einer benutzerdefinierten Vorlage  
  
-   Rufen Sie die Methode <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> der Auflistung <xref:Microsoft.Office.Interop.Word.Documents> auf, und geben Sie den Pfad zur Vorlage an.  Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` oder `ThisAddIn` in Ihrem Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreWordAutomation#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#2)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Öffnen vorhandener Dokumente](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  