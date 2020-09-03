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
ms.openlocfilehash: da4ff08ae667b868670364c7ad6b9a6b69ae6ad3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815330"
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
 [Reguläres Ausdrucks Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax für reguläre Ausdrücke (JavaScript)](https://msdn.microsoft.com/library/1400241x)