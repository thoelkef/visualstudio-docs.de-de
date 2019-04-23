---
title: 'Vorgehensweise: Hinzufügen von Steuerelementen zur Backstage-Ansicht '
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c4241464fe8a43af882fbdbad0f898838e8fd897
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068365"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Vorgehensweise: Hinzufügen von Steuerelementen zur Backstage-Ansicht
  Können Sie zum Hinzufügen von Steuerelementen zum Menü, das geöffnet wird, wenn Sie auf dem Menüband-Designer die **Datei** Registerkarte. Beim Ausführen der Anwendung Steuerelemente, die Sie zum Hinzufügen der **Datei** Registerkarte angezeigt werden, eine Gruppe namens **-Add-ins**.

 Sie können keine Steuerelemente vor oder nach integrierten Steuerelementen positionieren, indem Sie mithilfe des Menüband-Designers in Visual Studio. Ein integriertes Steuerelement ist ein Steuerelement, das bereits in der Backstage-Ansicht angezeigt wird. Wenn Sie Steuerelemente vor oder nach integrierten Steuerelementen positionieren möchten, müssen Sie eine Menüband-XML verwenden. Weitere Informationen zu **Menüband (XML)**, finden Sie unter [Menüband-XML-](../vsto/ribbon-xml.md). Weitere Informationen zum Anpassen der Backstage-Ansicht finden Sie unter [Einführung in die Office 2010-Backstage-Ansicht für Entwickler](http://go.microsoft.com/fwlink/?LinkId=182189) und [anpassen die Office 2010-Backstage-Ansicht für Entwickler](http://go.microsoft.com/fwlink/?LinkId=182188).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-controls-to-backstage-view"></a>Zum Hinzufügen von Steuerelementen zur Backstage-Ansicht

1. Öffnen Sie das Element "Menüband" in der Entwurfsansicht.

     Informationen zur Vorgehensweise beim Hinzufügen einer **Menüband (visueller Designer)** dem Projekt, finden Sie unter [Vorgehensweise: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. Klicken Sie im Menüband-Designer auf die **Datei** Registerkarte.

     Ein Menü-Designer wird angezeigt. Diese Entwurfsoberfläche ist keine Steuerelemente enthalten.

3. Von der **Steuerelemente für Office-Menübänder** Registerkarte die **Toolbox**, ziehen Sie eines der folgenden Steuerelemente auf dem Menü-Designer:

    - Schaltfläche

    - CheckBox

    - Katalog

    - Menü

    - Trennzeichen

    - SplitButton

    - ToggleButton

4. Ziehen Sie Steuerelemente, um sie im Menü an neue Positionen zu verschieben.

## <a name="see-also"></a>Siehe auch
- [Übersicht über das Menüband](../vsto/ribbon-overview.md)
- [Menüband-Designer](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Vorgehensweise: Erste Schritte Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
