---
title: Escape-Funktion (JavaScript) | Microsoft Docs
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
- escape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encoding string objects
- Escape method
- hexadecimal
- String object, encoding
ms.assetid: caa92bea-ba69-4109-a68a-6e2debda463a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b53a447ae6dde917c12a4711d9038136dc4500cf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="escape-function-javascript"></a>escape-Funktion (JavaScript)
Codiert Zeichenfolgen an, damit sie auf allen Computern gelesen werden können. Veraltet.  
  
## <a name="syntax"></a>Syntax  
  
```  
escape(charString)   
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `charString` Argument ist "any" `String` Objekt oder Literal codiert werden.  
  
 Die **Escape** Funktion gibt einen Zeichenfolgenwert (im Unicode-Format) mit dem Inhalt des `charstring`. Alle Leerzeichen, Satzzeichen, Akzent Zeichen, und alle anderen nicht-ASCII-Zeichen mit ersetzt `%` *Xx* Codierung, in dem *Xx* entspricht die hexadezimale Zahl, die Zeichen. Ein Leerzeichen wird beispielsweise als "% 20" zurückgegeben.  
  
 Zeichen mit einem Wert größer als 255 gespeichert sind, mithilfe der **%u** *Xxxx* Format.  
  
> [!NOTE]
>  Die **Escape** Funktion sollte nicht zum Codieren von Uniform Resource Identifiers (URI) verwendet werden. Verwendung `encodeURI` und `encodeURIComponent` stattdessen fungiert.  
  
 **Gilt für**: [Global-Objekt](../../javascript/reference/global-object-javascript.md)  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [EncodeURI-Funktion](../../javascript/reference/encodeuri-function-javascript.md)   
 [EncodeURIComponent-Funktion](../../javascript/reference/encodeuricomponent-function-javascript.md)   
 [String-Objekt](../../javascript/reference/string-object-javascript.md)   
 [unescape-Funktion](../../javascript/reference/unescape-function-javascript.md)