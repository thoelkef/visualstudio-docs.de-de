---
title: Ijsdebugbreakpoint::D isable-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.Disable
apilocation:
- jscript9diag.dll
ms.assetid: f6f2889c-c001-4ee5-8e3f-4f36235e4fad
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51e4be2abc8b5a507e091b330de1779cfb14b57e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577736"
---
# <a name="ijsdebugbreakpointdisable-method"></a>IJsDebugBreakPoint::Disable-Methode
Deaktiviert den Haltepunkt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Disable(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="remarks"></a>Hinweise  
 Gibt E_UNEXPECTED zurück, wenn der Aufruf an einem gelöschten Haltepunkt erfolgt. Gibt "S_FALSE" zurück bei Aufruf an einem bereits deaktivierten Haltepunkt.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag. h  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugBreakPoint-Schnittstelle](../../winscript/reference/ijsdebugbreakpoint-interface.md)