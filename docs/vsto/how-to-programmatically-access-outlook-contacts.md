---
title: 'Vorgehensweise: programmgesteuerten Zugriff auf Outlook-Kontakten | Microsoft Docs'
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c48a58a4215ce73bcc6e9f4593819cbbdbed1693
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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
  
  