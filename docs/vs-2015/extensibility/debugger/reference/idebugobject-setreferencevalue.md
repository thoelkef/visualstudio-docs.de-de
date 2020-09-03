---
title: 'Idebugobject:: "abtreferencevalue" | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b1da0e152d536e9bed47dfb3964df60634c017bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180505"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Legt den Verweis Wert dieses-Objekts fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT SetReferenceValue(   
   IDebugObject* pObject  
);  
```  
  
```csharp  
int SetReferenceValue(  
   [In] IDebugObject pObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pObject`  
 in Ein [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt, das den neuen Verweis Wert darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode macht dieses [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt zu einem Verweis auf den Wert des Objekts, das im- `pObject` Parameter angegeben ist, und gibt einen vorherigen Verweis zurück. Beachten Sie, dass dieses `IDebugObject` Objekt bereits ein Referenztyp sein muss.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
