---
title: Prototype-Eigenschaft (Datum) | Microsoft Docs
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
ms.assetid: 44f9c637-7da7-4833-906d-358506f32ced
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c0b337964d2a2fe17a4e9a7906d81069470e61b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-date"></a>prototype-Eigenschaft (Datum)
Gibt einen Verweis auf den Prototyp für ein Datum zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
date.prototype  
```  
  
## <a name="remarks"></a>Hinweise  
 Das `date`-Argument ist der Name eines Objekts.  
  
 Verwenden der `prototype` Eigenschaft, um auf ein Datum einen Basissatz an Funktionalität bereitzustellen. Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Um beispielsweise dem `Date`-Objekt eine Methode hinzuzufügen, die den Wert des größten Elements des Arrays zurückgibt, deklarieren Sie die Funktion, fügen Sie sie `Date.prototype` hinzu, und verwenden Sie sie dann.  
  
```JavaScript  
function max( ){  
    var max = new Date();  
    max.setFullYear(2200, 01, 01);  
    return max;  
}  
Date.prototype.maxDate = max;  
var myDate = new Date();  
  
if (myDate < myDate.maxDate())  
    document.write("today isn't the max");  
else if (myDate == myDate.maxDate())  
    document.write("today is the max");   
  
// Output:  
// today isn't the max  
  
```  
  
 Alle systeminternen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekte verfügen über eine `prototype` -Eigenschaft, die schreibgeschützt ist. Eigenschaften und Methoden auf den Prototyp hinzugefügt werden, aber das Objekt möglicherweise nicht anderen Prototyp zugewiesen werden. Jedoch können benutzerdefinierte Objekte als einen neuen Prototyp zugewiesen werden.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]