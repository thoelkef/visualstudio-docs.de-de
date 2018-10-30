---
title: IDebugFunctionObject::CreateObjectNoConstructor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d82df4cef343965d9fdf88357154a9a3a399d9eb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842156"
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