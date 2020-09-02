---
title: 'Idebugobject:: IsEqual | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85252cdaf9fb076ebd4f8000115bcea576531bb1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159111"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vergleicht ein-Objekt mit diesem-Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```csharp  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pObject`  
 in Ein [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt, das das Objekt darstellt, mit dem verglichen werden soll.  
  
 `pfIsEqual`  
 vorgenommen Gibt einen Wert ungleich 0 (NULL `TRUE` ) zurück, wenn die Werte der-Objekte gleich sind; andernfalls wird NULL () zurückgegeben `FALSE` .  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 In der Regel kann diese Methode die Adressen der durch den `pObject` -Parameter dargestellten Werte und dieses [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt vergleichen. wenn die Adressen gleich sind, können die-Objekte als gleich betrachtet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
