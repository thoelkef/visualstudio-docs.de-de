---
title: 'Ijsdebugdatatarget:: GetThreadContext-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetThreadContext
apilocation:
- jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7904ef81eb900c6466069267101f30d89e362a1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154685"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext-Methode
Ruft den Kontext zum angegebenen Thread ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `threadId`  
 [in] Im Zielprozess ausgeführter Thread.  
  
 `contextFlags`  
 [in] Gibt Kontextflags an. Dies ist mit dem "ContextFlags"-Feld von CONTEXT identisch (weitere Informationen finden Sie unter "winnt.h", suchen Sie nach "CONTEXT_ALL").  
  
 `contextSize`  
 [in] Die Größe des durch "pContext" angegebenen Puffers.  
  
 `pContext`  
 [out] Empfängt plattformspezifische CONTEXT-Struktur in den Puffer, der von "pContext" angegeben wird.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugDataTarget-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)