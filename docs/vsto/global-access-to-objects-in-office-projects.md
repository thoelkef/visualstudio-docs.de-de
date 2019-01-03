---
title: Globaler Zugriff auf Objekte in Office-Projekten
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument_Shutdown
- ThisDocument_Startup
- Globals class, object global access
- worksheets [Office development in Visual Studio], global access
- documents [Office development in Visual Studio], global access
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- application-level addins [Office development in Visual Studio]
- addins [Office development in Visual Studio], events
- workbooks [Office development in Visual Studio], global access
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio]
- Startup event
- Shutdown event
- projects [Office development in Visual Studio], global access
- Office documents [Office development in Visual Studio, global access
- ThisAddin_Startup
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 843eba9cceefb2360ed24284a80f4359d092fd89
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909072"
---
# <a name="global-access-to-objects-in-office-projects"></a>Globaler Zugriff auf Objekte in Office-Projekten
  Wenn Sie ein Office-Projekt erstellen, generiert Visual Studio im Projekt automatisch eine Klasse mit dem Namen `Globals` . Mit der `Globals` -Klasse können Sie von beliebigem Code im Projekt aus zur Laufzeit auf mehrere verschiedene Projektelemente zugreifen.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="how-to-use-the-globals-class"></a>Gewusst wie: verwenden die Globals-Klasse  
 `Globals` ist eine statische Klasse, in der Verweise auf bestimmte Elemente im Projekt abgelegt sind. Mit der `Globals` -Klasse können Sie von beliebigem Code im Projekt aus zur Laufzeit auf die folgenden Elemente zugreifen:  
  
- Die - `ThisWorkbook` und `Sheet`*n* -Klassen in einer Excel-Arbeitsmappe oder einem Vorlagenprojekt. Sie können mit den `Globals.ThisWorkbook` - und `Sheet`*n* -Eigenschaften auf diese Objekte zugreifen.  
  
- Die `ThisDocument` -Klasse in einem Word-Dokument oder einem Vorlagenprojekt. Sie können mit der `Globals.ThisDocument` -Eigenschaft auf dieses Objekt zugreifen.  
  
- Die `ThisAddIn` Klasse in einem VSTO-Add-in-Projekt. Sie können mit der `Globals.ThisAddIn` -Eigenschaft auf dieses Objekt zugreifen.  
  
- Alle Menübänder im Projekt, das Sie mit dem Menüband-Designer angepasst haben. Sie können mit der `Globals.Ribbons` -Eigenschaft auf die Menübänder zugreifen. Weitere Informationen finden Sie unter [Zugriff auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md).  
  
- Alle Outlook-Formularbereiche in einem VSTO-Add-In-Projekt für Outlook. Sie können mit der `Globals.FormRegions` -Eigenschaft auf die Formularbereiche zugreifen. Weitere Informationen finden Sie unter [Zugriff auf einen Formularbereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md).  
  
- Ein Factoryobjekt, das Ihnen ermöglicht, Menübandsteuerelemente zu erstellen und Hostelemente zur Laufzeit in Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]abzielen. Sie können mit der `Globals.Factory` -Eigenschaft auf dieses Objekt zugreifen. Dieses Objekt ist eine Instanz einer Klasse, die eine der folgenden Schnittstellen implementiert:  
  
  -   <xref:Microsoft.Office.Tools.Factory>  
  
  -   <xref:Microsoft.Office.Tools.Excel.Factory>  
  
  -   <xref:Microsoft.Office.Tools.Outlook.Factory>  
  
  -   <xref:Microsoft.Office.Tools.Word.Factory>  
  
  Beispielsweise können Sie Text mithilfe der `Globals.Sheet1` -Eigenschaft in ein <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement auf `Sheet1` einfügen, wenn ein Benutzer in einem Projekt auf Dokumentebene für Excel auf eine Schaltfläche im Aktionsbereich klickt.  
  
  [!code-vb[Trin_VstcoreProgramming#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#1)]
  [!code-csharp[Trin_VstcoreProgramming#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#1)]  
  
## <a name="initialize-the-globals-class"></a>Initialisieren der Globals-Klasse  
 Code, der versucht, den `Globals` -Klasse, bevor das Dokument oder ein VSTO-Add-in initialisiert wird möglicherweise eine Laufzeitausnahme auslösen. So kann beispielsweise die Verwendung von `Globals` beim Deklarieren einer Variablen auf Klassenebene fehlschlagen, da die `Globals` -Klasse vor der Instanziierung des deklarierten Objekts möglicherweise noch nicht mit Verweisen auf alle Hostelemente initialisiert wurde.  
  
> [!NOTE]  
>  Die `Globals` -Klasse wird zur Entwurfszeit nie initialisiert, vom Designer werden jedoch Steuerelementinstanzen erstellt. Dies bedeutet, dass Sie beim Erstellen eines Benutzersteuerelements mit einer Eigenschaft der `Globals` -Klasse innerhalb einer Benutzersteuerelementklasse überprüfen müssen, ob die Eigenschaft **null** zurückgibt, bevor Sie das zurückgegebene Objekt verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Zugriff auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Zugriff auf einen Formularbereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)   
 [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)   
 [Dokumenthostelement](../vsto/document-host-item.md)   
 [Arbeitsmappenhostelement](../vsto/workbook-host-item.md)   
 [Arbeitsblatthostelement](../vsto/worksheet-host-item.md)   
 [Schreiben Sie Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)  
