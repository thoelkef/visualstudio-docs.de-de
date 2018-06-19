---
title: ScriptEngine-Funktion (JavaScript) | Microsoft Docs
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
- ScriptEngine
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ScriptEngine function
ms.assetid: 65674b2b-d2c2-4493-99b3-f0d20fda8249
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d441fcce065677f7b673a9979acff9cf9aa2ce90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640860"
---
# <a name="scriptengine-function-javascript"></a>ScriptEngine-Funktion (JavaScript)
Ruft den Namen der verwendeten Skriptsprache ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
ScriptEngine()  
```  
  
## <a name="remarks"></a>Hinweise  
 Die Funktion `ScriptEngine` gibt „JScript“ zurück, womit [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] als das aktuelle Skriptmodul angegeben wird.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `ScriptEngine`-Funktion:  
  
```JavaScript  
if (window.ScriptEngine) {  
    console.log(window.ScriptEngine());  
}  
  
// Output: JScript  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [ScriptEngineBuildVersion-Funktion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMajorVersion-Funktion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [ScriptEngineMinorVersion-Funktion](../../javascript/reference/scriptengineminorversion-function-javascript.md)