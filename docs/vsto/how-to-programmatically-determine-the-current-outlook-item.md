---
title: 'Vorgehensweise: Programmgesteuertes Bestimmen des aktuellen Outlook-Elements'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3608f516eb9206bc5b4c232c227d3e49c2414be7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599752"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Vorgehensweise: Programmgesteuertes Bestimmen des aktuellen Outlook-Elements
  Dieses Beispiel verwendet die `Explorer.SelectionChange` Ereignis, um den Namen des aktuellen Ordners und einige Informationen über das ausgewählte Element anzuzeigen. Der Code zeigt das ausgewählte Element.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Beispiel benötigen Sie Folgendes:

-   Termin, wenden Sie sich an und e-Mail-Elemente in Microsoft Office Outlook.

## <a name="see-also"></a>Siehe auch
- [Übersicht über Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)
- [Vorgehensweise: Programmgesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Vorgehensweise: Programmgesteuertes Suchen eines bestimmten Kontakts](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
