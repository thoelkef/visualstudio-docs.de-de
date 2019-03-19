---
title: IJsDebugStackWalker-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d06af2c509339d9499f66e1f267c54c69951e225
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150893"
---
# <a name="ijsdebugstackwalker-interface"></a>IJsDebugStackWalker-Schnittstelle
Stellt einen Stapeldurchlauf für einen angegebenen Thread dar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Member  
  
### <a name="public-methods"></a>Öffentliche Methoden  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[IJsDebugStackWalker::GetNext-Methode](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Ruft den nächsten Frame ab.|  
  
## <a name="remarks"></a>Hinweise  
 Stapeldurchläufe können nur erstellt werden, während das Ziel angehalten wird. Sie sind ungültig, sobald der Zielprozess erneut fortgesetzt wurde.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Script-Schnittstellenreferenz](../../winscript/reference/windows-script-interfaces-reference.md)