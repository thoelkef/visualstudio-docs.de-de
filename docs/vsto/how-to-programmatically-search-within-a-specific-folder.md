---
title: 'Vorgehensweise: programmgesteuerte Suche in einem bestimmten Ordner | Microsoft Docs'
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
ms.openlocfilehash: aedddb0eab79e66d9d5a41d70a4907a2f22951ab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Gewusst wie: Programmgesteuerte Suche in einem bestimmten Ordner
  Dieses Codebeispiel verwendet die `Find` und `FindNext` Methoden zum Suchen nach Text in der Betreffzeile der e-Mail-Nachrichten, die in der **Posteingang**. Diese Methode verwendet eine Zeichenfolge um zu suchende Buchstaben T als die ersten Buchstaben des der `Subject` Text.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Ordnern](../vsto/working-with-folders.md)   
 [Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)   
 [Vorgehensweise: Programmgesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  