---
title: Unerwarteter Quantifizierer (JavaScript) | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2070ec6ad01eb62c6be9b6b9acfc91cba7bc863d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572538"
---
# <a name="unexpected-quantifier-javascript"></a>Unerwarteter Quantifizierer (JavaScript)
Wenn Sie das Suchmuster für reguläre Ausdrücke erstellen, haben Sie ein pattern-Element mit einem ungültigen Wiederholungs Faktor erstellt. Beispielsweise ist das Muster  
  
```js
/^+/  
```  
  
 ist unzulässig, da das Element ^ (Anfang der Eingabe) keinen Wiederholungs Faktor aufweisen darf. In der folgenden Tabelle werden die Elemente aufgelistet, die keine Wiederholungs Faktoren aufweisen können.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|^|Beginn der Eingabe|  
|$|Ende der Eingabe|  
|\b|Wort Grenze|  
|\B|Nicht-Wort Grenze|  
|*|NULL oder mehr Wiederholungen|  
|+|Mindestens eine Wiederholung|  
|?|Keine oder eine Wiederholung|  
|Nr|n Wiederholungen|  
|{n,}|n oder mehr Wiederholungen|  
|{n, m}|Von n bis m Wiederholungen, einschließlich|  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass das Suchmuster Element nur rechtliche Wiederholungs Faktoren enthält.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekt für reguläre Ausdrücke](../../javascript/reference/regular-expression-object-javascript.md)    
 [Syntax für reguläre Ausdrücke (JavaScript)](https://msdn.microsoft.com/library/1400241x)