---
title: Number-Eigenschaft (Fehler) (JavaScript) | Microsoft Docs
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
- Number
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Number property
ms.assetid: 8697e20b-a2b0-4e26-85c0-ab07ddfe8281
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbc229e7d0572e1a3dbed056b344da7ff9ce7292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639100"
---
# <a name="number-property-error-javascript"></a>number-Eigenschaft (Fehler) (JavaScript)
Gibt den numerischen Wert zurück, der einem bestimmten Fehler zugewiesen ist, bzw. legt diesen fest. Die `Error` Standardeigenschaft des Objekts ist **Anzahl**.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.number [= errorNumber]  
```  
  
## <a name="parameters"></a>Parameter  
 *Objekt*  
 Jede Instanz von der `Error` Objekt.  
  
 *Fehlernummer*  
 Eine ganze Zahl, die einen Fehler darstellt.  
  
## <a name="remarks"></a>Hinweise  
 Eine Fehlernummer ist ein 32-Bit-Wert. Das obere 16-Bit-Wort ist der Einrichtungscode, und das untere Wort ist der Fehlercode. Fehlercode: Ermitteln Sie mithilfe der `&` (bitweises und) Operator, um die Eigenschaft Number mit der Hexadezimalzahl kombinieren `0xFFFF`.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird eine Ausnahme ausgelöst werden und zeigt den Fehlercode, der die Nummer des Fehlers abgeleitet ist.  
  
```JavaScript  
try  
    {  
    // Cause an error.  
    var x = y;  
    }  
catch(e)  
    {  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
  
    document.write ("Facility Code: ")  
    document.write(e.number>>16 & 0x1FFF)  
    document.write ("<br />");  
  
    document.write ("Error Message: ")  
    document.write (e.message)  
    }  
```  
  
## <a name="example"></a>Beispiel  
 Die Ausgabe dieses Codes lautet wie folgt.  
  
```JavaScript  
Error Code: 5009  
Facility Code: 10  
Error Message: 'y' is undefined  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Gilt für**: [-Fehlerobjekt.](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Description-Eigenschaft (Fehler)](../../javascript/reference/description-property-error-javascript.md)   
 [Message-Eigenschaft (Fehler)](../../javascript/reference/message-property-error-javascript.md)   
 [name-Eigenschaft (Fehler)](../../javascript/reference/name-property-error-javascript.md)