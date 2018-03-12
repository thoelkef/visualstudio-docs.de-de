---
title: 'Vorgehensweise: programmgesteuerten Zugriff auf Outlook-Kontakten | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 4d4d88416507f7e63cd112df350dc93b2e13605f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Gewusst wie: Programmgesteuertes Zugreifen auf Outlook-Kontakte
  In diesem Beispiel findet alle Kontakte, deren Nachname eine angegebene Suchzeichenfolge.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Für dieses Beispiel benötigen Sie Folgendes:  
  
-   Kontakte, deren Nachnamen die Zeichenfolge enthalten "**Na"** (z. B. Tzipi Butnaru) in der **Kontakte** Ordner.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Kontaktelementen](../vsto/working-with-contact-items.md)   
 [Vorgehensweise: Programmgesteuertes Hinzufügen eines Eintrags zu Outlook-Kontakten](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [Vorgehensweise: Programmgesteuertes Suchen eines bestimmten Kontakts](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [Vorgehensweise: programmgesteuerte Suche einer e-Mail-Adresse in den Kontakten](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [Vorgehensweise: Programmgesteuertes Löschen von Outlook-Kontakten](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  