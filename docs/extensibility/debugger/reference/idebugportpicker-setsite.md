---
title: IDebugPortPicker::SetSite | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00730a5338a3355f2397a91bc7a3693b30dca31b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930608"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Legt den Dienstanbieter fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetSite(  
   IServiceProvider * pSP  
);  
```  
  
```csharp  
public int SetSite(  
   IServiceProvider pSP  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pSP`  
 [in] Verweis auf die Schnittstelle des Dienstanbieters.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird aufgerufen werden, bevor Sie andere Methoden aufgerufen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)