---
title: 'IActiveScriptErrorDebug110:: getexceptionthrownkind | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug110::QueryIsFirstChance
ms.assetid: ecc16e54-93e4-4322-ae13-afa7cd860032
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d50ef1dfa3492fdc43a5010b624dae296c692722
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575053"
---
# <a name="iactivescripterrordebug110getexceptionthrownkind"></a>IActiveScriptErrorDebug110::GetExceptionThrownKind
Gibt einen Wert zurück, der die Art der ausgelösten Ausnahme angibt.  
  
> [!IMPORTANT]
> Die [IActiveScriptErrorDebug110-Schnittstelle](../../winscript/reference/iactivescripterrordebug110-interface.md) wird von der PDM-Version 11,0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetExceptionThrownKind(  
   SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND*  pExceptionKind  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pExceptionKind`  
 vorgenommen Die Art der Ausnahme, die ausgelöst wird (z. b. First-Chance oder unbehandelt), die durch einen Enumerationswert der [SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md) -Enumeration dargestellt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptErrorDebug110-Schnittstelle](../../winscript/reference/iactivescripterrordebug110-interface.md)