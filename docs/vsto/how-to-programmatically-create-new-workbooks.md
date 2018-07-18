---
title: 'Gewusst wie: Programmgesteuertes Erstellen neuer Arbeitsmappen'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7e1da9ff331a4376a6ff242dca4382832ee4e85f
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257107"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Gewusst wie: Programmgesteuertes Erstellen neuer Arbeitsmappen
  Wenn Sie eine Arbeitsmappe programmgesteuert erstellen, ist diese ein systemeigenes <xref:Microsoft.Office.Interop.Excel.Workbook>-Objekt und kein <xref:Microsoft.Office.Tools.Excel.Workbook>-Hostelement.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Sie können ein <xref:Microsoft.Office.Tools.Excel.Workbook>-Hostelement für ein <xref:Microsoft.Office.Interop.Excel.Workbook>-Objekt im VSTO-Add-In-Projekt generieren. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="to-create-a-new-workbook"></a>So erstellen Sie eine neue Arbeitsmappe  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>-Methode der <xref:Microsoft.Office.Interop.Excel.Workbooks>-Auflistung.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#1)]  
  
    > [!NOTE]  
    >  Sie können eine Arbeitsmappe auf der Grundlage einer anderen Vorlage als der Standardvorlage erstellen: Übergeben Sie die Vorlage, die Sie verwenden möchten, als Parameter an die Methode <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Öffnen von Arbeitsmappen](../vsto/how-to-programmatically-open-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Speichern von Arbeitsmappen](../vsto/how-to-programmatically-save-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Schließen von Arbeitsmappen](../vsto/how-to-programmatically-close-workbooks.md)   
 [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)   
 [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)  
  
  