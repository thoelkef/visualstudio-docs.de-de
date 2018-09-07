---
title: 'Gewusst wie: programmgesteuerte Suche in einem bestimmten Ordner'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 64df4180e533f254927ae134ed005b0626dfdde8
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672912"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Gewusst wie: programmgesteuerte Suche in einem bestimmten Ordner
  Dieses Codebeispiel verwendet die `Find` und `FindNext` Methoden, um nach Text in der Betreffzeile von e-Mail-Nachrichten zu suchen, die in der **Posteingang**. Diese Methode verwendet eine Zeichenfolge um zu prüfen, der Buchstabe T Zeichenfolgenfilter ab, der die `Subject` Text.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Ordnern](../vsto/working-with-folders.md)   
 [Übersicht über Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)   
 [Gewusst wie: Programmgesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  