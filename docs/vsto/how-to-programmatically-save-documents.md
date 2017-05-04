---
title: "Gewusst wie: Programmgesteuertes Speichern von Dokumenten | Microsoft Docs"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Speichern"
  - "Word [Office-Entwicklung in Visual Studio], Speichern von Dokumenten"
ms.assetid: a6225ae9-94f5-421a-9860-5299002d543d
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Gewusst wie: Programmgesteuertes Speichern von Dokumenten
  Es gibt mehrere Möglichkeiten, Microsoft Office Word\-Dokumente zu speichern.  Sie können ein Dokument speichern, ohne seinen Namen zu ändern, oder Sie können ein Dokument unter einem neuen Namen speichern.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Speichern eines Dokuments, ohne den Namen zu ändern  
  
#### So speichern Sie das einer Anpassung auf Dokumentebene zugeordnete Dokument  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Word.Document.Save%2A>\-Methode der <xref:Microsoft.Office.Tools.Word.Document>\-Klasse auf.  Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreWordAutomation#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#7)]  
  
#### So speichern Sie das aktive Dokument  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Word._Document.Save%2A>\-Methode für das aktive Dokument auf.  Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument`\-Klasse oder der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#8)]
     [!code-vb[Trin_VstcoreWordAutomation#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#8)]  
  
 Wenn Sie sich nicht sicher sind, ob es sich bei dem zu speichernden Dokument um das aktive Dokument handelt, können Sie auf dieses Dokument mit seinem Namen verweisen.  
  
#### So speichern Sie ein mit seinem Namen angegebenes Dokument  
  
1.  Verwenden Sie den Dokumentnamen als Argument für die <xref:Microsoft.Office.Interop.Word.Documents>\-Auflistung.  Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument`\-Klasse oder der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#9)]
     [!code-vb[Trin_VstcoreWordAutomation#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#9)]  
  
## Speichern eines Dokuments unter einem neuen Namen  
 Verwenden Sie die SaveAs\-Methode, um ein Dokument unter einem neuen Namen zu speichern.  Sie können diese Methode vom <xref:Microsoft.Office.Tools.Word.Document>\-Hostelement in einem Word\-Projekt auf Dokumentebene oder von einem systemeigenen <xref:Microsoft.Office.Interop.Word.Document>\-Objekt in einem beliebigen Word\-Projekt verwenden.  Bei dieser Methode müssen Sie den neuen Dateinamen angeben. Die weiteren Argumente sind jedoch optional.  
  
> [!NOTE]  
>  Wenn Sie das Dialogfeld **SaveAs** im <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>\-Ereignishandler von `ThisDocument` anzeigen und den *Cancel*\-Parameter auf **false** festlegen, könnte die Anwendung unerwartet beendet werden.  Wenn Sie den *Cancel*\-Parameter auf **true** festlegen, wird in einer Fehlermeldung mitgeteilt, dass die automatische Speicherung deaktiviert wurde.  
  
#### So speichern Sie das einer Anpassung auf Dokumentebene zugeordnete Dokument unter einem neuen Namen  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A>\-Methode der `ThisDocument`\-Klasse im Projekt auf, und verwenden Sie dabei einen vollqualifizierten Pfad und Dateinamen.  Wenn in diesem Ordner bereits eine Datei mit dem angegebenen Namen vorhanden ist, wird diese ohne Rückmeldung überschrieben.  Um dieses Codebeispiel verwenden zu können, müssen Sie es in der `ThisDocument`\-Klasse ausführen.  
  
    > [!NOTE]  
    >  Wenn das Zielverzeichnis nicht vorhanden ist oder beim Speichern einer Datei andere Probleme auftreten, löst die <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A>\-Methode eine Ausnahme aus.  Es empfiehlt sich daher, die <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A>\-Methode mit einem **try…catch**\-Block zu umgeben oder einen solchen Block innerhalb der aufrufenden Methode zu verwenden.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreWordAutomation#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#10)]  
  
#### So speichern Sie ein systemeigenes Dokument unter einem neuen Namen  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>\-Methode für das <xref:Microsoft.Office.Interop.Word.Document>\-Dokument auf, das Sie speichern möchten, und verwenden Sie dabei einen vollqualifizierten Pfad und Dateinamen.  Wenn in diesem Ordner bereits eine Datei mit dem angegebenen Namen vorhanden ist, wird diese ohne Rückmeldung überschrieben.  
  
     Im folgenden Codebeispiel wird das aktive Dokument unter einem neuen Namen gespeichert.  Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument`\-Klasse oder der `ThisAddIn`\-Klasse im Projekt aus.  
  
    > [!NOTE]  
    >  Wenn das Zielverzeichnis nicht vorhanden ist oder beim Speichern einer Datei andere Probleme auftreten, löst die <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>\-Methode eine Ausnahme aus.  Es empfiehlt sich daher, die <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>\-Methode mit einem **try…catch**\-Block zu umgeben oder einen solchen Block innerhalb der aufrufenden Methode zu verwenden.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#10)]  
  
## Kompilieren des Codes  
 Für dieses Codebeispiel benötigen Sie Folgendes:  
  
-   Um ein Dokument unter einem Namen zu speichern, muss auf Laufwerk C in einem Verzeichnis mit dem Namen "Test" ein Dokument mit dem Namen "NewDocument.doc" vorhanden sein.  
  
-   Um das Dokument unter einem neuen Namen zu speichern, muss auf Laufwerk C: ein Verzeichnis mit dem Namen "Test" vorhanden sein.  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Schließen von Dokumenten](../vsto/how-to-programmatically-close-documents.md)   
 [Gewusst wie: Programmgesteuertes Öffnen vorhandener Dokumente](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Dokumenthostelement](../vsto/document-host-item.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  