---
title: "Gewusst wie: Hinzuf&#252;gen von benutzerdefinierten XML-Elementen zu Dokumenten mithilfe von VSTO-Add-Ins"
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
  - "Add-Ins [Office-Entwicklung in Visual Studio], Benutzerdefinierte XML-Komponenten"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Benutzerdefinierte XML-Komponenten"
  - "Word [Office-Entwicklung in Visual Studio], Benutzerdefinierte XML-Komponenten"
  - "PowerPoint [Office-Entwicklung in Visual Studio], Benutzerdefinierte XML-Komponenten"
  - "Excel [Office-Entwicklung in Visual Studio], Benutzerdefinierte XML-Komponenten"
  - "Benutzerdefinierte XML-Komponenten [Office-Entwicklung in Visual Studio], Hinzufügen"
  - "Dokumente [Office-Entwicklung in Visual Studio], Benutzerdefinierte XML-Komponenten"
  - "Add-Ins auf Anwendungsebene [Office-Entwicklung in Visual Studio], Benutzerdefinierte XML-Komponenten"
ms.assetid: 872d2beb-193b-49f9-9a7b-dcebab91a73b
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Gewusst wie: Hinzuf&#252;gen von benutzerdefinierten XML-Elementen zu Dokumenten mithilfe von VSTO-Add-Ins
  Sie können XML\-Daten in folgenden Dokumenttypen speichern, indem Sie ein benutzerdefiniertes XML\-Element in einem VSTO\-Add\-In erstellen:  
  
-   Microsoft Office Excel\-Arbeitsmappe  
  
-   Microsoft Office Word\-Dokument  
  
-   Microsoft Office PowerPoint\-Präsentation  
  
 Weitere Informationen finden Sie unter [Übersicht über benutzerdefinierte XML-Abschnitte](../vsto/custom-xml-parts-overview.md).  
  
 **Betrifft:** Die Informationen in diesem Thema betreffen Projekte auf Anwendungsebene für Excel, PowerPoint und Word. Weitere Informationen finden Sie unter [Verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md).  
  
### So fügen Sie einer Excel\-Arbeitsmappe ein benutzerdefiniertes XML\-Element hinzu  
  
1.  Fügen Sie der <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A>\-Auflistung in der Arbeitsmappe ein neues <xref:Microsoft.Office.Core.CustomXMLPart>\-Objekt hinzu. Die XML\-Zeichenfolge, die Sie in der Arbeitsmappe speichern möchten, ist in <xref:Microsoft.Office.Core.CustomXMLPart> enthalten.  
  
     Im folgenden Codebeispiel wird einer angegebenen Arbeitsmappe ein benutzerdefiniertes XML\-Element hinzugefügt.  
  
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelAppLevel/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelAppLevel/VB/ThisAddIn.vb#1)]  
  
2.  Fügen Sie die `AddCustomXmlPartToWorkbook`\-Methode der `ThisAddIn`\-Klasse in einem VSTO\-Add\-In\-Projekt für Excel hinzu.  
  
3.  Rufen Sie die Methode aus anderem Code in Ihrem Projekt auf. Um das benutzerdefinierte XML\-Element beispielsweise zu erstellen, wenn der Benutzer eine Arbeitsmappe öffnet, rufen Sie die Methode von einem Ereignishandler für das <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen>\-Ereignis auf.  
  
### So fügen Sie einem Word\-Dokument ein benutzerdefiniertes XML\-Element hinzu  
  
1.  Fügen Sie der <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A>\-Auflistung im Dokument ein neues <xref:Microsoft.Office.Core.CustomXMLPart>\-Objekt hinzu. Die XML\-Zeichenfolge, die Sie im Dokument speichern möchten, ist in <xref:Microsoft.Office.Core.CustomXMLPart> enthalten.  
  
     Im folgenden Codebeispiel wird einem angegebenen Dokument ein benutzerdefiniertes XML\-Element hinzugefügt.  
  
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordAppLevel/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordAppLevel/VB/ThisAddIn.vb#1)]  
  
2.  Fügen Sie die `AddCustomXmlPartToDocument`\-Methode der `ThisAddIn`\-Klasse in einem VSTO\-Add\-In\-Projekt für Word hinzu.  
  
3.  Rufen Sie die Methode aus anderem Code in Ihrem Projekt auf. Um das benutzerdefinierte XML\-Element beispielsweise zu erstellen, wenn der Benutzer ein Dokument öffnet, rufen Sie die Methode von einem Ereignishandler für das <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>\-Ereignis auf.  
  
### So fügen Sie einer PowerPoint\-Präsentation ein benutzerdefiniertes XML\-Element hinzu  
  
1.  Fügen Sie der <xref:Microsoft.Office.Interop.PowerPoint._Presentation.CustomXMLParts%2A>\-Auflistung in der Präsentation ein neues <xref:Microsoft.Office.Core.CustomXMLPart>\-Objekt hinzu. Die XML\-Zeichenfolge, die Sie in der Präsentation speichern möchten, ist in <xref:Microsoft.Office.Core.CustomXMLPart> enthalten.  
  
     Im folgenden Codebeispiel wird einer angegebenen Präsentation ein benutzerdefiniertes XML\-Element hinzugefügt.  
  
     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartPowerPointAppLevel/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartPowerPointAppLevel/VB/ThisAddIn.vb#1)]  
  
2.  Fügen Sie die `AddCustomXmlPartToPresentation`\-Methode der `ThisAddIn`\-Klasse in einem VSTO\-Add\-In\-Projekt für PowerPoint hinzu.  
  
3.  Rufen Sie die Methode aus anderem Code in Ihrem Projekt auf. Um das benutzerdefinierte XML\-Element beispielsweise zu erstellen, wenn der Benutzer eine Präsentation öffnet, rufen Sie die Methode von einem Ereignishandler für das <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen>\-Ereignis auf.  
  
## Robuste Programmierung  
 Zur Vereinfachung verwendet dieses Beispiel eine XML\-Zeichenfolge, die als lokale Variable in der Methode definiert ist. In der Regel sollten Sie den XML\-Code aus einer externen Quelle, z. B. einer Datei oder Datenbank, abrufen.  
  
## Siehe auch  
 [Übersicht über benutzerdefinierte XML-Abschnitte](../vsto/custom-xml-parts-overview.md)   
 [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Abschnitten zu Anpassungen auf Dokumentebene](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
  