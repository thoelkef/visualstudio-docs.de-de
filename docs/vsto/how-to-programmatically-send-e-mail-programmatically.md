---
title: 'Gewusst wie: Programm gesteuertes Senden von e-Mails'
ms.date: 08/14/2019
ms.topic: how-to
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
ms.openlocfilehash: c56527f18857ad3c4ac82060ffd5794b72ac017c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543259"
---
# <a name="how-to-programmatically-send-email"></a>Gewusst wie: Programm gesteuertes Senden von e-Mails
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

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit e-Mail-Elementen](../vsto/working-with-mail-items.md)
- [Gewusst wie: Programm gesteuertes Erstellen eines e-Mail-Elements](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Gewusst wie: Programm gesteuertes zugreifen auf Outlook-Kontakte](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Gewusst wie: Programm gesteuertes Ausführen von Aktionen beim Empfang einer e-Mail-Nachricht](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
