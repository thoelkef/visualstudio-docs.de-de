---
title: IDebugStackFrame::GetCodeContext | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugStackFrame.GetCodeContext
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetCodeContext
ms.assetid: 3dd378f3-e4b7-413e-8812-0f6c72952544
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b872e63169f6c2d70cd3476324b3d0071718350
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframegetcodecontext"></a>IDebugStackFrame::GetCodeContext
Gibt den Stapelrahmen zugeordneten Codekontext zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetCodeContext(  
   IDebugCodeContext**  ppcc  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppcc`  
 [out] Der Codekontext der Stapelrahmen zugeordnet.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt den aktuellen Codekontext den Stapelrahmen zugeordnet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStackFrame-Schnittstelle](../../winscript/reference/idebugstackframe-interface.md)