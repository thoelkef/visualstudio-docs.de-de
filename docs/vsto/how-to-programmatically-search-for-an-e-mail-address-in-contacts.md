---
title: 'Gewusst wie: programmgesteuerte Suche einer e-Mail-Adresse in den Kontakten'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e7b9c4c7d02f3cd1564e6733c46cb821eade7f54
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673704"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>Gewusst wie: programmgesteuerte Suche einer e-Mail-Adresse in den Kontakten
  In diesem Beispiel wird ein Kontaktordner nach Kontakten durchsucht, die den Domänennamen **example.com** in ihren E-Mail-Adressen aufweisen.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 Für dieses Beispiel benötigen Sie Folgendes:  
  
-   Kontakte mit dem Domänennamen **example.com** in ihren E-Mail-Adressen (z. B. `somebody@example.com`), die einen Vor- und Nachnamen aufweisen.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Kontaktelementen](../vsto/working-with-contact-items.md)   
 [Gewusst wie: Programmgesteuertes Senden von e-Mail-Adresse](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [Gewusst wie: Programmgesteuertes Zugreifen auf Outlook-Kontakte](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Gewusst wie: Programmgesteuertes Hinzufügen eines Eintrags zu Outlook-Kontakten](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
  
  