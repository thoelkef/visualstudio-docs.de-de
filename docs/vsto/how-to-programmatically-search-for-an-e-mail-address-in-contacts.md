---
title: Suchen Sie programmgesteuert eine e-Mail-Adresse in den Kontakten
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26e32314db68ae064edac5537222447625cb051d
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328975"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>Vorgehensweise: Suchen Sie programmgesteuert eine e-Mail-Adresse in den Kontakten
  In diesem Beispiel wird ein Kontaktordner nach Kontakten durchsucht, die den Domänennamen **example.com** in ihren E-Mail-Adressen aufweisen.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Beispiel benötigen Sie Folgendes:

- Kontakte mit dem Domänennamen **example.com** in ihren E-Mail-Adressen (z. B. `somebody@example.com`), die einen Vor- und Nachnamen aufweisen.

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Kontaktelementen](../vsto/working-with-contact-items.md)
- [Vorgehensweise: Programmgesteuertes Senden von e-Mail-Adresse](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Vorgehensweise: Programmgesteuertes Zugreifen auf Outlook-Kontakte](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Vorgehensweise: Programmgesteuertes Hinzufügen eines Eintrags zu Outlook-Kontakten](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
