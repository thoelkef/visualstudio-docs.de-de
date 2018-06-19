---
title: Stack-Eigenschaft (Fehler) (JavaScript) | Microsoft Docs
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
- Error.stack
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript error stack
- error stack [JavaScript]
ms.assetid: 1dc21fdd-853c-4664-bf1c-24eb1f6f2daf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14e4a2537b1543b7e8d9727afdeb8ea5dee61bbc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641140"
---
# <a name="stack-property-error-javascript"></a>stack-Eigenschaft (Fehler) (JavaScript)
Ruft den Fehlerstapel als Zeichenfolge ab oder legt ihn fest, der die Stapelüberwachungsrahmen enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.stack   
```  
  
## <a name="remarks"></a>Hinweise  
 Die `stack` -Eigenschaft wird auf `undefined` festgelegt, wenn der Fehler generiert wird, und er ruft die Ablaufverfolgungsinformationen ab, wenn der Fehler ausgelöst wird. Wenn ein Fehler mehrere Male ausgelöst wird, wird die `stack`Eigenschaft bei jedem Auslösen des Fehlers aktualisiert.  
  
 Stapelrahmen werden im folgenden Format angezeigt: **am Funktionsname (\<voll gekennzeichneter Name/URL >:\<Zeilennummer >:\<Spaltennummer >)**  
  
 Wenn Sie Ihr eigenes Fehlerobjekt erstellen und die Stapelüberwachung auf einen Wert festlegen, wird der Wert beim Auslösen des Fehlers nicht überschrieben.  
  
 Die `stack`-Eigenschaft zeigt im Rahmen keine Inlinefunktionen an  Es zeigt nur den physischen Stapel an.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie den Stapel abrufen können, wenn Sie einen Fehler feststellen.  
  
```JavaScript  
try  
    {  
        var x = y.name;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie den Stapel festlegen und anschließend abrufen können.  
  
```JavaScript  
try  
    {  
        var err = Error("my error");  
        err.stack = "my stack trace";  
        throw err;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]  
  
 **Gilt für**: [-Fehlerobjekt.](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Description-Eigenschaft (Fehler)](../../javascript/reference/description-property-error-javascript.md)   
 [Message-Eigenschaft (Fehler)](../../javascript/reference/message-property-error-javascript.md)   
 [Name-Eigenschaft (Fehler)](../../javascript/reference/name-property-error-javascript.md)   
 [stackTraceLimit-Eigenschaft (Fehler)](../../javascript/reference/stacktracelimit-property-error-javascript.md)