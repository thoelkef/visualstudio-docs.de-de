---
title: IDebugComPlusSymbolProvider::UnloadSymbols | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- UnloadSymbols
- IDebugComPlusSymbolProvider::UnloadSymbols
ms.assetid: 53e3ddc1-ab47-4097-8fef-b26e5504b37a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35ae8e84b82f1ea2d965396f662879ed1cfe1531
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104942"
---
# <a name="idebugcomplussymbolproviderunloadsymbols"></a>IDebugComPlusSymbolProvider::UnloadSymbols
Wird die Debugsymbolen für das angegebene Modul aus dem Arbeitsspeicher entladen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT UnloadSymbols(  
   ULONG32 ulAppDomainID,  
   GUID    guidModule  
);  
```  
  
```csharp  
int UnloadSymbols(  
   uint ulAppDomainID,  
   Guid guidModule  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ulAppDomainID`  
 [in] Der Bezeichner der Anwendungsdomäne.  
  
 `guidModule`  
 [in] Eindeutiger Bezeichner des Moduls.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Implementierung dieser Methode für eine **CDebugSymbolProvider** -Objekt, das macht die [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) Schnittstelle.  
  
```cpp  
HRESULT CDebugSymbolProvider::UnloadSymbols(  
    ULONG32 ulAppDomainID,  
    GUID guidModule  
)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pmodule;  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    METHOD_ENTRY( CDebugSymbolProvider::UnloadSymbols );  
  
#if DEBUG  
  
    DebugVerifyModules();  
#endif  
  
    IfFailGo( GetModule( idModule, &pmodule ) );  
  
#if DEBUG  
  
    DebugVerifyModules();  
#endif  
  
    RemoveModule( pmodule );  
    pmodule->Cleanup();  
  
Error:  
#if DEBUG  
  
    DebugVerifyModules();  
#endif  
  
    METHOD_EXIT( CDebugSymbolProvider::UnloadSymbols, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)