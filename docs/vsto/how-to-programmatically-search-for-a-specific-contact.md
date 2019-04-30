---
title: 'Vorgehensweise: Programmgesteuertes Suchen eines bestimmten Kontakts'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: feff583d28bf53f4bffc9b425d52902688b80a4b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000324"
---
# <a name="how-to-programmatically-search-for-a-specific-contact"></a>Vorgehensweise: Programmgesteuertes Suchen eines bestimmten Kontakts
  Dieses Beispiel durchsucht einen Outlook-Kontaktordner über den Vor- und Nachnamen nach einem bestimmten Kontakt. Im Beispiel wird vorausgesetzt, dass ein Kontakt namens **John Evans** im Kontaktordner vorhanden ist.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/CSharp/trin_outlook_rl_searchforcontact/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/VisualBasic/trin_outlook_rl_searchforcontact/thisaddin.vb#1)]

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Kontaktelementen](../vsto/working-with-contact-items.md)
- [Erste Schritte zum Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)
