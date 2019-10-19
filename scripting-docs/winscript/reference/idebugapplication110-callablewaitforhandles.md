---
title: 'IDebugApplication110:: callablewaitforhandles | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22af0e9dcf548bbd2f0f8c179b4889d5294eb284
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575075"
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
Wartet darauf, dass alle angegebenen Handles signalisiert werden, während Thread übergreifende Aufrufe an diesen Thread gesendet werden können. Diese Methode muss vom Debuggerthread aufgerufen werden.  
  
> [!IMPORTANT]
> Die [IDebugApplication110-Schnittstelle](../../winscript/reference/idebugapplication110-interface.md) wird von PDM v 11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>Parameter  
 `handleCount`  
 Die Anzahl der Handles, auf die gewartet werden soll.  
  
 `pHandles`  
 Der Satz von Handles, auf den gewartet werden soll.  
  
 `pIndex`  
 Wenn der HRESULT-Wert S_OK ist, ist der Index in `pHandles` für das Signal, das signalisiert wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication110-Schnittstelle](../../winscript/reference/idebugapplication110-interface.md)