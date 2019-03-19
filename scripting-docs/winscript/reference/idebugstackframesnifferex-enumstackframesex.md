---
title: IDebugStackFrameSnifferEx::EnumStackFramesEx | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 8969c279e4eb2c2966e297317a25a60f12be68a9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157973"
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