---
title: 'Gewusst wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht '
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
ms.openlocfilehash: 87cea877928baf52b0442ed9b0d952fcf649f155
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986008"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Gewusst wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht
  Mit dem Menüband-Designer können Sie dem Menü Steuerelemente hinzufügen, die geöffnet werden, wenn Sie auf die Registerkarte **Datei** klicken. Wenn Sie die Anwendung ausführen, werden Steuerelemente, die Sie der Registerkarte **Datei** hinzufügen, als Gruppe mit dem Namen **Add-ins**angezeigt.

 Mithilfe des Menüband-Designers in Visual Studio können Sie keine Steuerelemente vor oder nach integrierten Steuerelementen positionieren. Ein integriertes Steuerelement ist ein Steuerelement, das bereits in der Backstage-Ansicht angezeigt wird. Wenn Sie Steuerelemente vor oder nach integrierten Steuerelementen positionieren möchten, müssen Sie eine Menüband-XML-Datei verwenden. Weitere Informationen zu **Menüband (XML)** finden Sie unter [Menüband-XML](../vsto/ribbon-xml.md). Weitere Informationen zum Anpassen der Backstage-Ansicht finden Sie unter [Einführung in die Office 2010-Backstage-Ansicht für Entwickler](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) und [Anpassen der Office 2010-Backstage-Ansicht für Entwickler](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-controls-to-backstage-view"></a>So fügen Sie der Backstage-Ansicht Steuerelemente hinzu

1. Öffnen Sie das Menü Band Element in Designansicht.

     Weitere Informationen zum Hinzufügen eines Elements vom Typ " **Menüband (visueller Designer)** " zu Ihrem Projekt finden Sie unter Gewusst [wie: Starten der Anpassung des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. Klicken Sie im Menüband-Designer auf die Registerkarte **Datei** .

     Ein Menü-Designer wird angezeigt. Diese Entwurfs Oberfläche enthält keine Steuerelemente.

3. Ziehen Sie von der Registerkarte Steuer **Elemente für Office** -Menü Bänder der **Toolbox**eines der folgenden Steuerelemente auf den Menü-Designer:

    - Schaltfläche

    - CheckBox

    - Katalog

    - Menü

    - Trennzeichen

    - SplitButton

    - ToggleButton

4. Ziehen Sie Steuerelemente, um Sie an neue Positionen im Menü zu verschieben.

## <a name="see-also"></a>Siehe auch
- [Übersicht über Menüband](../vsto/ribbon-overview.md)
- [Menüband-Designer](../vsto/ribbon-designer.md)
- [Menüband-XML](../vsto/ribbon-xml.md)
- [Gewusst wie: Starten der Multifunktionsleiste](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
