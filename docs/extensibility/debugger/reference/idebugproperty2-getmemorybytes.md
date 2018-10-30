---
title: IDebugProperty2::GetMemoryBytes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::GetMemoryBytes
helpviewer_keywords:
- IDebugProperty2::GetMemoryBytes
ms.assetid: b32042ed-7a06-4b4a-99ef-fe03b0aa61cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b6b8b82067405e91f4d1d7fac4aeccd5e29ffa0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948017"
---
# <a name="idebugproperty2getmemorybytes"></a>IDebugProperty2::GetMemoryBytes
Ruft die Arbeitsspeicher-Bytes, aus denen den Wert einer Eigenschaft ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetMemoryBytes (   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```csharp  
int GetMemoryBytes (   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppMemoryBytes`  
 [out] Gibt eine [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) -Objekt, das verwendet werden kann, um den Arbeitsspeicher abzurufen, die den Wert der Eigenschaft enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls den Fehlercode zurück. Gibt `S_GETMEMORYBYTES_NO_MEMORY_BYTES` treten keine Bytes Arbeitsspeicher abrufen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)