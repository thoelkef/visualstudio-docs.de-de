---
title: "Vorgehensweise: Programmgesteuertes Öffnen von Arbeitsmappen | Microsoft Docs"
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
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 11fe801cf80c15953056f4f6fdd50c5c4fadd3c9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-open-workbooks"></a>Gewusst wie: Programmgesteuertes Öffnen von Arbeitsmappen
  Die <xref:Microsoft.Office.Interop.Excel.Workbooks> -Auflistung in Microsoft Office Excel ermöglicht es mit allen geöffneten Arbeitsmappen funktionieren und die Arbeitsmappen zu öffnen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-open-an-existing-workbook"></a>Um einer vorhandenen Arbeitsmappe zu öffnen.  
  
1.  Verwenden der <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> Methode der <xref:Microsoft.Office.Interop.Excel.Workbooks> -Auflistung, in den Pfad zur Arbeitsmappe übergeben.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Für dieses Codebeispiel benötigen Sie Folgendes:  
  
-   Eine Arbeitsmappe mit dem Namen `YourWorkbook.xls` muss vorhanden sein, in einem Verzeichnis namens `Test` auf Laufwerk C.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Öffnen von Textdateien als Arbeitsmappen](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Erstellen neuer Arbeitsmappen](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Speichern von Arbeitsmappen](../vsto/how-to-programmatically-save-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Schließen von Arbeitsmappen](../vsto/how-to-programmatically-close-workbooks.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)  
  
  