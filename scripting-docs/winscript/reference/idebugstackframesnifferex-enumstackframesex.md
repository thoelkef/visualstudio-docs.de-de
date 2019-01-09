---
title: IDebugStackFrameSnifferEx::EnumStackFramesEx | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrameSnifferEx::EnumStackFramesEx
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c34ce267113ae5576a8b3bdca9ac34d4abc00f7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086970"
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
Gibt einen Enumerator der Stapelrahmen des aktuellen Threads.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwSpMin`  
 [in] Die untere Grenze von Adresse für die Auflistung von Stapelrahmen.  
  
 `ppedsf`  
 [out] Der Enumerator von Stapelrahmen des aktuellen Threads.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Die Stack-Frame-Enumerator gibt die Frames, die beginnend ab des Anfang des Stapels, mit dem zuletzt abgelegte Frame zurück. Der Enumerator enthält nur Stapelrahmen mit Adressen, die größer als oder gleich `dwSpMin`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStackFrameSnifferEx-Schnittstelle](../../winscript/reference/idebugstackframesnifferex-interface.md)