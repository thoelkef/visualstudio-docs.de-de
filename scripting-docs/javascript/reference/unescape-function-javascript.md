---
title: unescape-Funktion (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: unescape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Unescape method
ms.assetid: 4adf0270-88b5-4d54-8110-d879d6ae97c2
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96601fc21f47c86aec8c3702a6861c3676aacacf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="unescape-function-javascript"></a>unescape-Funktion (JavaScript)
Decodiert `String` Objekte codiert, mit der `escape` Funktion. Veraltet.  
  
## <a name="syntax"></a>Syntax  
  
```  
unescape(charString)   
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `charString` Argument ist ein `String` Objekt oder Literal decodiert werden.  
  
 Die `unescape` Funktion gibt einen Zeichenfolgenwert mit dem Inhalt des `charstring`. Alle Zeichen, die mit dem % codiert*Xx* hexadezimaler Form werden durch ihre ASCII-Zeichen-Set-Entsprechungen ersetzt.  
  
 Codiert Zeichen **%u** *Xxxx* Format (Unicode-Zeichen) werden durch das Unicode-Zeichen mit hexadezimaler Codierung ersetzt *Xxxx*.  
  
> [!NOTE]
>  Die `unescape` Funktion sollte nicht verwendet werden, die zu decodierende Uniform Resource Identifiers (URI). Verwendung `decodeURI` und `decodeURIComponent` stattdessen fungiert.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Global-Objekt](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [DecodeURI-Funktion](../../javascript/reference/decodeuri-function-javascript.md)   
 [DecodeURIComponent-Funktion](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [Escape-Funktion](../../javascript/reference/escape-function-javascript.md)   
 [String-Objekt](../../javascript/reference/string-object-javascript.md)