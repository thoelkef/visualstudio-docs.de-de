---
title: ToLocaleUpperCase-Methode (String) (JavaScript) | Microsoft Docs
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
- toLocaleUpperCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleUpperCase method
ms.assetid: e927adb6-475e-44b2-91f7-cedda10a39b0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07a89560dde0319598da30fc3451524112b99eac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640430"
---
# <a name="tolocaleuppercase-method-string-javascript"></a>toLocaleUpperCase-Methode (String) (JavaScript)
Gibt eine Zeichenfolge zurück, in dem alle alphabetische Zeichen in Großbuchstaben unter Berücksichtigung der Host konvertiert Umgebung aktuelle Gebietsschema worden ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
stringVar.toLocaleUpperCase( )  
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `stringVar` Verweis ist ein `String` -Objekt oder Zeichenfolgenliteral.  
  
 Die `toLocaleUpperCase` Methode konvertiert Zeichen in eine Zeichenfolge, die Berücksichtigung aktuellen Gebietsschemas der hostumgebung. In den meisten Fällen das Ergebnis entspricht dem als Ergebnis der `toUpperCase` Methode. Ergebnisse unterscheiden, wenn die Regeln für eine Sprache mit die regulären Unicode-Zuordnungen Groß-/Kleinschreibung in Konflikt stehen.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [String-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ToLocaleLowerCase-Methode (String)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase-Methode (String)](../../javascript/reference/touppercase-method-string-javascript.md)