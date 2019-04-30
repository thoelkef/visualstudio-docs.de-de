---
title: 'Vorgehensweise: Programmgesteuertes Speichern von Anlagen von Outlook-e-Mail-Elementen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 874f19e0ae4e752a36ce95deab669ab46bfbf038
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419515"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Vorgehensweise: Programmgesteuertes Speichern von Anlagen von Outlook-e-Mail-Elementen
  In diesem Beispiel werden E-Mail-Anlagen in einem angegebenen Ordner gespeichert, wenn die E-Mail im Posteingang eingeht.

> [!IMPORTANT]
> Dieses Beispiel funktioniert nur, wenn Sie einen Ordner mit dem Namen hinzufügen **TestFileSave** im Stammverzeichnis c:.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit e-Mail-Elemente](../vsto/working-with-mail-items.md)
- [Vorgehensweise: Programmgesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Vorgehensweise: Programmgesteuertes Ausführen von Aktionen beim Empfang einer e-Mail-Nachricht](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [Vorgehensweise: Programmgesteuerte Suche in einem bestimmten Ordner](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
