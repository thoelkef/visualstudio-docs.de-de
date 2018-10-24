---
title: IDebugManagedObject::SetFromManagedObject | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 89ebc236a2ffa2ea8d2fb2c1bfc71bd33ad4754b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869521"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Legt den Wert der Instanz des Klassenobjekts Wert aus der Instanz der Wertklasse als Parameter angegeben.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT SetFromManagedObject(   
   IUnknown* pManagedObject  
);  
```  
  
```csharp  
int SetFromManagedObject(  
   object pManagedObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pManagedObject`  
 [in] Eine Schnittstelle, die das verwaltete Objekt, das mit dem neuen Wert darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird verwendet, um das verwaltete Objekt zu ändern, dargestellt durch die [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)

