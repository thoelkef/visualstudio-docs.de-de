---
title: 'Vorgehensweise: Ändern der Position einer Registerkarte des Menübands'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 512dfda8c95ecd56fe44eb6878e6abc0d942a782
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62826731"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Vorgehensweise: Ändern der Position einer Registerkarte des Menübands
  Sie können die Reihenfolge von benutzerdefinierten Registerkarten auf einem Menüband ändern, mit der **Registerkartenauflistungs-Editor**. Benutzerdefinierte Registerkarten können vor oder nach einer integrierten Registerkarte auf dem Menüband angeordnet werden. Eine integrierte Registerkarte ist eine Registerkarte, die sich bereits auf dem Menüband einer Microsoft Office-Anwendung befindet. Z. B. die **Daten** Registerkarte ist eine integrierte Registerkarte in Excel.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>So ändern Sie die Reihenfolge der Registerkarten auf dem Menüband

1. Wählen Sie die Menüband-Codedatei (*vb* oder *cs* Datei) in **Projektmappen-Explorer**.

2. Auf der **Ansicht** Menü klicken Sie auf **Designer**.

3. Mit der rechten Maustaste in der Menüband-Designer, und klicken Sie dann auf **Eigenschaften**.

4. In der **Eigenschaften** wählen Sie im Fenster der **Registerkarten** -Eigenschaft, und klicken Sie dann auf die Schaltfläche mit den Auslassungspunkten (![ASP.NET mobile-Designer-Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer Ellipse")).

     Die **Registerkartenauflistungs-Editor** angezeigt wird.

5. In der **Registerkartenauflistungs-Editor**in die **Mitglieder** Liste, wählen Sie die Registerkarte, die Sie verschieben, und klicken Sie auf den Pfeil nach oben oder nach-unten-Pfeile, um die Aktivierreihenfolge ändern möchten.

### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Um eine Registerkarte vor oder nach einer integrierten Registerkarte auf dem Menüband positionieren.

1. Wählen Sie eine benutzerdefinierte Registerkarte im Menüband-Designer.

2. In der **Eigenschaften** Fenster erweitern Sie die **ControlId** -Eigenschaft, und klicken Sie dann sicher, dass der Wert des der **ControlIdType** -Eigenschaftensatz auf **benutzerdefinierte**.

3. In der **Eigenschaften** Fenster, erweitern Sie die **Position** Eigenschaft.

4. Legen Sie die **PositionType** Eigenschaft auf den entsprechenden Wert:

    - **BeforeOfficeId** wird die Gruppe vor einer angegebenen integrierten Registerkarte.

    - **AfterOfficeId** wird die Gruppe nach einer angegebenen integrierten Registerkarte.

5. Legen Sie die **OfficeId** Eigenschaft, um die Steuerelement-ID einer integrierten Registerkarte.

     Eine Liste der Steuerelement-IDs, finden Sie unter [Office 2010-Hilfedateien: Steuerelement-IDs für Office fluent User Interface](http://go.microsoft.com/fwlink/?LinkID=181052).

## <a name="see-also"></a>Siehe auch
- [Übersicht über das Menüband](../vsto/ribbon-overview.md)
- [Menüband-Designer](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
