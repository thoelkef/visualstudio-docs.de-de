---
title: IEnumDebugStackFrames::Reset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Reset
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Reset
ms.assetid: 57be2683-5346-4464-bdf5-6fd45b56253a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76cb09ef9456f0dccf3bd034914c9988dd0ff187
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963337"
---
# <a name="ienumdebugstackframesreset"></a>IEnumDebugStackFrames::Reset
Setzt eine Enumerationsfolge auf den Anfang zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Reset();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode akzeptiert keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode setzt eine Enumerationsfolge auf den Anfang zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugStackFrames-Schnittstelle](../../winscript/reference/ienumdebugstackframes-interface.md)