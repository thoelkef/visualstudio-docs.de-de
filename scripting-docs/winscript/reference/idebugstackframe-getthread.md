---
title: 'Idebugstackframe:: GetThread | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetThread
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetThread
ms.assetid: ece24728-a6b2-4b01-a6f0-0a82b15be39b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51cb000ef20877f4f3f6536cc9a01ae44c2810c8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576735"
---
# <a name="idebugstackframegetthread"></a>IDebugStackFrame::GetThread
Gibt den Thread zurück, der diesem Stapel Rahmen zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetThread(  
   IDebugApplicationThread**  ppat  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppat`  
 vorgenommen Der Thread, der diesem Stapel Rahmen zugeordnet ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt den Thread zurück, der diesem Stapel Rahmen zugeordnet ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStackFrame-Schnittstelle](../../winscript/reference/idebugstackframe-interface.md)