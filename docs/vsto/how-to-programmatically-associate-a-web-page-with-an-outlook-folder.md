---
title: 'Gewusst wie: Programm gesteuertes Zuordnen einer Webseite zu einem Outlook-Ordner'
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
ms.openlocfilehash: b8d44ffc46557243d2681b8f8b4a3b85d1cd9be6
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546145"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Gewusst wie: Programm gesteuertes Zuordnen einer Webseite zu einem Outlook-Ordner
  In diesem Beispiel wird in Microsoft Office Outlook nach einem Ordner mit dem Namen gesucht `HtmlView` . Wenn der Ordner nicht vorhanden ist, erstellt der Code den Ordner und weist ihm eine Webseite zu. Wenn der Ordner vorhanden ist, zeigt der Code die Ordnerinhalte an.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Ordnern](../vsto/working-with-folders.md)
- [Gewusst wie: Programm gesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Gewusst wie: Programm gesteuertes Erstellen von benutzerdefinierten Ordner Elementen](../vsto/how-to-programmatically-create-custom-folder-items.md)
