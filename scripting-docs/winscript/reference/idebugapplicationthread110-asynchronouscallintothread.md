---
title: IDebugApplicationThread110::AsynchronousCallIntoThread | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 06b3031a-4aec-4a47-afaa-04642a4c4870
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2392d34a4971389b293e44a6223c2159d6d6a9cb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345850"
---
# <a name="idebugapplicationthread110asynchronouscallintothread"></a>IDebugApplicationThread110::AsynchronousCallIntoThread
Führt einen asynchronen Aufruf im Hauptthread verarbeitet.  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110-Schnittstelle](../../winscript/reference/idebugapplicationthread110-interface.md) wird implementiert von PDM V11. 0 und höher. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pptc`  
 Die [IDebugThreadCall-Schnittstelle](../../winscript/reference/idebugthreadcall-interface.md) aufzurufenden Objekts.  
  
 `dwParam1`  
 Der erste Parameter des Aufrufs.  
  
 `dwParam1`  
 Der erste Parameter des Aufrufs.  
  
 `dwParam2`  
 Der zweite Parameter des Aufrufs.  
  
 `dwParam3`  
 Der dritte Parameter des Aufrufs.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication110-Schnittstelle](../../winscript/reference/idebugapplication110-interface.md)