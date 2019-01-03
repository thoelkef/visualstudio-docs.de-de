---
title: IDebugProperty3::CreateObjectID | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b6fab6a75885dba8ddfd952ec3680e2c44b87312
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855821"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Erstellt eine eindeutige ID für diese Eigenschaft, um sicherzustellen, dass es für alle anderen Eigenschaften eindeutig ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird aufgerufen, wenn die sitzungsbasierter Debug-Manager möchte, um sicherzustellen, dass diese Eigenschaft für alle anderen Eigenschaften eindeutig identifiziert wird. Die Debug-Engine (DE) unterstützt diese Methode auf, es sei denn, die Eigenschaften, die mit befasst sich bereits eindeutig identifiziert werden. Die DE diese Methode nicht unterstützt, gibt `E_NOTIMPL`.  
  
 Alle eindeutigen ID erstellt, mit `CreateObjectID` wird zerstört, wenn die [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) aufgerufen; dies auch signalisiert das Ende der die Notwendigkeit, die diese Eigenschaft eindeutig identifiziert.  
  
> [!NOTE]
>  Es gibt keine Methode diese eindeutige ID abrufen, damit die DE durchführen kann, was sie für die eindeutigen IDs möchte bei der `CreateObjectID` Methode wird aufgerufen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)