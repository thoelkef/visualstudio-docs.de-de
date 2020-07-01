---
title: 'Gewusst wie: Starten der Anpassung des Menübands'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: be311f87862f4447d903294508927735d3507b08
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520067"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Gewusst wie: Starten der Anpassung des Menübands
  Fügen Sie einem Office-Projekt ein **Menüband (visueller Designer)** oder ein **Menüband (XML)** -Element hinzu, um das Menüband einer Microsoft Office-Anwendung anzupassen.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>So fügen Sie einem Projekt ein Menüband hinzu

1. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Menüband (visueller Designer)** oder **Menüband (XML)** aus. Weitere Informationen zu diesen Vorlagen finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).

3. Geben Sie im Feld **Name** einen Namen für das Menü Band Element ein.

    Folgende Zeichen dürfen nicht in den Namen verwendet werden:

   - Nummernzeichen (#)

   - Prozent (%)

   - Kaufmännisches Und-Zeichen (&)

   - Sternchen (*)

   - Senkrechter Strich (|)

   - Umgekehrter Schrägstrich (\\)

   - Doppelpunkt (:)

   - Doppeltes Anführungszeichen (")

   - Kleiner als (\<)

   - Größer als (>)

   - Fragezeichen (?)

   - Schrägstrich (/)

   - Führende oder nachfolgende Leerzeichen (' ')

   - Namen, die für Windows oder DOS reserviert sind, z. b. ("NUL", "AUX", "con", "COM1", "LPT1" usw.)

4. Klicken Sie auf **OK**.

   Das Menü Band Element wird in **Projektmappen-Explorer**angezeigt. Weitere Informationen zu den nächsten Schritten finden Sie unter Übersicht über das [Menüband](../vsto/ribbon-overview.md).

## <a name="see-also"></a>Siehe auch
- [Zugreifen auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)
- [Menüband-Designer](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
