---
title: 'IDebugApplication110:: asynchronouscallinmainthread | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::AsynchronousCallInMainThread
ms.assetid: 13b80ff0-4bed-48c1-8031-d4147b51bf6c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04c1a2962662d0046c6b9d323a287d580ee0f3e6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577390"
---
# <a name="idebugapplication110asynchronouscallinmainthread"></a>IDebugApplication110::AsynchronousCallInMainThread
Führt einen asynchronen-Rückruf für den Haupt Thread aus.  
  
> [!IMPORTANT]
> Die [IDebugApplication110-Schnittstelle](../../winscript/reference/idebugapplication110-interface.md) wird von PDM v 11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pptc`  
 Das aufzurufende [idebugthreadcallcenter-Schnittstellen](../../winscript/reference/idebugthreadcall-interface.md) Objekt.  
  
 `dwParam1`  
 Der erste Parameter des Aufrufes.  
  
 `dwParam1`  
 Der erste Parameter des Aufrufes.  
  
 `dwParam2`  
 Der zweite Parameter des Aufrufes.  
  
 `dwParam3`  
 Der dritte Parameter des Aufrufes.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication110-Schnittstelle](../../winscript/reference/idebugapplication110-interface.md)