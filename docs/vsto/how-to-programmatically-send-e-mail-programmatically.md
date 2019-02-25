---
title: 'Vorgehensweise: Programmgesteuertes Senden von e-Mail-Adresse'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 280b4f526bad3e0ba646058b3e2410a98ca910fe
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646004"
---
# <a name="how-to-programmatically-send-email"></a>Vorgehensweise: Programmgesteuertes Senden von e-Mail-Adresse
  In diesem Beispiel sendet eine e-Mail, Kontakte, die den Domänennamen **"example.com"** ihre e-Mail-Adressen.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Beispiel benötigen Sie Folgendes:

-   Kontakte, die den Domänennamen **"example.com"** ihre e-Mail-Adressen.

## <a name="robust-programming"></a>Stabile Programmierung
 Entfernen Sie den Filtercode, der für den Domänennamen sucht nicht **"example.com"**. Ihre Lösung sendet e-Mail-Nachrichten an alle Kontakte, wenn Sie den Filter zu entfernen.

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit e-Mail-Elemente](../vsto/working-with-mail-items.md)
- [Vorgehensweise: Programmgesteuertes Erstellen von e-Mail-Elementen](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Vorgehensweise: Programmgesteuertes Zugreifen auf Outlook-Kontakte](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Vorgehensweise: Programmgesteuertes Ausführen von Aktionen beim Empfang einer e-Mail-Nachricht](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
