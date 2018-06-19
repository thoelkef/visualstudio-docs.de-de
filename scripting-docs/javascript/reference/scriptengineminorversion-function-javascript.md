---
title: ScriptEngineMinorVersion-Funktion (JavaScript) | Microsoft Docs
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
- ScriptEngineMinorVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ScriptEngineMinorVersion function
ms.assetid: caa506a5-e61d-4b2a-8b83-83d56a2f26cd
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1be01c0ee10cac1c68d4750455151032a59a8e6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639540"
---
# <a name="scriptengineminorversion-function-javascript"></a>ScriptEngineMinorVersion-Funktion (JavaScript)
Ruft die Nebenversionsnummer des verwendeten Skriptmoduls ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
ScriptEngineMinorVersion()  
```  
  
## <a name="remarks"></a>Hinweise  
 Der Rückgabewert entspricht direkt den Versionsinformationen in der Dynamic Link Library (DLL) für die verwendete Skriptsprache.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `ScriptEngineMinorVersion`-Funktion.  
  
```JavaScript  
if (window.ScriptEngineMinorVersion) {  
    console.log(window.ScriptEngineMinorVersion());  
}  
  
//Output: <current minor version>  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [ScriptEngine-Funktion](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineBuildVersion-Funktion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMajorVersion-Funktion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)