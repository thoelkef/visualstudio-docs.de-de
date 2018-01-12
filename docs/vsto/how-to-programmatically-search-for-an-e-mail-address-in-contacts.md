---
title: 'Vorgehensweise: programmgesteuerte Suche einer e-Mail-Adresse in den Kontakten | Microsoft Docs'
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
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d9ab451d433536c7ebf5931aa2c971b08ed5c09b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-search-for-an-e-mail-address-in-contacts"></a>Gewusst wie: Programmgesteuerte Suche einer E-Mail-Adresse in den Kontakten
  In diesem Beispiel wird ein Kontaktordner nach Kontakten durchsucht, die den Domänennamen **example.com** in ihren E-Mail-Adressen aufweisen.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Für dieses Beispiel benötigen Sie Folgendes:  
  
-   Kontakte mit dem Domänennamen **example.com** in ihren E-Mail-Adressen (z. B. `somebody@example.com`), die einen Vor- und Nachnamen aufweisen.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Kontaktelementen](../vsto/working-with-contact-items.md)   
 [Vorgehensweise: Programmgesteuertes Senden von E-Mails](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [Vorgehensweise: programmgesteuerten Zugriff auf Outlook-Kontakten](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Vorgehensweise: Programmgesteuertes Hinzufügen eines Eintrags zu Outlook-Kontakten](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
  
  