---
title: 'Vorgehensweise: Programmgesteuertes Senden von E-Mails | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f8681fecf8dc2d4c3a26aeaeb372faeb57e54094
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-send-e-mail"></a>Vorgehensweise: Programmgesteuertes Senden von E-Mails  
  In diesem Beispiel sendet eine e-Mail, Kontakte, der Domänenname ist **example.com** in ihren e-Mail-Adressen.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Für dieses Beispiel benötigen Sie Folgendes:  
  
-   Kontakte, der Domänenname ist **example.com** in ihren e-Mail-Adressen.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Entfernen Sie den Filtercode, der für den Domänennamen sucht nicht **example.com**. Die Projektmappe sendet e-Mail-Nachrichten an alle Kontakte, wenn Sie den Filter zu entfernen.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit e-Mail-Elemente](../vsto/working-with-mail-items.md)   
 [Vorgehensweise: Programmgesteuertes Erstellen von e-Mail-Elementen](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Vorgehensweise: programmgesteuerten Zugriff auf Outlook-Kontakten](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Vorgehensweise: Programmgesteuertes Ausführen von Aktionen beim Empfang einer E-Mail-Nachricht](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  