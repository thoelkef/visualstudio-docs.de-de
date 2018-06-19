---
title: IDebugMethodField::EnumArguments | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc92dc6b560332509f69a975eca63ddb5c191fab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112271"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Erstellt einen Enumerator für den Typ jedes Arguments erforderlich, um die Methode aufzurufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnumArguments(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumArguments(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppParams`  
 [out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der Argumenttypen darstellt. Gibt einen null-Wert zurück, wenn keine Argumente.  
  
## <a name="return-value"></a>Rückgabewert  
 Bei Erfolg S_OK zurückgibt, oder gibt "S_FALSE" zurück, wenn keine Argumente. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Jedes Element ist ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt, das die Typen der einzelnen Parameter darstellt. Rufen Sie die [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) Methode zum Abrufen von Informationen über den Typ jedes Parameters.  
  
 Wenn der Name des Parameters zusammen mit dem Typ erforderlich ist, rufen Sie die [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)