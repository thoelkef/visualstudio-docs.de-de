---
title: Boolean-Objekt (JavaScript) | Microsoft Docs
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
- boolean_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Boolean object
- Boolean data type, Boolean object
ms.assetid: d67748f2-7bf5-4889-8269-e777616cc5f0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20695376e4935cf6ddc34f30e373df19575ece3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633910"
---
# <a name="boolean-object-javascript"></a>Boolean-Objekt (JavaScript)
Erstellt einen neuen booleschen Wert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
boolObj = new Boolean([boolValue])  
```  
  
## <a name="parameters"></a>Parameter  
 `boolObj`  
 Erforderlich. Der Variablenname, dem das `Boolean`-Objekt zugewiesen wird.  
  
 `boolValue`  
 Dies ist optional. Der anfängliche boolesche Wert für das neue Objekt. Wenn `boolvalue` weggelassen wird, oder `false`, 0, `null`, `NaN`, oder eine leere Zeichenfolge, die der anfängliche Wert des Boolean-Objekt ist `false`. Andernfalls ist der Anfangswert `true`.  
  
## <a name="remarks"></a>Hinweise  
 Die `Boolean` Objekt ist ein Wrapper für den Boolean-Datentyp. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]implizit verwendet die `Boolean` Objekt immer ein Boolean-Datentyp, um konvertiert wird eine `Boolean` Objekt.  
  
 Instanziieren Sie selten die `Boolean` Objekt explizit.  
  
## <a name="properties"></a>Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `Boolean`-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|[Constructor-Eigenschaft](../../javascript/reference/constructor-property-boolean.md)|Gibt die Funktion, die einen booleschen Wert erstellt.|  
|[Prototype-Eigenschaft](../../javascript/reference/prototype-property-boolean.md)|Gibt einen Verweis auf den Prototyp für einen booleschen Wert zurück.|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle werden die Methoden des `Boolean`-Objekts aufgelistet.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[ToString-Methode](../../javascript/reference/tostring-method-boolean-1.md)|Gibt eine Zeichenfolgendarstellung der einen booleschen Wert zurück.|  
|[ValueOf-Methode](../../javascript/reference/valueof-method-boolean.md)|Ruft einen Verweis auf den booleschen Wert ab.|  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]