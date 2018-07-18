---
title: IDebugObject::GetManagedDebugObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c7b416ca9af4279e11cabbbf880a73891059df6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113220"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Erstellt eine Kopie des verwalteten Objekts im Adressraum der Debugging-Modul.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```csharp  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppObject`  
 [out] Gibt eine [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) Objekt, das das neu erstellte verwaltete Objekt darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben. E_FAIL zurück, wenn diese [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) stellt keine Instanz einer verwalteten Klasse dar.  
  
## <a name="remarks"></a>Hinweise  
 Dies [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekt muss eine Klasseninstanz verwalteter Wert-darstellen, z. B. eine `System.Decimal` Instanz. Durch die Verwendung einer lokalen Kopie, den Aufwand des Aufrufs [auswerten](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) beseitigt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)