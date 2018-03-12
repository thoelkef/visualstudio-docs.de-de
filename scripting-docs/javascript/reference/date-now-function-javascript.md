---
title: Date.Now-Funktion (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- now method
ms.assetid: 41beda89-1a40-4fb1-88b0-38c090af739b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41a098c55b8ced3c630d3724615835301b6f00c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="datenow-function-javascript"></a>Date.now-Funktion (JavaScript)
Ruft das aktuelle Datum und die Uhrzeit an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Date.now()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Die Anzahl der Millisekunden zwischen Mitternacht des 1. Januar 1970, und das aktuelle Datum und die Uhrzeit.  
  
## <a name="remarks"></a>Hinweise  
 Die [GetTime-Methode](../../javascript/reference/gettime-method-date-javascript.md) gibt die Anzahl der Millisekunden zwischen dem 1. Januar 1970 und dem angegebenen Datum.  
  
 Informationen zum Berechnen der verstrichenen Zeit, und Vergleichen von Datumsangaben finden Sie unter [berechnen von Datums- und Uhrzeitangaben (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `now`-Methode veranschaulicht.  
  
```JavaScript  
var start = Date.now();  
var response = prompt("What is your name?", "");  
var end = Date.now();  
var elapsed = (end - start) / 1000;  
document.write("You took " + elapsed + " seconds" + " to type: " + response);  
  
// Output:  
// You took <seconds> seconds to type: <name>  
```  
  
## <a name="requirements"></a>Anforderungen  
 Nicht unterstützt in installierten Versionen vor Internet Explorer 9. Es wird jedoch in den folgenden Dokumentmodi unterstützt: Quirksmodus, Internet Explorer 6-Standardmodus, Internet Explorer 7-Standardmodus, Internet Explorer 8-Standardmodus, Internet Explorer 9-Standardmodus, Internet Explorer 10 (Standardmodus). Wird auch unterstützt [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] apps.  
  
## <a name="see-also"></a>Siehe auch  
 [GetTime-Methode (Datum)](../../javascript/reference/gettime-method-date-javascript.md)   
 [Date-Objekt](../../javascript/reference/date-object-javascript.md)   
 [Berechnen von Datums- und Uhrzeitangaben (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [JavaScript-Methoden](../../javascript/reference/javascript-methods.md)