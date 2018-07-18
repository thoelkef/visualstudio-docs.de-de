---
title: 'Gewusst wie: Programmgesteuertes Bestimmen des aktuellen Outlook-Elements'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 519fd1572b3ebb1faf8cc7adc6d5a9ba2773d67b
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257042"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Gewusst wie: Programmgesteuertes Bestimmen des aktuellen Outlook-Elements
  Dieses Beispiel verwendet die `Explorer.SelectionChange` Ereignis, um den Namen des aktuellen Ordners und einige Informationen über das ausgewählte Element anzuzeigen. Der Code zeigt das ausgewählte Element.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Beispiel  
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 Für dieses Beispiel benötigen Sie Folgendes:  
  
-   Termin, wenden Sie sich an und e-Mail-Elemente in Microsoft Office Outlook.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)   
 [Gewusst wie: Programmgesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Gewusst wie: Programmgesteuertes Suchen eines bestimmten Kontakts](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
  
  