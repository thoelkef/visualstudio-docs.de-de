---
title: 'Ijsdebugprocess:: CreateBreakpoint-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateBreakPoint
apilocation:
- jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b398b93c2e7b5ad43abd35d385407b39c0c980f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557971"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>IJsDebugProcess::CreateBreakPoint-Methode
Legt den Haltepunkt an der angegebenen Dokumentposition fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `documentId`  
 [in] Zeiger auf "IDebugDocumentText".  
  
 `characterOffset`  
 [in] Zeichenoffset vom Anfang der Datei.  
  
 `characterCount`  
 [in] Länge des Dokumenttexts, in den der Haltepunkt eingefügt werden soll.  
  
 `isEnabled`  
 [in] Gibt an, ob der Haltepunkt aktiviert ist.  
  
 `ppDebugBreakPoint`  
 [out] Objekt, das den Haltepunkt darstellt, der erstellt wurde.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugProcess-Schnittstelle](../../winscript/reference/ijsdebugprocess-interface.md)