---
title: 'Vorgehensweise: Hinzufügen von XMLMappedRange-Steuerelementen zu Arbeitsblättern'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 55b6c83624c3ccb6c28701cd97753ea155e37288
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Vorgehensweise: Hinzufügen von XMLMappedRange-Steuerelementen zu Arbeitsblättern
  Wenn Sie ein XML-Element auf eine Zelle in Microsoft Office Excel zuordnen, fügt Visual Studio automatisch eine <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> -Steuerelement Ihrem Arbeitsblatt.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Die <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Steuerelement ist nicht verfügbar, auf die **Toolbox** oder **Datenquellen** Fenster. Darüber hinaus kann nicht erstellt <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Steuerelemente programmgesteuert.  
  
## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Zum Hinzufügen von XMLMappedRange-Steuerelement zu einem Arbeitsblatt  
  
1.  Öffnen Sie die Excel-Arbeitsmappe in Visual Studio-Designer.  
  
2.  Öffnen Sie das Arbeitsblatt, in dem Sie das Steuerelement hinzufügen möchten.  
  
3.  Auf der **Developer** auf **Quelle**.  
  
    > [!NOTE]  
    >  Wenn die **Developer** Registerkarte ist nicht auf dem Menüband angezeigt, müssen Sie es aktivieren. Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen der Registerkarte "Entwickler" im Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
     Die **XML-Quelle** Aufgabenbereich angezeigt wird.  
  
4.  In der **XML-Quelle** im Aufgabenbereich, klicken Sie auf **XML-Zuordnungen**.  
  
5.  In der **XML-Zuordnungen** (Dialogfeld), klicken Sie auf **hinzufügen**.  
  
     Die **XML-Quelle** Dialogfeld wird angezeigt.  
  
6.  Wählen Sie ein XML-Schema aus der **XML-Quelle** (Dialogfeld), und klicken Sie auf **öffnen**.  
  
     Das Schema wird hinzugefügt, um die **XML-Zuordnungen** (Dialogfeld).  
  
7.  In der **XML-Zuordnungen** (Dialogfeld), klicken Sie auf **OK**.  
  
8.  Ziehen Sie ein Element aus der **XML-Quelle** im Aufgabenbereich auf eine Zelle im Arbeitsblatt.  
  
     Ein <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> erstellt und dem Projekt hinzugefügt.  
  
    > [!NOTE]  
    >  Wenn Sie ein übergeordnetes Element von Ziehen die **XML-Quelle** im Aufgabenbereich eine <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement erstellt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [XmlMappedRange-Steuerelement](../vsto/xmlmappedrange-control.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Hostelemente und Host-Steuerelemente (Übersicht)](../vsto/host-items-and-host-controls-overview.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Vorgehensweise: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  