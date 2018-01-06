---
title: 'Vorgehensweise: Programmgesteuertes Anzeigen einer Zeichenfolge in einer Arbeitsblattzelle | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
ms.assetid: b19870ad-e132-49fd-994e-0a91710fa4c9
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0b86e3d8b613a576131d47b90f4f0fae1ca89c22
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Gewusst wie: Programmgesteuertes Anzeigen einer Zeichenfolge in einer Arbeitsblattzelle
  In diesem Beispiel wird veranschaulicht, wie Text programmgesteuert in einer Zelle angezeigt. Um Text in die Zelle anzuzeigen, verwenden Sie entweder eine <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement oder ein systemeigenes Excel-Range-Objekt.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>Verwenden ein NamedRange-Steuerelement  
 Dieses Beispiel verwendet eine <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement namens `message`. Das Steuerelement muss einer Anpassung auf Dokumentebene zur Entwurfszeit hinzugefügt werden. Der folgende Code muss in einer Sheet-Klasse platziert werden, nicht in der `ThisWorkbook` Klasse.  
  
#### <a name="to-display-text-in-a-namedrange-control"></a>Zum Anzeigen von Text in einem NamedRange-Steuerelement  
  
1.  Legen Sie den Wert, der die <xref:Microsoft.Office.Tools.Excel.NamedRange> die Steuerung an **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]  
  
## <a name="using-a-native-excel-range"></a>Verwenden ein systemeigenes Excel-Bereich  
 Der folgende Code wird einen neuen Bereich programmgesteuert erstellt, und klicken Sie dann ein Wert zugewiesen.  
  
#### <a name="to-display-text-in-an-excel-range"></a>Zum Anzeigen von Text in einem Excel-Bereich  
  
1.  Rufen Sie den Bereich in Zelle **A1** auf `Sheet1` und legen Sie den Wert auf **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erfassen von Daten mit einem Windows Form](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Problembehandlung bei Office-Projektmappen](../vsto/troubleshooting-office-solutions.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  