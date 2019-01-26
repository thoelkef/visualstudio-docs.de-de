---
title: IDebugCodeContext3::GetModule | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugCodeContext3::GetModule
ms.assetid: 8e4317b8-8255-486c-a896-a68ed94f8aa1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a9c56f50e878b26ddb1012527a0388e03af6898
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54941600"
---
# <a name="idebugcodecontext3getmodule"></a>IDebugCodeContext3::GetModule
Ruft einen Verweis auf die Schnittstelle von der Debug-Modul ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetModule(   
   IDebugModule2 **ppModule  
);  
```  
  
```csharp  
public int GetModule(   
   out IDebugModule2 ppModule  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppModule`  
 [out] Verweis auf die Debug-Modul-Schnittstelle.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine **CDebugCodeContext** -Objekt, das macht die [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) Schnittstelle.  
  
```cpp  
HRESULT CDebugCodeContext::GetModule(IDebugModule2** ppModule)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
  
    IfFalseGo( ppModule, E_INVALIDARG );  
    *ppModule = NULL;  
  
    IfFailGo( this->GetModule(&pModule) );  
    IfFailGo( pModule->QueryInterface(IID_IDebugModule2, (void**) ppModule) );  
  
Error:  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)