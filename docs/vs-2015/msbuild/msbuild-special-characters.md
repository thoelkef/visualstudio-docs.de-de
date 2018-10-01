---
title: MSBuild-Sonderzeichen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fcbafb43a059221e5572c9c807cadfdefe68134
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514734"
---
# <a name="msbuild-special-characters"></a>MSBuild-Sonderzeichen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [MSBuild-Sonderzeichen](https://docs.microsoft.com/visualstudio/msbuild/msbuild-special-characters).  
  
  
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



