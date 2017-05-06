---
title: "Gewusst wie: Hinzuf&#252;gen von benutzerdefinierten XML-Abschnitten zu Anpassungen auf Dokumentebene"
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
  - "Anpassungen auf Dokumentebene [Office-Entwicklung in Visual Studio], Benutzerdefinierte XML-Komponenten"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Benutzerdefinierte XML-Komponenten"
  - "Word [Office-Entwicklung in Visual Studio], Benutzerdefinierte XML-Komponenten"
  - "Excel [Office-Entwicklung in Visual Studio], Benutzerdefinierte XML-Komponenten"
  - "Benutzerdefinierte XML-Komponenten [Office-Entwicklung in Visual Studio], Hinzufügen"
  - "Dokumente [Office-Entwicklung in Visual Studio], Benutzerdefinierte XML-Komponenten"
ms.assetid: e305a3d6-3a0e-4e72-ab8c-6a87a3590068
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Gewusst wie: Hinzuf&#252;gen von benutzerdefinierten XML-Abschnitten zu Anpassungen auf Dokumentebene
  Sie können XML\-Daten in einer Microsoft Office Excel\-Arbeitsmappe oder in einem Microsoft Office Word\-Dokument speichern, indem Sie einen benutzerdefinierten XML\-Abschnitt in einer Anpassung auf Dokumentebene erstellen. Weitere Informationen finden Sie unter [Übersicht über benutzerdefinierte XML-Abschnitte](../vsto/custom-xml-parts-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Visual Studio stellt keine Projekte auf Dokumentebene für Microsoft Office PowerPoint bereit. Informationen zum Hinzufügen eines benutzerdefinierten XML\-Abschnitt zu einer PowerPoint\-Präsentation mit VSTO\-Add\-In finden Sie unter [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Elementen zu Dokumenten mithilfe von VSTO-Add-Ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).  
  
### So fügen Sie einer Excel\-Arbeitsmappe ein benutzerdefiniertes XML\-Element hinzu  
  
1.  Fügen Sie der <xref:Microsoft.Office.Core.CustomXMLParts>\-Auflistung in der Arbeitsmappe ein neues <xref:Microsoft.Office.Core.CustomXMLPart>\-Objekt hinzu. Die XML\-Zeichenfolge, die Sie in der Arbeitsmappe speichern möchten, ist in <xref:Microsoft.Office.Core.CustomXMLPart> enthalten.  
  
     [!code-csharp[Trin_AddCustomXmlPartExcelDocLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelDocLevel/CS/ThisWorkbook.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelDocLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelDocLevel/VB/ThisWorkbook.vb#1)]  
  
2.  Fügen Sie die `AddCustomXmlPartToWorkbook`\-Methode der `ThisWorkbook`\-Klasse in einem Projekt auf Dokumentebene für Excel hinzu.  
  
3.  Rufen Sie die Methode aus anderem Code in Ihrem Projekt auf. Um z. B. das benutzerdefinierte XML\-Element zu erstellen, wenn der Benutzer eine Arbeitsmappe öffnet, rufen Sie die Methode über den `ThisWorkbook_Startup`\-Ereignishandler auf.  
  
### So fügen Sie einem Word\-Dokument ein benutzerdefiniertes XML\-Element hinzu  
  
1.  Fügen Sie der <xref:Microsoft.Office.Core.CustomXMLParts>\-Auflistung im Dokument ein neues <xref:Microsoft.Office.Core.CustomXMLPart>\-Objekt hinzu. Die XML\-Zeichenfolge, die Sie im Dokument speichern möchten, ist in <xref:Microsoft.Office.Core.CustomXMLPart> enthalten.  
  
     [!code-csharp[Trin_AddCustomXmlPartWordDocLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordDocLevel/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartWordDocLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordDocLevel/VB/ThisDocument.vb#1)]  
  
2.  Fügen Sie die `AddCustomXmlPartToDocument`\-Methode der `ThisDocument`\-Klasse in einem Projekt auf Dokumentebene für Word hinzu.  
  
3.  Rufen Sie die Methode aus anderem Code in Ihrem Projekt auf. Um z. B. das benutzerdefinierte XML\-Element zu erstellen, wenn der Benutzer ein Dokument öffnet, rufen Sie die Methode über den `ThisDocument_Startup`\-Ereignishandler auf.  
  
## Robuste Programmierung  
 Zur Vereinfachung verwendet dieses Beispiel eine XML\-Zeichenfolge, die als lokale Variable in der Methode definiert ist. In der Regel sollten Sie den XML\-Code aus einer externen Quelle, z. B. einer Datei oder Datenbank, abrufen.  
  
## Siehe auch  
 [Übersicht über benutzerdefinierte XML-Abschnitte](../vsto/custom-xml-parts-overview.md)   
 [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Elementen zu Dokumenten mithilfe von VSTO-Add-Ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
  