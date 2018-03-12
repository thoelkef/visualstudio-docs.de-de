---
title: "Funktion enthält kein gültiges Prototype-Objekt. | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4e2cbf198a452cd61f1355682ea3041436d2a27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Funktion enthält kein gültiges prototype-Objekt.
Sie haben versucht, **Instanceof** zu bestimmen, ob ein Objekt von einer bestimmten Funktion-Klasse abgeleitet wurde, aber Sie des Objekts neu `prototype` Eigenschaft entweder als `null`, oder einen externen Typ (beide ungültig [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekte). Ein externes Objekt möglich ein Objekt aus dem Host-Objektmodell (z. B. Internet Explorer Dokument oder -Fensterobjekt) oder einer externen COM-Objekts.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Gewährleisten Sie der Funktion `prototype` Eigenschaft bezieht sich auf eine gültige [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [Function-Objekt](../../javascript/reference/function-object-javascript.md)   
 [prototype-Eigenschaft (Objekt)](../../javascript/reference/prototype-property-object-javascript.md)