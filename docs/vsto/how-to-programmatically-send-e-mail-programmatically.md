---
title: 'Vorgehensweise: Programm gesteuertes Senden von e-Mails'
ms.date: 08/14/2019
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
ms.openlocfilehash: 72d033add2ba8320b14eebd5af700ab225d34410
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551754"
---
# <a name="how-to-programmatically-send-email"></a>Vorgehensweise: Programm gesteuertes Senden von e-Mails
  In diesem Beispiel wird eine e-Mail-Nachricht an Kontakte mit dem Domänen Namen **example.com** in Ihren e-Mail-Adressen gesendet.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Beispiel benötigen Sie Folgendes:

- Kontakte mit dem Domänen Namen **example.com** in Ihren e-Mail-Adressen.

## <a name="robust-programming"></a>Stabile Programmierung
 Entfernen Sie nicht den Filter Code, der nach dem Domänen Namen **example.com**sucht. Die Lösung sendet e-Mail-Nachrichten an alle Ihre Kontakte, wenn Sie den Filter entfernen.

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit e-Mail-Elementen](../vsto/working-with-mail-items.md)
- [Vorgehensweise: Programm gesteuertes Erstellen eines e-Mail-Elements](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Vorgehensweise: Programm gesteuertes zugreifen auf Outlook-Kontakte](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Vorgehensweise: Programm gesteuertes Ausführen von Aktionen beim Empfang einer e-Mail-Nachricht](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
