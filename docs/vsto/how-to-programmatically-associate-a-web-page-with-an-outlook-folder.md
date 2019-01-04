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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1950a75eeee6f99a03346dde53317b30824a35f4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990658"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Vorgehensweise: Programmgesteuertes Zuordnen einer Webseite zu einem Outlook-Ordner
  In diesem Beispiel wird überprüft, für einen Ordner mit dem Namen `HtmlView` in Microsoft Office Outlook. Wenn der Ordner nicht vorhanden ist, wird der Code erstellt den Ordner, und weist sie eine Webseite. Wenn der Ordner vorhanden ist, zeigt den Code der Inhalt des Ordners an.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Ordnern](../vsto/working-with-folders.md)   
 [Vorgehensweise: Programmgesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Vorgehensweise: Programmgesteuertes Erstellen von benutzerdefinierten Ordnerelementen](../vsto/how-to-programmatically-create-custom-folder-items.md)  
