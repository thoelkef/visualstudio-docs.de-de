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
ms.openlocfilehash: da5722553b448605129adcf32cfaa52e2dc76352
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577657"
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
 **Header:** "jscript9diag. h  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugDataTarget-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)