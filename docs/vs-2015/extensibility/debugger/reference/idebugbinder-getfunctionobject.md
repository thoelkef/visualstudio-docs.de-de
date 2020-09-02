---
title: 'Idebugbinder:: getfunctionobject | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4a2a55285684c5aa93cc5876fb06c69c809d8b01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157312"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode ruft ein [idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Objekt ab, das verwendet wird, um Funktionsparameter zu erstellen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetFunctionObject(   
   IDebugFunctionObject **ppFunction  
);  
```  
  
```csharp  
int GetFunctionObject(  
   out IDebugFunctionObject ppFunction  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppFunction`  
 vorgenommen Gibt die [idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Schnittstelle zurück, die verwendet wird, um Funktionsparameter zu erstellen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
