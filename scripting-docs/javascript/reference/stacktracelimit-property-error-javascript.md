---
title: StackTraceLimit-Eigenschaft (Fehler) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Error.stackTraceLimit
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error stack track limit [JavaScript]
- JavaScript error stack
- error stack [JavaScript]
- JavaScript stack trace limit
ms.assetid: 127ef8e8-892e-4263-9ebc-03364af01212
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9af736ee8b385f93b761f1dfa021c23ee5376292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="stacktracelimit-property-error-javascript"></a>stackTraceLimit-Eigenschaft (Fehler) (JavaScript)
Abrufen oder Festlegen der stapelüberwachungslimit, entspricht die Anzahl der Fehler angezeigt. Die Standardgrenze ist 10.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Error  
.stackTraceLimit   
```  
  
## <a name="remarks"></a>Hinweise  
 Sie können festlegen, die `stackTraceLimit` Eigenschaft zu einem positiven Wert zwischen 0 und `Infinity`. Wenn die `stackTraceLimit` Eigenschaftensatz wird auf 0 zu dem Zeitpunkt ein Fehler ausgelöst wird, wird keine stapelüberwachung angezeigt. Wenn die Eigenschaft auf einen negativen Wert oder einen nicht numerischen Wert festgelegt ist, wird der Wert in 0 konvertiert. Wenn die StackTraceLimit, um festgelegt ist `Infinity`, der gesamte Stapel wird angezeigt. Andernfalls `ToUint32` wird verwendet, um den Wert zu konvertieren.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel veranschaulicht das Festlegen und anschließend die stapelüberwachungslimit abrufen.  
  
```JavaScript  
try  
    {  
    var err = new Error("my error");  
    Error.stackTraceLimit = 7;  
    throw err;  
    }  
catch(e)  
    {  
    document.write ("Error stack trace limit: ")  
    document.write (Error.stackTraceLimit);  
    }  
```  
  
## <a name="requirements"></a>Anforderungen  
 Unterstützt in InternetExplorer 10 und [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] apps.  
  
 **Gilt für**: [-Fehlerobjekt.](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Description-Eigenschaft (Fehler)](../../javascript/reference/description-property-error-javascript.md)   
 [Message-Eigenschaft (Fehler)](../../javascript/reference/message-property-error-javascript.md)   
 [Name-Eigenschaft (Fehler)](../../javascript/reference/name-property-error-javascript.md)   
 [stack-Eigenschaft (Fehler)](../../javascript/reference/stack-property-error-javascript.md)