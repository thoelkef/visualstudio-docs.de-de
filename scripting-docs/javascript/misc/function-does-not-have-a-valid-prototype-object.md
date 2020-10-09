---
title: Die Funktion weist kein gültiges Prototypobjekt auf. Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15b00087cd66b873044b7bafb1bfecf4fc91f8d9
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862400"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Funktion enthält kein gültiges prototype-Objekt.
Sie haben versucht, mit **instanceof** festzustellen, ob ein Objekt von einer bestimmten Funktionsklasse abgeleitet wurde, aber Sie haben die-Eigenschaft des Objekts `prototype` entweder als `null` oder als externen Objekttyp (sowohl ungültige [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekte) neu definiert. Bei einem externen Objekt kann es sich um ein Objekt aus dem Host Objektmodell (z. b. das Dokument-oder Fenster Objekt von Internet Explorer) oder ein externes com-Objekt handeln.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass die-Eigenschaft der Funktion `prototype` auf ein gültiges [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekt verweist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Function-Objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [prototype-Eigenschaft (Objekt)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)