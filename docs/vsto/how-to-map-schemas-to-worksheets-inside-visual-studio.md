---
title: 'Vorgehensweise: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b2d0caadfc08d7fa1d2ea29d04e84a5d954a42fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Gewusst wie: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio
  Sie können ein XML-Schema zu einem Arbeitsblatt zuordnen, während das Arbeitsblatt in Visual Studio geöffnet ist. Sie verwenden den gleichen Microsoft Office Excel-Tools, die Sie verwenden, wenn die Arbeitsmappe außerhalb von Visual Studio geöffnet ist. Die Office-Projekt erstellt dieselben Objekte, ob Sie das Schema der Tabelle vor dem zuordnen oder nach der Erstellung der Excel-Projektmappe.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Sie können keine mehrteiligen XML-Schemas in Excel-Projektmappen.  
  
### <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Zuordnen ein XML-Schemas zu einem Excel-Arbeitsblatt in Visual Studio  
  
1.  Öffnen Sie die Excel-Arbeitsmappe oder einem Vorlagenprojekt Projekt innerhalb von Visual Studio.  
  
2.  Klicken Sie in das Arbeitsblatt zum Verschieben des Fokus in den Designer.  
  
3.  Klicken Sie im Menüband auf die Registerkarte **Entwickler** .  
  
    > [!NOTE]  
    >  Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen der Registerkarte "Entwickler" auf der Multifunktionsleiste](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  In der **XML** zu gruppieren, klicken Sie auf **Quelle**.  
  
     Die **XML-Quelle** Fenster wird geöffnet.  
  
5.  In der **XML-Quelle** Fenster, klicken Sie auf **XML-Zuordnungen**.  
  
     Die **XML-Zuordnungen** Dialogfeld wird geöffnet.  
  
6.  In der **XML-Zuordnungen** (Dialogfeld), klicken Sie auf **hinzufügen**.  
  
7.  Navigieren Sie zu der Schemadatei, wählen Sie diese, und klicken Sie dann auf **öffnen**.  
  
8.  Klicken Sie auf **OK**.  
  
     Das Schema wird dargestellt, der **XML-Quelle** Fenster. In Ihrem Projekt ein typisiertes <xref:System.Data.DataSet> wird basierend auf dem Schema generiert und ein <xref:System.Windows.Forms.BindingSource> wird erstellt.  
  
9. Ziehen Sie Elemente aus der **XML-Quelle** Fenster aus, um den Stellen in Ihrem Arbeitsblatt, in denen die entsprechenden Steuerelemente erstellt werden sollen.  
  
     Wenn Sie ein nicht wiederholendes Schemaelement ziehen, generiert das Office-Projekt ein <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Steuerelement, das automatisch an gebunden ist die <xref:System.Windows.Forms.BindingSource>.  
  
     Wenn Sie ein sich wiederholendes Schemaelement ziehen, generiert das Office-Projekt ein <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement, das nicht automatisch an eine Datenquelle gebunden ist. Weitere Informationen finden Sie unter [XML-Schemas und Daten in Anpassungen auf Dokumentebene](../vsto/xml-schemas-and-data-in-document-level-customizations.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [XML-Schemas und -Daten in Anpassungen auf Dokumentebene](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  