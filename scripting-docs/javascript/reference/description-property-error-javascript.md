---
title: Description-Eigenschaft (Fehler) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Description
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error handling, error description
- Description property
- errors, description
ms.assetid: ea727f1e-2041-4400-965c-67e6d47a1ff0
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6135951fdf65698ed48b9bbacdcc55c1aac22d41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636360"
---
# <a name="description-property-error-javascript"></a>description-Eigenschaft (Eigenschaft) (JavaScript)
Gibt die beschreibende Zeichenfolge, die einem bestimmten Fehler zugeordnet ist, zurück oder legt diese fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.description [= stringExpression]  
```  
  
## <a name="parameters"></a>Parameter  
 *object*  
 Erforderlich. Jede Instanz von einem `Error` Objekt.  
  
 `stringExpression`  
 Dies ist optional. Ein Zeichenfolgenausdruck, der eine Beschreibung des Fehlers enthält.  
  
## <a name="remarks"></a>Hinweise  
 Die **Beschreibung** Eigenschaft enthält die Zeichenfolge der Fehlermeldung einen bestimmten Fehler zugeordnet. Verwenden Sie die in dieser Eigenschaft enthaltenen Wert um einen Benutzer auf einen Fehler hinzuweisen.  
  
 Die **Beschreibung** und **Nachricht** Eigenschaften bieten die gleiche Funktionalität; das **Beschreibung** Eigenschaft bietet Abwärtskompatibilität; das  **Nachricht** Eigenschaft entspricht dem ECMA-Standard.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **Beschreibung** Eigenschaft.  
  
```JavaScript  
try  
{  
// Cause an error:  
    x = y     
}  
catch(e)  
{  
// Prints "[object Error]":  
    document.write(e)  
    document.write (" ");  
// Prints 5009:  
    document.write((e.number & 0xFFFF))    
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.description);  
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.message)  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Gilt für**: [-Fehlerobjekt.](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Number-Eigenschaft (Fehler)](../../javascript/reference/number-property-error-javascript.md)   
 [Message-Eigenschaft (Fehler)](../../javascript/reference/message-property-error-javascript.md)   
 [name-Eigenschaft (Fehler)](../../javascript/reference/name-property-error-javascript.md)