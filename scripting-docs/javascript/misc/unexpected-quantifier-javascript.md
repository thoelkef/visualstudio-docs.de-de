---
title: Unerwarteter Quantifizierer (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb6d6d3129057c399dd7369c6f69eb7396f07ab4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="unexpected-quantifier-javascript"></a>Unerwarteter Quantifizierer (JavaScript)
Beim Verfassen Ihre Suche Musters eines regulären Ausdrucks, haben Sie ein Muster-Element mit einer unzulässige Wiederholung Authentifizierungsstufe erstellt. Zum Beispiel das Muster  
  
```  
/^+/  
```  
  
 ist nicht zulässig da das Element ^ (Anfang Eingabe) sind keine Wiederholung Faktor. Die folgende Tabelle enthält die Elemente, die Wiederholung Faktoren haben dürfen.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|^|Der Anfang der Eingabe|  
|$|Ende der Eingabe|  
|\b|Wortgrenze|  
|\B|Nicht-Wortgrenze|  
|*|NULL oder mehr Wiederholungen|  
|+|Eine oder mehrere Wiederholungen|  
|?|NULL oder eins Wiederholungen|  
|{n}|n Wiederholungen|  
|{n}|n oder weitere Wiederholungen|  
|{n, m}|Von n zu m Wiederholungen, inklusive|  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass Ihre Suche Muster Element nur zulässige Wiederholung Faktoren enthält.  
  
## <a name="see-also"></a>Siehe auch  
 [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax regulärer Ausdrücke (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)