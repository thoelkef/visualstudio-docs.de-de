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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0d833f0d01cb6abda3383e1f96d1563de96b7dff
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54991709"
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