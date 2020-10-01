---
title: Zuordnen einer Webseite zu einem Outlook-Ordner
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 35eb2dc3b1b595a4bf960af67ac5006cd9839c6e
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585339"
---
# <a name="associate-a-web-page-with-an-outlook-folder"></a>Zuordnen einer Webseite zu einem Outlook-Ordner

  In diesem Beispiel wird in Microsoft Office Outlook nach einem Ordner mit dem Namen gesucht `HtmlView` . Wenn der Ordner nicht vorhanden ist, erstellt der Code den Ordner und weist ihm eine Webseite zu. Wenn der Ordner vorhanden ist, zeigt der Code die Ordnerinhalte an.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Ordnern](../vsto/working-with-folders.md)
- [Gewusst wie: Programm gesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Gewusst wie: Programm gesteuertes Erstellen von benutzerdefinierten Ordner Elementen](../vsto/how-to-programmatically-create-custom-folder-items.md)
