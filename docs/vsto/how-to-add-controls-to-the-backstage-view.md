---
title: 'Vorgehensweise: Hinzufügen von Steuerelementen zur Backstage-Ansicht | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1cdda3960363ba87e9434cd14077c7182a9f56c4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Gewusst wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht
  Können Sie dem Menüband-Designer zum Hinzufügen von Steuerelementen zum Menü, das geöffnet wird, wenn Sie auf die **Datei** Registerkarte beim Ausführen der Anwendung, Steuerelemente, die Sie zum Hinzufügen der **Datei** Registerkarte angezeigt werden, eine Gruppe namens  **Add-ins**.  
  
 Sie können keine Steuerelemente vor oder nach integrierten Steuerelementen positionieren, mithilfe des Menüband-Designers in Visual Studio. Ein integriertes Steuerelement ist ein Steuerelement, das bereits in der Backstage-Ansicht angezeigt wird. Wenn Sie Steuerelemente vor oder nach integrierten Steuerelementen positionieren möchten, müssen Sie eine Menüband-XML verwenden. Weitere Informationen zu **Menüband (XML)**, finden Sie unter [Menüband-XML-](../vsto/ribbon-xml.md). Weitere Informationen zum Anpassen der Backstage-Ansicht finden Sie unter [Einführung in die Office 2010-Backstage-Ansicht für Entwickler](http://go.microsoft.com/fwlink/?LinkId=182189) und [Anpassen von Office 2010-Backstage-Ansicht für Entwickler](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-controls-to-backstage-view"></a>Zum Hinzufügen von Steuerelementen zur Backstage-Ansicht  
  
1.  Öffnen Sie das Element "Menüband" in der Entwurfsansicht.  
  
     Informationen zur Vorgehensweise beim Hinzufügen einer **Menüband (visueller Designer)** finden Sie dem Projekt [wie: Erste Schritte beim, Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Klicken Sie im Menüband-Designer auf die **Datei** Registerkarte.  
  
     Menü-Designer wird angezeigt. Diese Entwurfsoberfläche enthält keine Steuerelemente.  
  
3.  Aus der **Steuerelemente für Office-Menübänder** auf der Registerkarte die **Toolbox**, ziehen Sie eines der folgenden Steuerelemente auf der Designer im Menü:  
  
    -   Schaltfläche  
  
    -   CheckBox  
  
    -   Katalog  
  
    -   Menü  
  
    -   Trennzeichen  
  
    -   SplitButton  
  
    -   ToggleButton  
  
4.  Ziehen Sie Steuerelemente auf das Menü an neue Positionen verschieben.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über das Menüband](../vsto/ribbon-overview.md)   
 [Menüband-Designer](../vsto/ribbon-designer.md)   
 [Menüband-XML](../vsto/ribbon-xml.md)   
 [Vorgehensweise: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  