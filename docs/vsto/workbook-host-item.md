---
title: Arbeitsmappenhostelement | Microsoft Docs
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
- Excel workbooks
- Workbook host items
- host items [Office development in Visual Studio], Workbook
- workbooks, Excel
- Workbook host items, events
- workbooks
- Excel [Office development in Visual Studio], workbooks
- workbooks, events
- events [Office development in Visual Studio]
ms.assetid: 54489d91-a799-4dc2-89b8-498cf17c2f57
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: baeb44b4804f74aad4b2850eb0bbd4ad539b33e1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="workbook-host-item"></a>Arbeitsmappenhostelement
  Das <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelement ist ein Typ, der den <xref:Microsoft.Office.Interop.Excel.Workbook> -Typ aus der primären Interopassembly für Excel erweitert. Das <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelement stellt die gleichen Eigenschaften, Methoden und Ereignisse wie ein <xref:Microsoft.Office.Interop.Excel.Workbook> -Objekt bereit, bietet jedoch auch zusätzliche Funktionen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 In Projekten auf Dokumentebene gibt es ein <xref:Microsoft.Office.Tools.Excel.Workbook> -Standardhostelement, das die Arbeitsmappe im Projekt darstellt. In VSTO-Add-In-Projekten können Sie <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelemente zur Laufzeit generieren.  
  
## <a name="understanding-the-workbook-host-item-in-document-level-projects"></a>Grundlegendes zum Arbeitsmappen-Hostelement in Projekten auf Dokumentebene  
 Verwenden Sie die `ThisWorkbook` -Klasse, um auf die Arbeitsmappe im Projekt zuzugreifen. Über die `ThisWorkbook` -Klasse erhalten Sie Zugriff auf Member des <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelements, um grundlegende Aufgaben in der Anpassung auszuführen, z. B. das Ausführen von Code, wenn die Arbeitsmappe geöffnet bzw. geschlossen wird. Weitere Informationen finden Sie unter [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
 Die `ThisWorkbook` -Klasse stellt einen Ausgangspunkt bereit, an dem Sie mit dem Schreiben von Code im Projekt beginnen können. Da die Klasse die gleichen Eigenschaften, Methoden und Ereignisse wie das <xref:Microsoft.Office.Interop.Excel.Workbook> -Objekt in der primären Interopassembly für Excel bereitstellt, können Sie auch mit `ThisWorkbook` auf das Excel-Objektmodell zugreifen. Weitere Informationen finden Sie unter [Excel Object Model Overview](../vsto/excel-object-model-overview.md).  
  
 Doppelklicken Sie im **Projektmappen-Explorer** auf das **ThisWorkbook** -Projektelement, um den Arbeitsmappen-Designer und die Eigenschaften und Ereignisse der Arbeitsmappe im Fenster **Eigenschaften** anzuzeigen.  
  
### <a name="limitations-of-the-workbook-host-item-in-document-level-projects"></a>Einschränkungen des Arbeitsmappen-Hostelements in Projekten auf Dokumentebene  
 Ein Projekt auf Dokumentebene kann nur ein <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelement (die `ThisWorkbook` -Klasse) enthalten. Sie können dem Projekt zur Entwurfszeit keine neuen <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelemente hinzufügen, und Sie können zur Laufzeit von einer Anpassung auf Dokumentebene keine neuen <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelemente erstellen.  
  
 Wenn Sie zur Laufzeit eine neue Excel-Arbeitsmappe erstellen, hat sie den Typ <xref:Microsoft.Office.Interop.Excel.Workbook>. Da es kein Hostelement ist, kann es keine Hoststeuerelemente bzw. Windows Forms-Steuerelemente enthalten. Weitere Informationen zum Erstellen von Arbeitsmappen zur Laufzeit finden Sie unter [wie: Programmgesteuertes Erstellen neuer Arbeitsmappen](../vsto/how-to-programmatically-create-new-workbooks.md).  
  
 Das <xref:Microsoft.Office.Tools.Excel.Workbook> Hostelement dient nicht als Container für Hoststeuerelemente. Daher können Sie der Arbeitsmappe keine sichtbaren Steuerelemente hinzufügen. Sie können jedoch Komponenten wie <xref:System.Data.DataSet>hinzufügen, sodass die Komponenten von allen Arbeitsblättern gemeinsam genutzt werden können. In einem Projekt auf Dokumentebene befinden sich die für die Arbeitsmappe verfügbare Komponenten auf den Registerkarten **Komponente** , **Daten** und **Alle Windows Forms** der **Toolbox**.  
  
> [!NOTE]  
>  Die Office-Entwicklungstools in Visual Studio unterstützen keine freigegebenen Arbeitsmappen.  
  
## <a name="understanding-workbook-host-items-in-vsto-add-in-projects"></a>Grundlegendes zu Arbeitsmappen-Hostelementen in VSTO-Add-In-Projekten  
 In VSTO-Add-In-Projekten können Sie für jede Arbeitsmappe, die in Excel geöffnet ist, zur Laufzeit ein <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelement generieren. Zum Generieren einer <xref:Microsoft.Office.Tools.Excel.Workbook> Hostelement, verwenden Sie die GetVstoObject-Methode. Weitere Informationen finden Sie unter [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)   
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Arbeitsblatt-Hostelements](../vsto/worksheet-host-item.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  