---
title: MSBuild-Sonderzeichen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a54f446cb82b3181ee057d4887b37940868a5920
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150764"
---
# <a name="msbuild-special-characters"></a>MSBuild-Sonderzeichen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] reserviert einige Zeichen für die besondere Verwendung in bestimmten Kontexten. Sie müssen diese Zeichen nur mit einem Escapezeichen versehen, wenn Sie sie in dem für sie reservierten Kontext in ihrer ursprünglichen Bedeutung verwenden möchten. Beispielsweise hat ein Sternchen nur in den Attributen `Include` und `Exclude` einer Elementdefinition und im Zusammenhang mit Aufrufen von `CreateItem` eine besondere Bedeutung. Wenn aber ein Sternchen in diesen Kontexten wirklich als Sternchen angezeigt werden soll, müssen Sie es mit einem Escapezeichen versehen. In allen anderen Kontexten müssen Sie lediglich auf die Sternchentaste drücken, wenn ein Sternchen angezeigt werden soll.  
  
 Verwenden Sie die Syntax %*xx*, um ein Sonderzeichen mit einem Escapezeichen zu versehen, wobei *xx* den Hexadezimalwert des ASCII-Zeichens darstellt. Weitere Informationen finden Sie unter [Vorgehensweise: Escapesonderzeichen in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## <a name="special-characters"></a>Sonderzeichen  
 In der folgenden Tabelle werden Sonderzeichen für [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] aufgeführt:  
  
|**Zeichen**|**ASCII**|**Reservierte Nutzung**|  
|-------------------|---------------|------------------------|  
|%|%25|Verweisen auf Metadaten|  
|$|%24|Verweisen auf Eigenschaften|  
|@|%40|Verweisen auf Elementlisten|  
|'|%27|Bedingungen und andere Ausdrücke|  
|;|%3B|Listentrennzeichen|  
|?|%3F|Platzhalterzeichen für Dateinamen in `Include`- und `Exclude`-Attributen|  
|*|%2A|Platzhalterzeichen für Dateinamen in `Include`- und `Exclude`-Attributen|  
  
## <a name="see-also"></a>Siehe auch  
 [Advanced Concepts (Weiterführende Konzepte)](../msbuild/msbuild-advanced-concepts.md)   
 [Elemente](../msbuild/msbuild-items.md)
