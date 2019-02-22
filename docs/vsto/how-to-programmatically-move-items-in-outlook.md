---
title: 'Vorgehensweise: Programmgesteuertes Verschieben von Elementen in Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 10b0f05e758f71830d5377c738ff9dee683022b8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641623"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Vorgehensweise: Programmgesteuertes Verschieben von Elementen in Outlook
  In diesem Beispiel verschiebt ungelesene e-Mail-Nachrichten aus der **Posteingang** in einen Ordner namens **Test**. Im Beispiel wird nur die Nachrichten, die das Wort **Test** in die `Subject` Feld.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Beispiel benötigen Sie Folgendes:

-   Ein Outlook-Ordner mit dem Namen **Test**.

-   Eine e-Mail-Nachricht, die mit dem Wort eingeht **Test** in die `Subject` Feld.

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Ordnern](../vsto/working-with-folders.md)
- [Vorgehensweise: Programmgesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Vorgehensweise: Programmgesteuerte Suche in einem bestimmten Ordner](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Vorgehensweise: Programmgesteuertes Ausführen von Aktionen beim Empfang einer e-Mail-Nachricht](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
