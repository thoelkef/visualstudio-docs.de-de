---
title: Eigenschaften in Office-Projekten
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Trust Assemblies Location property
- Cache in Document property
- properties [Office development in Visual Studio]
- Namespace for Host Item property
- Office projects [Office development in Visual Studio], properties
- projects [Office development in Visual Studio], properties
- Value2 property
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2b5c5e0719f7b619fa00a3a0f4333ae0080c0715
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692771"
---
# <a name="properties-in-office-projects"></a>Eigenschaften in Office-Projekten
  Es gibt mehrere wichtige Eigenschaften, die für Office-Projekte in Visual Studio verfügbar sind. Sie können auf diese Eigenschaften über das Fenster **Eigenschaften** zugreifen.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="namespace-for-host-item"></a>Namespace für Hostelement  
 Verwenden Sie die Eigenschaft **Namespace für Hostelement** , um den Namespace für Hostelementklassen (z. B. die Klassen `ThisAddIn`, `ThisWorkbook`oder `ThisDocument` ) in Visual C#-Projekten zu ändern. Diese Eigenschaft wird der **Eigenschaften** Fenster bei der Auswahl von des Dokumentknotens in einem Projekt auf Dokumentebene (z. B. *"ExcelWorkbook1.xlsx"* oder *"WordDocument1.docx"* ) oder den Anwendungsknoten in einem VSTO-Add-in-Projekt (z. B. Excel oder Word) im **Projektmappen-Explorer**.  
  
 Wenn Sie ein Visual C#-Office-Projekt erstellen, erhalten Hostelemente einen Namespace, der auf dem Namen des Projekts basiert. Es wird empfohlen, die Eigenschaft **Namespace für Hostelement** zu verwenden, um den Namespace zu ändern, anstatt die Codedateien direkt zu bearbeiten. Wenn Sie diese Eigenschaft verwenden, wird der Namespace in den generierten (ausgeblendeten) Codedateien und in den sichtbaren Codedateien geändert.  
  
## <a name="cacheindocument"></a>CacheInDocument  
 Die **CacheInDocument** -Eigenschaft wird im Fenster **Eigenschaften** für Projekte der Dokumentebene angezeigt, wenn Sie eine Instanz von <xref:System.Data.DataSet> im Visual Studio-Designer auswählen. Nur öffentliche Member können zwischengespeichert werden. Stellen Sie sicher, dass die **Modifiers** -Eigenschaft auf **Public** festgelegt ist, wenn Sie ein <xref:System.Data.DataSet>-Element zwischenspeichern möchten.  
  
 Diese Eigenschaft verwendet einen booleschen Wert:  
  
-   Wählen Sie **true** , um das DataSet im Dokument zwischenzuspeichern.  
  
-   Wählen Sie **false** , wenn Sie das DataSet nicht im Dokument zwischenspeichern möchten.  
  
 Weitere Informationen zum Zwischenspeichern von Daten finden Sie unter [zwischengespeicherten Daten in Anpassungen auf Dokumentebene](../vsto/cached-data-in-document-level-customizations.md).  
  
## <a name="value2"></a>Value2  
 Die **Value2** -Eigenschaft ist nur für Excel-Arbeitsmappen oder Vorlagenprojekte verfügbar. Sie wird im Fenster **Eigenschaften** unter dem Eigenschaftenknoten **Databindings** angezeigt, wenn Sie im Arbeitsblatt-Designer ein <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement auswählen.  
  
 Verwenden Sie die **Value2** -Eigenschaft im Fenster **Eigenschaften** , um die <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> -Eigenschaft des <xref:Microsoft.Office.Tools.Excel.NamedRange> -Elements an ein Feld in Ihrer Datenquelle zu binden.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)   
 [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)   
 [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md)  
  
  