---
title: IJsDebugStackWalker-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbea11bf1188d148818ea8a082bceec76c704c2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugstackwalker-interface"></a>IJsDebugStackWalker-Schnittstelle
Stellt einen Stapeldurchlauf für einen angegebenen Thread dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Mitglieder  
  
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