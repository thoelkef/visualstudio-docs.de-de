---
title: 'Vorgehensweise: Exportieren eines Menübands vom Menüband-Designer in Menüband-XML'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 370c2e1d08c47b8a5068d0227426d2b4083590a5
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53646931"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Vorgehensweise: Exportieren eines Menübands vom Menüband-Designer in Menüband-XML
  Die **Menüband (visueller Designer)** Element unterstützt nicht alle mögliche Arten von Multifunktionsleisten-Anpassung. Zum Anpassen des Menübands auf eine innovative Weise können Sie exportieren im Menüband vom Designer in Menüband-XML und den XML-Code direkt bearbeiten.  
  
> [!NOTE]  
>  Nicht alle Eigenschaftswerte, die in der Menüband-XML-Datei angezeigt werden. Weitere Informationen finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Um eines Menübands vom Menüband-Designer in Menüband-XML exportieren  
  
1.  Mit der rechten Maustaste in der Menüband-Codedatei **Projektmappen-Explorer**, und klicken Sie dann auf **Ansicht-Designer**.  
  
2.  Mit der rechten Maustaste in der Menüband-Designer, und klicken Sie dann auf **Menüband nach XML exportieren**.  
  
     Visual Studio fügt eine Menüband-XML-Datei und eine Codedatei des Menüband-XML zu Ihrem Projekt.  
  
3.  Suchen Sie in der Menüband-Code-Klasse, die Kommentare, die mit beginnen `TODO:`.  
  
4.  Kopieren Sie den Codeblock in diesen Kommentaren in der **ThisAddin**, **ThisWorkbook**, oder **ThisDocument** Klasse, je nachdem, welche Art von Lösung, die Sie entwickeln.  
  
     Dieser Code ermöglicht, Microsoft Office-Anwendung zu ermitteln und laden das benutzerdefinierte Menüband. Weitere Informationen finden Sie unter [Ribbon XML](../vsto/ribbon-xml.md).  
  
5.  In der **ThisAddin**, **ThisWorkbook**, oder **ThisDocument** Klasse, heben Sie die auskommentierung des Codeblocks.  
  
     Nachdem Sie den Code auskommentiert haben, sollte es im folgende Beispiel entsprechen. In diesem Beispiel heißt die Ribbon-Klasse `MyRibbon`.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  Wechseln Sie zu der Codedatei des Menüband-XML, und suchen die `Ribbon Callbacks` Region.  
  
     Dies ist das Schreiben Sie Rückrufmethoden Benutzeraktionen wie das Klicken auf eine Schaltfläche zu behandeln.  
  
7.  Erstellen Sie eine Rückrufmethode für jeden Ereignishandler, die Sie in der Menüband-Designer-Code geschrieben haben.  
  
8.  Verschieben Sie alle den Ereignishandlercode aus den Ereignishandlern in die Rückrufmethoden, und ändern Sie den Code zum Arbeiten mit den für die menübanderweiterung (RibbonX) Programmiermodell.  
  
     Informationen zum Schreiben von Rückrufmethoden, und verwenden das RibbonX-Programmiermodell finden Sie unter [Menüband-XML-](../vsto/ribbon-xml.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über das Menüband](../vsto/ribbon-overview.md)   
 [Menüband-Designer](../vsto/ribbon-designer.md)   
 [Menüband-XML](../vsto/ribbon-xml.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  