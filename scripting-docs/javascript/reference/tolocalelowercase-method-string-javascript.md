---
title: ToLocaleLowerCase-Methode (String) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLocaleLowerCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLocaleLowerCase method
ms.assetid: add894d3-d14a-4dbc-a9b9-7ad1d3a2e581
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 642ced387e0d3b4cf763767ec147d6160ed7d36b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalelowercase-method-string-javascript"></a>toLocaleLowerCase-Methode (String) (JavaScript)
Wandelt alle Buchstaben in Kleinbuchstaben Berücksichtigung aktuellen Gebietsschemas der hostumgebung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
stringVar.toLocaleLowerCase( )  
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `stringVar` Verweis ist ein `String` -Objekt oder Zeichenfolgenliteral.  
  
 Die `toLocaleLowerCase` Methode konvertiert Zeichen in eine Zeichenfolge, die Berücksichtigung aktuellen Gebietsschemas der hostumgebung. In den meisten Fällen das Ergebnis entspricht dem als Ergebnis der `toLowerCase` Methode. Ergebnisse unterscheiden, wenn die Regeln für eine Sprache mit die regulären Unicode-Zuordnungen Groß-/Kleinschreibung in Konflikt stehen.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [String-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ToLocaleUpperCase-Methode (String)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [toLowerCase-Methode](../../javascript/reference/tolowercase-method-javascript.md)