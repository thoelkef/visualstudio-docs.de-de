---
title: "Gewusst wie: Programmgesteuertes Anzeigen einer Zeichenfolge in einer Arbeitsblattzelle | Microsoft Docs"
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
  - "Text [Office-Entwicklung in Visual Studio], Hinzufügen zu Arbeitsblättern"
  - "Arbeitsblätter, Anzeigen von Text in Zellen"
ms.assetid: b19870ad-e132-49fd-994e-0a91710fa4c9
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Gewusst wie: Programmgesteuertes Anzeigen einer Zeichenfolge in einer Arbeitsblattzelle
  Dieses Beispiel veranschaulicht das programmgesteuerte Anzeigen von Text in einer Zelle.  Um in einer Zelle Text anzuzeigen, verwenden Sie entweder ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement oder ein systemeigenes Excel\-Bereichsobjekt.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Verwenden eines NamedRange\-Steuerelements  
 In diesem Beispiel wird ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement mit der Bezeichnung `message` verwendet.  Das Steuerelement muss einer Anpassung auf Dokumentebene zur Entwurfszeit hinzugefügt werden.  Der folgende Code muss in eine Arbeitsblattklasse und nicht in die `ThisWorkbook`\-Klasse eingefügt werden.  
  
#### So zeigen Sie Text in einem NamedRange\-Steuerelement an  
  
1.  Legen Sie den Wert des <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelements auf **Hello World** fest.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#68)]  
  
## Verwenden eines systemeigenen Excel\-Bereichs  
 Im folgenden Code wird ein neuer Bereich programmgesteuert erstellt, und anschließend wird diesem ein Wert zugewiesen.  
  
#### So zeigen Sie Text in einem Excel\-Bereich an  
  
1.  Rufen Sie den Bereich in Zelle **A1** auf `Sheet1` ab, und legen Sie den Wert auf **Hello World** fest.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#69)]  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Erfassen von Daten mit einem Windows Form](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Problembehandlung für Office-Lösungen](../vsto/troubleshooting-office-solutions.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  