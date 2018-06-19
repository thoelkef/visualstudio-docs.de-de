---
title: RegExp-Objekt (JavaScript) | Microsoft Docs
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
- RegExp
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- RegExp object, overview
- RegExp object
ms.assetid: 7f6b1073-8cbb-49ed-94b6-56833ba663c5
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7319e4556721bcfd397061ce525acfb3278c6b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640780"
---
# <a name="regexp-object-javascript"></a>RegExp-Objekt (JavaScript)
Ein systeminternes globales Objekt, das speichert Informationen zu den Ergebnissen des Muster eines regulären Ausdrucks übereinstimmt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RegExp.property   
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche *Eigenschaft* Argument kann eines der `RegExp` -Objekteigenschaften.  
  
 Die `RegExp` Objekt kann nicht direkt erstellt werden, ist jedoch immer zur Verwendung verfügbar. Bis zum Abschluss einer erfolgreichen reguläre Ausdruckssuche die Anfangswerte fest, der die verschiedenen Eigenschaften der der `RegExp` Objekt lauten wie folgt:  
  
|Eigenschaft|Kurzform|Anfangswert|  
|--------------|---------------|-------------------|  
|Index||-1|  
|Eingabe|$_|Leere Zeichenfolge.|  
|lastIndex||-1|  
|lastMatch|$&|Leere Zeichenfolge.|  
|lastParen|$+|Leere Zeichenfolge.|  
|leftContext|$`|Leere Zeichenfolge.|  
|rightContext|$'|Leere Zeichenfolge.|  
|$1 - $9|$1 - $9|Leere Zeichenfolge.|  
  
 Seine Eigenschaften haben als ihren Wert nicht definiert, bis zum Abschluss einer erfolgreichen reguläre Ausdruckssuche.  
  
 Die globale `RegExp` Objekt sollte nicht mit verwechselt werden die **reguläre** Objekt. Obwohl sie dasselbe klingen, sind sie unabhängig und unterscheidet sich. Die Eigenschaften des globalen `RegExp` -Objekts ständig aktualisierte Informationen über jede Übereinstimmung enthalten, während es eintritt, während die Eigenschaften des der **reguläre** -Objekts enthalten nur Informationen zu den Übereinstimmungen an, die auftreten mit dieser Instanz von der **reguläre**.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird eine Suche mit regulärem Ausdruck. Übereinstimmungen angezeigt und von der globalen submatches `RegExp` -Objekt, und aus dem Array, das von zurückgegebene die `exec` Methode.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
<a name="js56jsobjregexpprop"></a>   
## <a name="properties"></a>Eigenschaften  
 [$1... $9-Eigenschaften](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md) &#124; [-Indexeigenschaft](../../javascript/reference/index-property-regexp-javascript.md) &#124; [input-Eigenschaft](../../javascript/reference/input-property-dollar-regexp-javascript.md) &#124; [LastIndex-Eigenschaft](../../javascript/reference/lastindex-property-regexp-javascript.md) &#124; [LastMatch-Eigenschaft](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md) &#124; [LastParen-Eigenschaft](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md) &#124; [LeftContext-Eigenschaft](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md) &#124; [RightContext-Eigenschaft](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)  
  
## <a name="methods"></a>Methoden  
 Die `RegExp` Objekt hat keine Methoden.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax regulärer Ausdrücke (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String-Objekt](../../javascript/reference/string-object-javascript.md)