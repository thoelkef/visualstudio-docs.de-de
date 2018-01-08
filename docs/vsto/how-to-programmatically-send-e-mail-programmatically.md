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
ms.assetid: 4fa0e1b5-2caf-4a11-8626-df643b23f5f0
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 39a0ebee37c57630649f680d14aa8fef22833225
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
  
  