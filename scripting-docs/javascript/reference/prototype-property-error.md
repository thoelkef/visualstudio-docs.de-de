---
title: Prototype-Eigenschaft (Fehler) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 6c268a51-1a3d-4397-abf8-e54ca4e598fe
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7d0413d3541691a38672e7c0720b58245725b76
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639480"
---
# <a name="prototype-property-error"></a>prototype-Eigenschaft (Fehler)
Gibt einen Verweis auf den Prototyp für einen Fehler zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
error.prototype  
```  
  
## <a name="remarks"></a>Hinweise  
 Die `error` -Argument ist der Name eines Fehlers.  
  
 Verwenden der `prototype` Eigenschaft, um einen Basissatz an Funktionalität zu einem Fehler bereitzustellen. Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Um beispielsweise dem `Error`-Objekt eine Methode hinzuzufügen, die den Wert des größten Elements des Arrays zurückgibt, deklarieren Sie die Funktion, fügen Sie sie `Error.prototype` hinzu, und verwenden Sie sie dann.  
  
```JavaScript  
function getSeverity(){  
    if (this.number > 1000)  
        return "high";  
    else  
        return "low";  
}  
Error.prototype.getSev = getSeverity;  
var myError = new Error();  
myError.number = 5000;  
  
document.write(myError.getSev());   
  
// Output: high  
  
```  
  
 Alle systeminternen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekte verfügen über eine `prototype` -Eigenschaft, die schreibgeschützt ist. Eigenschaften und Methoden auf den Prototyp hinzugefügt werden, aber das Objekt möglicherweise nicht anderen Prototyp zugewiesen werden. Jedoch können benutzerdefinierte Objekte als einen neuen Prototyp zugewiesen werden.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]