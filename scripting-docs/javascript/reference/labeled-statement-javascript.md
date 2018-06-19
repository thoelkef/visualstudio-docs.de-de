---
title: Mit der Bezeichnung Anweisung (JavaScript) | Microsoft Docs
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
- labeled_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- continue statement
- labeled statement
- identifiers, statements
ms.assetid: 019f898e-9e27-4be4-a22f-c5927c7fcae2
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd72b15d3fc9083ca127a48981c0cd0a7ee56b6c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637600"
---
# <a name="labeled-statement-javascript"></a>Anweisung mit Bezeichnung (JavaScript)
Stellt einen Bezeichner für eine Anweisung bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      label :  
   statements   
```  
  
## <a name="parameters"></a>Parameter  
 *Bezeichnung*  
 Erforderlich. Ein eindeutiger Bezeichner verwendet, wenn die Anweisung mit Bezeichnung.  
  
 `statements`  
 Dies ist optional. Eine oder mehrere Anweisungen, die zugeordneten *Bezeichnung*.  
  
## <a name="remarks"></a>Hinweise  
 Bezeichnungen werden verwendet, indem Sie die **Break** und **weiterhin** Anweisungen an die Anweisung, die **Break** und **weiterhin** anwenden.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Code die **weiterhin** Anweisung verweist auf die **für** Schleife, in der vorangestellt ist die `Inner:` Anweisung. Wenn `j` beträgt 24, die **weiterhin** Anweisung verursacht, die **für** -Schleife zur nächsten Iteration wechseln. Die Zahlen 21 bis 23 und 25 bis 30 Drucken in jeder Zeile.  
  
```JavaScript  
Outer:  
for (i = 1; i <= 10; i++) {  
   document.write ("<br />");  
   document.write ("i: " + i);  
   document.write (" j: ");  
  
Inner:  
   for (j = 21; j <= 30; j++) {  
      if (j == 24)  
          {  
          continue Inner;  
      }  
      document.write (j + " ");  
  }  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [break-Anweisung](../../javascript/reference/break-statement-javascript.md)   
 [continue-Anweisung](../../javascript/reference/continue-statement-javascript.md)