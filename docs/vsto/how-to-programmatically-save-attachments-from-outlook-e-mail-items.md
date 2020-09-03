---
title: Programm gesteuertes Speichern von Anlagen von Outlook-e-Mails
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
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
ms.openlocfilehash: 9fbe6099a8928397a7d885ac72c4f34da2da6af0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545885"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Gewusst wie: Programm gesteuertes Speichern von Anlagen von Outlook-e-Mail

In diesem Beispiel werden E-Mail-Anlagen in einem angegebenen Ordner gespeichert, wenn die E-Mail im Posteingang eingeht.

> [!IMPORTANT]
> Dieses Beispiel funktioniert nur, wenn Sie im Stammverzeichnis des C-Verzeichnisses einen Ordner mit dem Namen **TestFileSave** hinzufügen.

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel

[!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]

## <a name="see-also"></a>Weitere Informationen

- [Arbeiten mit e-Mail-Elementen](../vsto/working-with-mail-items.md)
- [Gewusst wie: Programm gesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Gewusst wie: Programm gesteuertes Ausführen von Aktionen beim Empfang einer e-Mail-Nachricht](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [Gewusst wie: Programm gesteuertes suchen innerhalb eines bestimmten Ordners](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
