---
title: 'Vorgehensweise: Erste Schritte beim Anpassen des Menübands'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, adding Ribbon to project
- Ribbon [Office development in Visual Studio], adding
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, adding Ribbon to project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 14c4ff1e8bf443351f835d74d44b49bbb61e0321
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640115"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Vorgehensweise: Erste Schritte beim Anpassen des Menübands
  Fügen Sie zum Anpassen des Menübands einer Microsoft Office-Anwendung eine **Menüband (visueller Designer)** oder **Menüband (XML)** Element, das ein Office-Projekt.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Hinzufügen eine Multifunktionsleiste zu einem Projekt

1. Auf der **Projekt** Menü klicken Sie auf **neues Element hinzufügen**.

2. In der **neues Element hinzufügen** wählen Sie im Dialogfeld **Menüband (visueller Designer)** oder **Menüband (XML)**. Weitere Informationen zu diesen Vorlagen finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).

3. In der **Namen** geben einen Namen für das Element "Menüband".

    Dürfen enthalten keine die folgenden Zeichen:

   -   Nummernzeichen (#)

   -   Prozentzeichen (%)

   -   Kaufmännisches und-Zeichen (&)

   -   Sternchen (*)

   -   Senkrechter Strich (|)

   -   Umgekehrter Schrägstrich (\\)

   -   Doppelpunkt (:)

   -   Doppeltes Anführungszeichen (")

   -   Kleiner als (\<)

   -   Größer als (>)

   -   Fragezeichen (?)

   -   Schrägstrich (/)

   -   Führende oder nachfolgende Leerzeichen ("")

   -   Z. B. ("Nul", "Aux", "con", "com1", "lpt1" usw.) Windows oder DOS reservierte Namen

4. Klicken Sie auf **OK**.

   Das Element "Menüband" wird im **Projektmappen-Explorer**. Weitere Informationen zu den nächsten Schritten finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).

## <a name="see-also"></a>Siehe auch
- [Zugriff auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)
- [Menüband-Designer](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
