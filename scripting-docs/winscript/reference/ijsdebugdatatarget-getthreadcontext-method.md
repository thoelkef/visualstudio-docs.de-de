---
title: 'Ijsdebugdatatarget:: GetThreadContext-Methode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4e2f858c66eda2ad09b04d7beab776c793b6f195
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728180"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext-Methode
Ruft den Kontext zum angegebenen Thread ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
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