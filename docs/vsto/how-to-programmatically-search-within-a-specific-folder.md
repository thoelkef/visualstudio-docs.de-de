---
title: 'Gewusst wie: Programm gesteuertes suchen innerhalb eines bestimmten Ordners'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f5e0f098edcffce07eb2c3f243b994d1a53cdf9
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547016"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Gewusst wie: Programm gesteuertes suchen innerhalb eines bestimmten Ordners
  In diesem Codebeispiel `Find` werden die `FindNext` -Methode und die-Methode verwendet, um Text im Feld Betreff von e-Mail-Nachrichten im **Posteingang**zu suchen. Diese Methode verwendet einen Zeichen folgen Filter, um den Buchstaben T als Anfangsbuchstaben des Texts zu überprüfen `Subject` .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Ordnern](../vsto/working-with-folders.md)
- [Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)
- [Gewusst wie: Programm gesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
