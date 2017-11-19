---
title: Object.Assign-Funktion (Objekt) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2dd6b312-dcd3-414e-8d53-088c6341c46d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c156369299e58eac556d43a87476de2ce09173e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="objectassign-function-object-javascript"></a>Object.assign-Funktion (Objekt) (JavaScript)
Kopiert die Werte aus einem oder mehreren Quellobjekten in ein Zielobjekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
Object.assign(target, ...sources );  
```  
  
#### <a name="parameters"></a>Parameter  
 `target`  
 Erforderlich. Ein Objekt, in das aufzählbare Eigenschaften kopiert werden.  
  
 `...sources`  
 Erforderlich. Ein oder mehrere Objekte, aus denen aufzählbare Eigenschaften kopiert werden.  
  
## <a name="exceptions"></a>Ausnahmen  
 Diese Funktion löst einen `TypeError` aus, wenn ein Zuweisungsfehler auftritt, durch den der Kopiervorgang beendet wird. Ein `TypeError` wird ausgelöst, wenn eine Zieleigenschaft schreibgeschützt ist.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion gibt das Zielobjekt zurück. Nur *enumerable own* Eigenschaften aus dem Quellobjekt in das Zielobjekt kopiert werden. Sie können diese Funktion verwenden, um Objekte zusammenzuführen oder zu klonen.  
  
 `null`- oder `undefined`-Quellen werden wie leere Objekte behandelt und leisten keinen Beitrag zum Zielobjekt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird die Zusammenführung eines Objekts mit `Object.assign` veranschaulicht.  
  
```JavaScript  
var first = { name: "Bob" };  
var last = { lastName: "Smith" };  
  
var person = Object.assign(first, last);  
console.log(person);  
  
// Output:  
// { name: "Bob", lastName: "Smith" }   
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das Klonen eines Objekts mit `Object.assign` veranschaulicht.  
  
```JavaScript  
var obj = { person: "Bob Smith"};  
var clone = Object.assign({}, obj);  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]