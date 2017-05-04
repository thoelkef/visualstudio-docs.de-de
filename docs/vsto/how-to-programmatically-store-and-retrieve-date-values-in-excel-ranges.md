---
title: "Gewusst wie: Programmgesteuertes Speichern und Abrufen von Datumswerten in Excel-Bereichen | Microsoft Docs"
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
  - "Datumswerte"
  - "Datumswerte, Speichern in Excel-Bereichen"
  - "Datumsangaben, Abrufen aus Excel-Bereichen"
  - "Datumsangaben, Speichern in Excel-Bereichen"
  - "Excel [Office-Entwicklung in Visual Studio], Abrufen von Datumswerten aus Bereichen"
  - "Excel [Office-Entwicklung in Visual Studio], Speichern von Datumswerten in Bereichen"
  - "Bereiche, Abrufen von Datenwerten"
  - "Bereiche, Speichern von Datumswerten"
ms.assetid: e1cdd262-0356-4499-8bc5-e730f74235a2
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Gewusst wie: Programmgesteuertes Speichern und Abrufen von Datumswerten in Excel-Bereichen
  Werte können in einem <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement oder einem systemeigenen Excel\-Bereichsobjekt gespeichert oder abgerufen werden.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Wenn Sie einen Datumswert, der auf den 1.1.1900 oder ein späteres Datum fällt, mit Office\-Entwicklungstools in Visual Studio in einem Bereich speichern, wird er im OLE\-Automatisierungsformat \(OA\) gespeichert.  Sie müssen die <xref:System.DateTime.FromOADate%2A>\-Methode verwenden, um den Wert von OLE\-Automatisierungsdatumsangaben \(OA\) abzurufen.  Wenn das Datum vor dem 1.1.1900 liegt, wird es als Zeichenfolge gespeichert.  
  
> [!NOTE]  
>  Datumsangaben in Excel unterscheiden sich von Datumsangaben für die OLE\-Automatisierung bezüglich der ersten beiden Monate des Jahres 1900.  Es treten auch Unterschiede auf, wenn die Option **1904\-Datumswerte** aktiviert ist.  In den folgenden Codebeispielen werden diese Unterschiede nicht behandelt.  
  
## Verwenden eines NamedRange\-Steuerelements  
  
-   Dieses Beispiel bezieht sich auf Anpassungen auf Dokumentebene.  Der folgende Code muss in eine Arbeitsblattklasse und nicht in die `ThisWorkbook`\-Klasse eingefügt werden.  
  
#### So speichern Sie einen Datumswert in einem benannten Bereich  
  
1.  Erstellen Sie ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement in der Zelle **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#50)]  
  
2.  Legen Sie das heutige Datum als Wert für `NamedRange1` fest.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#51)]  
  
#### So rufen Sie einen Datumswert aus einem benannten Bereich ab  
  
1.  Rufen Sie den Datumswert von `NamedRange1` ab.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#52)]  
  
## Verwenden von systemeigenen Excel\-Bereichen  
  
#### So speichern Sie einen Datumswert in einem systemeigenen Excel\-Bereichsobjekt  
  
1.  Erstellen Sie einen <xref:Microsoft.Office.Interop.Excel.Range>, der die Zelle **A1** darstellt.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#25)]  
  
2.  Legen Sie das heutige Datum als Wert für `rng` fest.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#26)]  
  
#### So rufen Sie einen Datumswert aus einem systemeigenen Excel\-Bereichsobjekt ab  
  
1.  Rufen Sie den Datumswert von `rng` ab.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#27)]  
  
## Siehe auch  
 [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)   
 [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Gewusst wie: Programmgesteuertes Verweisen auf Arbeitsblattbereiche im Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Gewusst wie: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  