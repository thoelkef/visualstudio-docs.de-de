---
title: Die Funktion weist kein gültiges Prototypobjekt auf. Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: cb3cffa4bffd616560aa95ace4ad82a4368ebbd5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574605"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Funktion enthält kein gültiges prototype-Objekt.
Sie haben versucht, mit **instanceof** festzustellen, ob ein Objekt von einer bestimmten Funktionsklasse abgeleitet wurde, aber Sie haben die `prototype`-Eigenschaft des Objekts entweder als `null`oder als externen Objekttyp (sowohl ungültige [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekte) neu definiert. Bei einem externen Objekt kann es sich um ein Objekt aus dem Host Objektmodell (z. b. das Dokument-oder Fenster Objekt von Internet Explorer) oder ein externes com-Objekt handeln.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass sich die `prototype`-Eigenschaft der Funktion auf ein gültiges [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekt bezieht.  
  
## <a name="see-also"></a>Siehe auch  
 [Funktions Objekt](../../javascript/reference/function-object-javascript.md)   
 [prototype-Eigenschaft (Objekt)](../../javascript/reference/prototype-property-object-javascript.md)