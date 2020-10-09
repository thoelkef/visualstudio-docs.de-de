---
title: Unerwarteter Quantifizierer (JavaScript) | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: f67f9a2fc81b0bd950e171e4274eb09eacd88bbc
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861846"
---
# <a name="unexpected-quantifier-javascript"></a>Unerwarteter Quantifizierer (JavaScript)
Wenn Sie das Suchmuster für reguläre Ausdrücke erstellen, haben Sie ein pattern-Element mit einem ungültigen Wiederholungs Faktor erstellt. Beispielsweise ist das Muster  
  
```js
/^+/  
```  
  
 ist unzulässig, da das Element ^ (Anfang der Eingabe) keinen Wiederholungs Faktor aufweisen darf. In der folgenden Tabelle werden die Elemente aufgelistet, die keine Wiederholungs Faktoren aufweisen können.  
  
|Element|BESCHREIBUNG|  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Reguläres Ausdrucks Objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Syntax für reguläre Ausdrücke (JavaScript)](/previous-versions/1400241x(v=vs.100))