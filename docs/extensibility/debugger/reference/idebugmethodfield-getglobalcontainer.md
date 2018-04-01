---
title: IDebugMethodField::GetGlobalContainer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b2fef7bf82992b6fdaaadbbd2bee6a9e36f68ad0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
Ruft den globalen Container der Methode ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetGlobalContainer(  
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetGlobalContainer(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppClass`  
 [out] Gibt eine [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) für das Modul, in dem diese Methode definiert wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Das zurückgegebene [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt, das gesamte Modul darstellt, und ist ein künstlicher Objekt, d. h. das Modul selbst verfügt nicht über eine tatsächliche Klasse, aber es dargestellt werden kann ein `IDebugClassField` -Objekt, sodass die verschiedenen Elemente des Moduls aufgelistet und ermittelt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)