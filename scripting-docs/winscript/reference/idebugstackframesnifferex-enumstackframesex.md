---
title: IDebugStackFrameSnifferEx::EnumStackFramesEx | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation: jscript.dll
helpviewer_keywords: IDebugStackFrameSnifferEx::EnumStackFramesEx
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a96a382c1dce73731fdd4326d8b0d1c35b7aa33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
Gibt einen Enumerator für Stapelrahmen des aktuellen Threads zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwSpMin`  
 [in] Die Adresse Untergrenze für die Auflistung von Stapelrahmen.  
  
 `ppedsf`  
 [out] Enumerator für Stapelrahmen des aktuellen Threads.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Stack-Frame-Enumerator gibt die Frames, die beginnend am Anfang des Stapels, mit dem zuletzt abgelegte Frame zurück. Der Enumerator enthält nur Stapelrahmen mit Adressen, die größer als oder gleich `dwSpMin`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStackFrameSnifferEx-Schnittstelle](../../winscript/reference/idebugstackframesnifferex-interface.md)