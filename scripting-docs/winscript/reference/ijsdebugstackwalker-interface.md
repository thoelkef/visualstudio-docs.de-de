---
title: Ijsdebugstackwalker-Schnittstelle | Microsoft-Dokumentation
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
ms.openlocfilehash: 3b06b8c1f9282c42599c798030440c30450ef6dd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574020"
---
# <a name="ijsdebugstackwalker-interface"></a>IJsDebugStackWalker-Schnittstelle
Stellt einen Stapeldurchlauf für einen angegebenen Thread dar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Member  
  
### <a name="public-methods"></a>Öffentliche Methoden  
  
|-Name|Beschreibung|  
|----------|-----------------|  
|[IJsDebugStackWalker::GetNext-Methode](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Ruft den nächsten Frame ab.|  
  
## <a name="remarks"></a>Hinweise  
 Stapeldurchläufe können nur erstellt werden, während das Ziel angehalten wird. Sie sind ungültig, sobald der Zielprozess erneut fortgesetzt wurde.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag. h  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Script-Schnittstellenreferenz](../../winscript/reference/windows-script-interfaces-reference.md)