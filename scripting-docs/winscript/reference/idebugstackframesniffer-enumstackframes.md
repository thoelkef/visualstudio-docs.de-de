---
title: IDebugStackFrameSniffer::EnumStackFrames | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrameSniffer.EnumStackFrames
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrameSniffer::EnumStackFrames
ms.assetid: a7629ab3-ef7d-4bbe-a137-bb2a8ad0f384
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 245908b543bf1482022846801e5ac7d2f557ebb5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089302"
---
# <a name="idebugstackframesnifferenumstackframes"></a>IDebugStackFrameSniffer::EnumStackFrames
Gibt einen Enumerator der Stapelrahmen des aktuellen Threads.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT EnumStackFrames(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppedsf`  
 [out] Der Enumerator von Stapelrahmen des aktuellen Threads.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Die Stack-Frame-Enumerator gibt die Frames, die beginnend ab des Anfang des Stapels, beginnend mit dem zuletzt abgelegte Frame zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStackFrameSniffer-Schnittstelle](../../winscript/reference/idebugstackframesniffer-interface.md)