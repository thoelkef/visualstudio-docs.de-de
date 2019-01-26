---
title: IDebugFunctionObject::CreateObjectNoConstructor | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8117b737ba33c59a3768f2a0ea19f483ff4e711e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934480"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
Erstellt ein Objekt mit keinen Konstruktor.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CreateObjectNoConstructor(   
   IDebugField*   pClassObject,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateObjectNoConstructor(  
   IDebugField      pClassField,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pClassObject`  
 [in] Ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt, das den Typ des zu erstellenden-Objekts darstellt.  
  
 `ppObject`  
 [out] Gibt eine [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , das das neu erstellte Objekt darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Rufen Sie diese Methode, um ein Objekt, das stellt eine Instanz einer Struktur oder ein komplexer Typ (die einen Konstruktor nicht erforderlich), der ein Parameter an die Funktion der durch dargestellt wird, erstellen die [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) Schnittstelle.  
  
 Wenn der Objektparameter ein Konstruktors erfordert, rufen die [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)