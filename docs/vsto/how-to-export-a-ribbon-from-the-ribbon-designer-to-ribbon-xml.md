---
title: "Vorgehensweise: Exportieren eines Menübands vom Menüband-Designer in Multifunktionsleisten-XML | Microsoft Docs"
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
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- Ribbon [Office development in Visual Studio], exporting
- XML [Office development in Visual Studio], Ribbon
- Ribbon Designer [Office development in Visual Studio]
- exporting Ribbon
ms.assetid: 96e0e9ed-4392-4f45-ac33-b6f7c22ea321
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b73bff8170e351e9e22e95d53ae446895cfdbd2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Gewusst wie: Exportieren einer Multifunktionsleiste aus dem Multifunktionsleisten-Designer in Multifunktionsleisten-XML
  Die **Menüband (visueller Designer)** Element unterstützt nicht alle Mögliche Typen der menübandanpassung. Zum Anpassen des Menübands auf eine innovative Weise können Sie im Menüband vom Designer in Menüband-XML exportieren und den XML-Code direkt bearbeiten.  
  
> [!NOTE]  
>  Nicht alle Eigenschaftswerte, die in der Menüband-XML-Datei angezeigt werden. Weitere Informationen finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Zum Exportieren eines Menübands vom Menüband-Designer in Menüband-XML  
  
1.  Mit der rechten Maustaste in der Menüband-Codedatei **Projektmappen-Explorer**, und klicken Sie dann auf **Sicht-Designer**.  
  
2.  Mit der rechten Maustaste in der Menüband-Designer, und klicken Sie dann auf **Menüband nach XML exportieren**.  
  
     Visual Studio fügt eine Menüband-XML-Datei und eine Codedatei des Menüband-XML zu Ihrem Projekt.  
  
3.  Suchen Sie in der Menübandklasse Code Kommentare, die mit beginnt `TODO:`.  
  
4.  Kopieren Sie den Codeblock in diese Kommentare an die **"ThisAddIn"**, **ThisWorkbook**, oder **ThisDocument** Klasse, je nachdem, welche Art von Lösung, die Sie entwickeln.  
  
     Dieser Code ermöglicht es, die Microsoft Office-Anwendung zu ermitteln und laden das benutzerdefinierte Menüband. Weitere Informationen finden Sie unter [Ribbon XML](../vsto/ribbon-xml.md).  
  
5.  In der **"ThisAddIn"**, **ThisWorkbook**, oder **ThisDocument** Klasse, kommentieren Sie den Codeblock.  
  
     Nachdem Sie den Code kommentieren, sollte es im folgende Beispiel ähneln. In diesem Beispiel heißt der Ribbon-Klasse `MyRibbon`.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  Wechseln Sie zu der Codedatei des Menüband-XML, und suchen die `Ribbon Callbacks` Region.  
  
     Dies ist das Schreiben Sie Rückrufmethoden Benutzeraktionen wie das Klicken auf eine Schaltfläche zu behandeln.  
  
7.  Erstellen Sie eine Rückrufmethode für jeden Ereignishandler, die Sie in der Menüband-Designer-Code geschrieben hat.  
  
8.  Verschieben Sie alle Ereignishandlercode aus den Ereignishandlern zu Rückrufmethoden, und ändern Sie den Code mit dem Programmmodell für die menübanderweiterung (RibbonX) Programmiermodell arbeiten.  
  
     Informationen zum Schreiben von Rückrufmethoden, und verwenden das RibbonX-Programmiermodell finden Sie unter [Menüband-XML-](../vsto/ribbon-xml.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über das Menüband](../vsto/ribbon-overview.md)   
 [Menüband-Designer](../vsto/ribbon-designer.md)   
 [Menüband-XML](../vsto/ribbon-xml.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  