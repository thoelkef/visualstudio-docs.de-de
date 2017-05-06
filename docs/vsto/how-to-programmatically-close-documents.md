---
title: "Gewusst wie: Programmgesteuertes Schlie&#223;en von Dokumenten"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Schließen"
  - "Word [Office-Entwicklung in Visual Studio], Schließen von Dokumenten"
ms.assetid: d5bee1dc-63d1-4307-828f-b7b077e20fb9
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Gewusst wie: Programmgesteuertes Schlie&#223;en von Dokumenten
  Sie können das aktive Dokument schließen, oder Sie können ein Dokument angeben, das geschlossen werden soll.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Schließen des aktiven Dokuments  
 Es gibt zwei Verfahren für das Schließen des aktiven Dokuments: eines für Anpassungen auf Dokumentebene und eines für VSTO\-Add\-Ins.  
  
#### So schließen Sie das aktive Dokument in einer Anpassung auf Dokumentebene  
  
1.  Rufen Sie die Methode <xref:Microsoft.Office.Tools.Word.Document.Close%2A> der Klasse `ThisDocument` in Ihrem Projekt auf, um das der Anpassung zugeordnete Dokument zu schließen. Wenn Sie das folgende Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` aus.  
  
    > [!NOTE]  
    >  In diesem Beispiel wird der <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges>\-Wert an den Parameter *SaveChanges* übergeben, um das Dokument ohne Speichern von Änderungen oder Anzeigen einer Benutzeraufforderung zu schließen.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreWordAutomation#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#3)]  
  
#### So schließen Sie das aktive Dokument in einem VSTO\-Add\-In  
  
1.  Rufen Sie die Methode <xref:Microsoft.Office.Interop.Word._Document.Close%2A> der\-Eigenschaft <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> auf, um das aktive Dokument zu schließen. Wenn Sie das folgende Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisAddIn` in Ihrem Projekt aus.  
  
    > [!NOTE]  
    >  In diesem Beispiel wird der <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges>\-Wert an den Parameter *SaveChanges* übergeben, um das Dokument ohne Speichern von Änderungen oder Anzeigen einer Benutzeraufforderung zu schließen.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## Schließen eines namentlich angegebenen Dokuments  
 Das Schließen eines namentlich angegebenen Dokuments erfolgt bei VSTO\-Add\-Ins und Anpassungen auf Dokumentebene auf die gleiche Weise.  
  
#### So schließen Sie ein namentlich angegebenes Dokument  
  
1.  Geben Sie den Namen des Dokuments als Argument für die Auflistung <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> an, und rufen Sie dann die Methode <xref:Microsoft.Office.Interop.Word._Document.Close%2A> auf. Im folgenden Codebeispiel wird davon ausgegangen, dass ein Dokument namens **NewDocument** in Word geöffnet ist.  
  
    > [!NOTE]  
    >  In diesem Beispiel wird der <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges>\-Wert an den Parameter *SaveChanges* übergeben, um das Dokument ohne Speichern von Änderungen oder Anzeigen einer Benutzeraufforderung zu schließen.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_VstcoreWordAutomation#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#4)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Öffnen vorhandener Dokumente](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Gewusst wie: Programmgesteuertes Speichern von Dokumenten](../vsto/how-to-programmatically-save-documents.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  