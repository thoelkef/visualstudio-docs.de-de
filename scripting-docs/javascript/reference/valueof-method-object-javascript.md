---
title: ValueOf-Methode (Objekt) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: valueOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: valueOf method
ms.assetid: c555e38b-f451-4341-8fcd-4c8b02906a2c
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 677b56fd6fc142ce175b130d2f83291c1ac9535f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-object-javascript"></a>valueOf-Methode (Objekt) (JavaScript)
Gibt den einfachen Wert des angegebenen Objekts zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.valueOf( )  
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `object` Verweis ist einer systeminternen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekt.  
  
 Die `valueOf` Methode unterschiedlich definiert ist, für jede systeminterne [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekt.  
  
|Objekt|Rückgabewert|  
|------------|------------------|  
|Array|Gibt die Instanz des Arrays zurück.|  
|Boolesch|Der boolesche Wert.|  
|Datum|Die gespeicherte Zeit-Wert in Millisekunden seit Mitternacht des 1. Januar 1970 UTC.|  
|Funktion|Die Funktion selbst.|  
|Anzahl|Der numerische Wert.|  
|Objekt|Das Objekt selbst. Dies ist die Standardeinstellung.|  
|Zeichenfolge|Der Zeichenfolgenwert.|  
  
 Die **mathematische** und `Error` Objekte verfügen nicht über eine `valueOf` Methode.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **Gilt für**: [Array-Objekt](../../javascript/reference/array-object-javascript.md)&#124; [Boolean-Objekt](../../javascript/reference/boolean-object-javascript.md)&#124; [Datum Objekt](../../javascript/reference/date-object-javascript.md)&#124; [Funktion Objekt](../../javascript/reference/function-object-javascript.md)&#124; [Zahl Objekt](../../javascript/reference/number-object-javascript.md)&#124; [Object-Objekt](../../javascript/reference/object-object-javascript.md)&#124; [String-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [toString-Methode (Objekt)](../../javascript/reference/tostring-method-object-javascript.md)