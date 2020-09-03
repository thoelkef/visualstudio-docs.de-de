---
title: 'Idebugobject:: getmemorycontext | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e69e5a77e93df2d338eb7d2e7114129ea9ac8d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162461"
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Arbeitsspeicher Kontext ab, der die Adresse des Werts des-Objekts darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetMemoryContext(   
   IDebugMemoryContext2** pContext  
);  
```  
  
```csharp  
int GetMemoryContext(  
   ref IDebugMemoryContext2 pContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pContext`  
 vorgenommen Gibt ein [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) -Objekt zurück, das die Adresse des Werts des-Objekts darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Der zurückgegebene Speicher Kontext gibt die Adresse des Werts an, der durch dieses [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt dargestellt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
