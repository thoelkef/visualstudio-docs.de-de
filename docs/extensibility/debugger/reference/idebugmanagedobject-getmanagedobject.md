---
title: IDebugManagedObject::GetManagedObject | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugManagedObject::GetManagedObject
helpviewer_keywords: IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d73d68edcae0de9ca5834d6c622660e83cb72afa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
Gibt eine Schnittstelle, die das verwaltete Objekt darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetManagedObject(   
   IUnknown** ppManagedObject  
);  
```  
  
```cpp  
int GetManagedObject(  
   out object ppManagedObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppManagedObject`  
 [out] Gibt eine Schnittstelle, die das verwaltete Objekt darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Für jede Schnittstelle implementiert, die von der verwalteten Klasse, sodass seine Methoden aufgerufen werden kann die Schnittstelle, die von dieser Methode zurückgegebene abgefragt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)