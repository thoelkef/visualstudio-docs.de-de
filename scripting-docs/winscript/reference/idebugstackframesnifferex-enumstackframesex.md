---
title: 'Idebugstackframesnifferex:: enumstackframesex | Microsoft-Dokumentation'
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
ms.openlocfilehash: 6a4062e7c0a9b3a82578daffa2ab7ef7e9ba614d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576711"
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
Gibt einen Enumerator von Stapel Rahmen für den aktuellen Thread zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwSpMin`  
 in Das untere Adress Limit für das Auflisten von Stapel Rahmen.  
  
 `ppedsf`  
 vorgenommen Enumerator von Stapel Rahmen für den aktuellen Thread.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Der Stapel Rahmen-Enumerator gibt die Frames beginnend am oberen Rand des Stapels mit dem zuletzt über drückten Rahmen zurück. Der Enumerator enthält nur Stapel Rahmen mit Adressen, die größer oder gleich `dwSpMin` sind.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStackFrameSnifferEx-Schnittstelle](../../winscript/reference/idebugstackframesnifferex-interface.md)