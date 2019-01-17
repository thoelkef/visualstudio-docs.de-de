---
title: IDebugApplication110::SynchronousCallInMainThread | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::SynchronousCallInMainThread
ms.assetid: 57475ae5-1520-45ef-800d-ccfc6235a5d1
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d3ebe79563ed6dbd57de759b79a452f280918010
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349659"
---
# <a name="idebugapplication110synchronouscallinmainthread"></a>IDebugApplication110::SynchronousCallInMainThread
Stellt einen synchronen Aufruf im Hauptthread verarbeitet.  
  
> [!IMPORTANT]
>  [IDebugApplication110-Schnittstelle](../../winscript/reference/idebugapplication110-interface.md) wird implementiert von PDM V11. 0 und höher. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
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