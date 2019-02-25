---
title: Arbeitsmappenhostelement
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b8ffe18ea3407480faa69a6b9b3ba4309b28b279
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625258"
---
# <a name="workbook-host-item"></a>Arbeitsmappenhostelement
  Das <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelement ist ein Typ, der den <xref:Microsoft.Office.Interop.Excel.Workbook> -Typ aus der primären Interopassembly für Excel erweitert. Das <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelement stellt die gleichen Eigenschaften, Methoden und Ereignisse wie ein <xref:Microsoft.Office.Interop.Excel.Workbook> -Objekt bereit, bietet jedoch auch zusätzliche Funktionen.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 In Projekten auf Dokumentebene gibt es ein <xref:Microsoft.Office.Tools.Excel.Workbook> -Standardhostelement, das die Arbeitsmappe im Projekt darstellt. Sie können in VSTO-Add-in-Projekte generieren <xref:Microsoft.Office.Tools.Excel.Workbook> Hostelemente zur Laufzeit.

## <a name="understand-the-workbook-host-item-in-document-level-projects"></a>Verstehen Sie Arbeitsmappen-Hostelement in Projekten auf Dokumentebene
 Verwenden Sie die `ThisWorkbook` -Klasse, um auf die Arbeitsmappe im Projekt zuzugreifen. Über die `ThisWorkbook` -Klasse erhalten Sie Zugriff auf Member des <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelements, um grundlegende Aufgaben in der Anpassung auszuführen, z. B. das Ausführen von Code, wenn die Arbeitsmappe geöffnet bzw. geschlossen wird. Weitere Informationen finden Sie unter [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md).

 Die `ThisWorkbook` -Klasse stellt einen Ausgangspunkt bereit, an dem Sie mit dem Schreiben von Code im Projekt beginnen können. Da die Klasse die gleichen Eigenschaften, Methoden und Ereignisse wie das <xref:Microsoft.Office.Interop.Excel.Workbook> -Objekt in der primären Interopassembly für Excel bereitstellt, können Sie auch mit `ThisWorkbook` auf das Excel-Objektmodell zugreifen. Weitere Informationen finden Sie unter [Übersicht über Excel-Objektmodell](../vsto/excel-object-model-overview.md).

 Doppelklicken Sie im **Projektmappen-Explorer** auf das **ThisWorkbook** -Projektelement, um den Arbeitsmappen-Designer und die Eigenschaften und Ereignisse der Arbeitsmappe im Fenster **Eigenschaften** anzuzeigen.

### <a name="limitations-of-the-workbook-host-item-in-document-level-projects"></a>Einschränkungen des Arbeitsmappen-Hostelement in Projekten auf Dokumentebene
 Ein Projekt auf Dokumentebene kann nur ein <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelement (die `ThisWorkbook` -Klasse) enthalten. Sie können keine neuen hinzufügen <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelemente zur Entwurfszeit zu Ihrem Projekt, und Sie können nicht neu erstellen <xref:Microsoft.Office.Tools.Excel.Workbook> Hostelemente zur Laufzeit von einer Anpassung auf Dokumentebene.

 Wenn Sie eine neue Excel-Arbeitsmappe zur Laufzeit erstellen, werden sie vom Typ <xref:Microsoft.Office.Interop.Excel.Workbook>. Da das Arbeitsblatt kein Hostelement ist, kann es keine Hoststeuerelemente bzw. Windows Forms-Steuerelemente enthalten. Weitere Informationen zum Erstellen von Arbeitsmappen zur Laufzeit finden Sie unter [Vorgehensweise: Programmgesteuertes Erstellen neuer Arbeitsmappen](../vsto/how-to-programmatically-create-new-workbooks.md).

 Das <xref:Microsoft.Office.Tools.Excel.Workbook> Hostelement dient nicht als Container für Hoststeuerelemente. Daher können Sie der Arbeitsmappe keine sichtbaren Steuerelemente hinzufügen. Sie können jedoch Komponenten wie <xref:System.Data.DataSet>hinzufügen, sodass die Komponenten von allen Arbeitsblättern gemeinsam genutzt werden können. In einem Projekt auf Dokumentebene befinden sich die für die Arbeitsmappe verfügbare Komponenten auf den Registerkarten **Komponente** , **Daten** und **Alle Windows Forms** der **Toolbox**.

> [!NOTE]
>  Die Office-Entwicklungstools in Visual Studio unterstützen keine freigegebenen Arbeitsmappen.

## <a name="understand-workbook-host-items-in-vsto-add-in-projects"></a>Verstehen Sie Arbeitsmappen-Hostelementen in VSTO-Add-in-Projekten
 Sie können in VSTO-Add-in-Projekte generieren eine <xref:Microsoft.Office.Tools.Excel.Workbook> Hostelements zur Laufzeit für jede Arbeitsmappe, die in Excel geöffnet ist. Verwenden Sie zum Generieren eines <xref:Microsoft.Office.Tools.Excel.Workbook>-Hostelements die `GetVstoObject`-Methode. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Siehe auch
- [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)
- [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)
- [Arbeitsblatthostelement](../vsto/worksheet-host-item.md)
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
