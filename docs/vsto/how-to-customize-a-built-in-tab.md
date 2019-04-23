---
title: 'Vorgehensweise: Anpassen einer integrierten Registerkarte'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5a686d2a43fed0fdb8c5c1e8f21d4b35fd63f3a6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60075661"
---
# <a name="how-to-customize-a-built-in-tab"></a>Vorgehensweise: Anpassen einer integrierten Registerkarte
  Einer integrierten Registerkarte können Gruppen und Steuerelemente hinzugefügt werden. Eine integrierte Registerkarte ist eine Registerkarte, die sich bereits auf dem Menüband einer Microsoft Office-Anwendung befindet. Z. B. die **Daten** Registerkarte ist eine integrierte Registerkarte in Excel. Wenn Sie eine benutzerdefinierte Gruppe erstellen, wird diese auf der Registerkarte an letzter Stelle angezeigt. Sie können die Gruppe aber an eine beliebige Position auf der Registerkarte verschieben.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
>  Sie können einer integrierten Registerkarte Gruppen hinzufügen, die integrierten Gruppen jedoch nicht von einer integrierten Registerkarte entfernen.

### <a name="to-add-groups-to-a-built-in-tab"></a>So fügen Sie einer integrierten Registerkarte Gruppen hinzu

1. Mit der rechten Maustaste in der Menüband-Codedatei **Projektmappen-Explorer**, und klicken Sie dann auf **Ansicht-Designer**.

    > [!NOTE]
    >  Wenn Sie nicht in der Menüband-Codedatei angezeigt wird **Projektmappen-Explorer**, müssen Sie hinzufügen, eine **Element "Menüband"** zu Ihrem Projekt. Weitere Informationen finden Sie unter [How to: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. Mit der rechten Maustaste in eine beliebige Registerkarte im Menüband-Designer, und klicken Sie dann auf **Eigenschaften**.

3. In der **Eigenschaften** Fenster, erweitern Sie die **ControlId** -Eigenschaft, und legen die **ControlIdType** Eigenschaft **Office**.

4. Legen Sie die **OfficeId** Eigenschaft, um die *Steuerelement-ID* der integrierten Registerkarte, die Sie anpassen möchten.

     Die Steuerelement-ID ist der Name, mit dem Registerkarten, Gruppen und Steuerelemente eindeutig identifiziert werden, die in Microsoft Office-Anwendungen integriert sind.

     Eine Liste der Steuerelement-IDs, finden Sie unter [Office 2010-Hilfedateien: Steuerelement-IDs für Office fluent User Interface](http://go.microsoft.com/fwlink/?LinkID=181052).

5. Von der **Steuerelemente für Office-Menübänder** Registerkarte die **Toolbox**, ziehen Sie Gruppen auf der Registerkarte ".

    > [!NOTE]
    >  Integrierte Gruppen werden im Designer nicht angezeigt. Die einzige Möglichkeit, zu bestimmen, ob Sie mit einer integrierten Registerkarte arbeiten aus diesem Grund ist, untersuchen die **ControlId** -Eigenschaft auf der Registerkarte.

### <a name="to-position-groups-on-a-built-in-tab"></a>So ordnen Sie Gruppen auf einer integrierten Registerkarte an

1. Wählen Sie im Menüband-Designer eine benutzerdefinierte Gruppe aus.

2. In der **Eigenschaften** Fenster, erweitern Sie die **Position** Eigenschaft.

3. Legen Sie die **PositionType** Eigenschaft auf den entsprechenden Wert:

    - **BeforeOfficeId** wird die Gruppe vor einer angegebenen integrierten Gruppe.

    - **AfterOfficeId** wird die Gruppe nach einer angegebenen integrierten Gruppe angeordnet.

4. Legen Sie die **OfficeId** Eigenschaft, um die Steuerelement-ID einer integrierten Gruppe.

     Eine Liste der Steuerelement-IDs, finden Sie unter [Office 2010-Hilfedateien: Steuerelement-IDs für Office fluent User Interface](http://go.microsoft.com/fwlink/?LinkID=181052).

## <a name="see-also"></a>Siehe auch
- [Übersicht über das Menüband](../vsto/ribbon-overview.md)
- [Menüband-Designer](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Vorgehensweise: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Vorgehensweise: Ändern der Position einer Registerkarte des Menübands](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Vorgehensweise: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Vorgehensweise: Add-In-Benutzeroberflächenfehler anzeigen](../vsto/how-to-show-add-in-user-interface-errors.md)
