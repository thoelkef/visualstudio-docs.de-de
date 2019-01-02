---
title: 'Vorgehensweise: Programmgesteuertes Zugreifen auf Outlook-Kontakte'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 662190d3db9c3d384d60f4953ea3809cb726f76c
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/27/2018
ms.locfileid: "53801722"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Vorgehensweise: Programmgesteuertes Zugreifen auf Outlook-Kontakte
  Dieses Beispiel ermittelt alle Kontakte, deren Nachname eine angegebene Suchzeichenfolge enthalten.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 Für dieses Beispiel benötigen Sie Folgendes:  
  
-   Kontakte, deren Nachname die Zeichenfolge enthalten "**Na"** (z. B. Tzipi Butnaru) in der **Kontakte** Ordner.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Kontaktelementen](../vsto/working-with-contact-items.md)   
 [Vorgehensweise: Programmgesteuertes Hinzufügen eines Eintrags zu Outlook-Kontakten](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [Vorgehensweise: Programmgesteuertes Suchen eines bestimmten Kontakts](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [Vorgehensweise: Suchen Sie programmgesteuert eine e-Mail-Adresse in den Kontakten](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [Vorgehensweise: Programmgesteuertes Löschen von Outlook-Kontakten](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  