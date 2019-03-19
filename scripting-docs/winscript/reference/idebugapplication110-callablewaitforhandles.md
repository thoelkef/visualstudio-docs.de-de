---
title: IDebugApplication110::CallableWaitForHandles | Microsoft-Dokumentation
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
ms.openlocfilehash: ac5482924288e52895398084aa4f5ab44e151a66
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155367"
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
Wartet darauf, eines der angegebenen Handles signalisiert wird, während gleichzeitig threadübergreifende Aufrufe, die für diesen Thread bereitgestellt werden. Diese Methode muss aus dem Debuggerthread aufgerufen werden.  
  
> [!IMPORTANT]
>  [IDebugApplication110-Schnittstelle](../../winscript/reference/idebugapplication110-interface.md) wird implementiert von PDM V11. 0 und höher. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>Parameter  
 `handleCount`  
 Die Anzahl der Handles zu warten.  
  
 `pHandles`  
 Der Satz von Handles zu warten.  
  
 `pIndex`  
 Wenn der HRESULT-Wert ist S_OK zurück, der Index `pHandles` für das Handle, das signalisiert wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication110-Schnittstelle](../../winscript/reference/idebugapplication110-interface.md)