---
title: 'Vorgehensweise: Programmgesteuertes Zuordnen einer Webseite zu einem Outlook-Ordner'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e83f8b7f6bcdb790b5e545aa76426bc05f0735f5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56604299"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Vorgehensweise: Programmgesteuertes Zuordnen einer Webseite zu einem Outlook-Ordner
  In diesem Beispiel wird überprüft, für einen Ordner mit dem Namen `HtmlView` in Microsoft Office Outlook. Wenn der Ordner nicht vorhanden ist, wird der Code erstellt den Ordner, und weist sie eine Webseite. Wenn der Ordner vorhanden ist, zeigt den Code der Inhalt des Ordners an.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Ordnern](../vsto/working-with-folders.md)
- [Vorgehensweise: Programmgesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Vorgehensweise: Programmgesteuertes Erstellen von benutzerdefinierten Ordnerelementen](../vsto/how-to-programmatically-create-custom-folder-items.md)
