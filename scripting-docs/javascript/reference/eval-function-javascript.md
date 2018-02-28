---
title: Eval-Funktion (JavaScript) | Microsoft Docs
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
- eval
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- eval function
- parsing, code
- parser
ms.assetid: 85587e39-9325-4b75-b9f9-9d7d475a2120
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 388e486f58bb70fd192701060a5faefaed8bd98e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="eval-function-javascript"></a>eval-Funktion (JavaScript)
Wertet [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] code und führt ihn aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
eval(codeString)   
```  
  
## <a name="parameters"></a>Parameter  
 `codeString`  
 Erforderlich. Ein `String` Wert, der gültige enthält [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Code.  
  
## <a name="remarks"></a>Hinweise  
 Die `eval` -Funktion ermöglicht die dynamische Ausführung von [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Quellcode.  
  
 Die `codeString` Zeichenfolge analysiert wird, werden die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Parser und ausgeführt.  
  
 Der Code übergeben wird, um die `eval` Funktion ausgeführt wird, in demselben Kontext wie der Aufruf von der `eval` Funktion.  
  
 Verwenden Sie nach Möglichkeit die [JSON.parse-Funktion](../../javascript/reference/json-parse-function-javascript.md) JavaScript Object Notation (JSON) Text deserialisiert werden. Die `JSON.parse` Funktion besser geschützt und wird schneller ausgeführt als die `eval` Funktion.  
  
## <a name="example"></a>Beispiel  
 Der folgende Code initialisiert die Variable `myDate` in ein Testdatum.  
  
```JavaScript  
var dateFn = "Date(1971,3,8)";  
var myDate;  
eval("myDate = new " + dateFn + ";");  
  
document.write(myDate);  
  
// Output: Thu Apr 8 00:00:00 PDT 1971  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Global-Objekt](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [String-Objekt](../../javascript/reference/string-object-javascript.md)