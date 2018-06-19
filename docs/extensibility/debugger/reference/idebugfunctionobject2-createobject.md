---
title: IDebugFunctionObject2::CreateObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5283d72972e1ba579cafa82648cbf0ec0fcf80c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113470"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Erstellt ein Objekt, das einen Konstruktor angegebenen Flageinstellungen Auswertung und einen Timeoutwert verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pConstructor`  
 [in] Ein [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Objekt, das den Konstruktor des zu erstellenden Objekts darstellt.  
  
 `dwArgs`  
 [in] Die Anzahl von Parametern in der `pArg` Array. Gibt die Anzahl von Parametern, die an den Konstruktor übergeben.  
  
 `pArgs`  
 [in] Ein Array von [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekte, die den Parameter darstellt, die an den Konstruktor übergeben.  
  
 `dwEvalFlags`  
 [in] Eine Kombination aus Flags aus der [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) -Enumeration, die angeben, wie die Auswertung ausgeführt werden.  
  
 `dwTimeout`  
 [in] Maximale Zeit in Millisekunden, bis vor der Rückgabe dieser Methode. Verwendung **UNENDLICHE** zum unendlichen Warten angibt.  
  
 `ppObject`  
 [out] Gibt eine **IDebugObject** , das das neu erstellte Objekt darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Rufen Sie diese Methode, um ein Objekt zu erstellen, die eine Instanz einer Klasse oder andere komplexer Typ, der einen Konstruktor benötigt, der einen Parameter darstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)