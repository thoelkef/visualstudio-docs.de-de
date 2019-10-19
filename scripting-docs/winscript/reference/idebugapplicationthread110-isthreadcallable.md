---
title: 'IDebugApplicationThread110:: isthreadcallable | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::IsThreadCallable
ms.assetid: 2a75a366-801d-47e0-bba3-51aa669e03a7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ff81190247454a4471a4150843d3fb0aaed5999
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574466"
---
# <a name="idebugapplicationthread110isthreadcallable"></a>IDebugApplicationThread110::IsThreadCallable
Bestimmt, ob sich dieser Thread in einem Zustand befindet, der Aufrufe verarbeitet, die mithilfe der Thread Wechsel Mechanismen von PDM durchgeführt werden, z. b. synchronouscallinthread.  
  
> [!IMPORTANT]
> Die [IDebugApplicationThread110-Schnittstelle](../../winscript/reference/idebugapplicationthread110-interface.md) wird von PDM v 11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT IsThreadCallable([out, annotation("_Out_")] BOOL * pfIsCallable);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pfIsCallable`  
 [out] `true`, wenn der Thread aufgerufen werden kann, andernfalls `false`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplicationThread110-Schnittstelle](../../winscript/reference/idebugapplicationthread110-interface.md)