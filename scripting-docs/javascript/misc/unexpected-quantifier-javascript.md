---
title: Unerwarteter Quantifizierer (JavaScript) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef0955bac35009d9b6c82f1856bb9005a08043ad
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282262"
---
# <a name="unexpected-quantifier-javascript"></a>Unerwarteter Quantifizierer (JavaScript)
Beim Verfassen Ihrer Musters für reguläre Ausdrücke suchen, haben Sie ein Muster-Element mit einem Faktor unzulässige Wiederholung erstellt. Zum Beispiel das Muster  
  
```  
/^+/  
```  
  
 ist nicht zulässig da das Element ^ (Beginn der Eingabe) sind keine Wiederholung Faktor. Die folgende Tabelle enthält die Elemente, die Wiederholung Faktoren haben können.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|^|Beginn der Eingabe|  
|$|Ende der Eingabe|  
|\b|Wortgrenze|  
|\B|Nicht-Wortgrenze|  
|*|NULL oder mehr Wiederholungen|  
|+|Eine oder mehrere Wiederholungen|  
|?|NULL oder einem Wiederholungen|  
|{n}|n Wiederholungen|  
|{n}|n oder mehrere Wiederholungen|  
|{n, m}|Von n bis m Wiederholungen, inklusive|  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass Ihre Suche Muster-Element nur zulässige Wiederholung Faktoren enthält.  
  
## <a name="see-also"></a>Siehe auch  
 [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax für reguläre Ausdrücke (JavaScript)](https://msdn.microsoft.com/library/1400241x)