---
title: "IDebugComPlusSymbolProvider::UnloadSymbols | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UnloadSymbols"
  - "IDebugComPlusSymbolProvider::UnloadSymbols"
ms.assetid: 53e3ddc1-ab47-4097-8fef-b26e5504b37a
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugComPlusSymbolProvider::UnloadSymbols
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Entlädt die Programmdebuginformationen Symbole für das angegebene Modul aus dem Arbeitsspeicher entladen.  
  
## Syntax  
  
```cpp#  
HRESULT UnloadSymbols(  
   ULONG32 ulAppDomainID,  
   GUID    guidModule  
);  
```  
  
```c#  
int UnloadSymbols(  
   uint ulAppDomainID,  
   Guid guidModule  
);  
```  
  
#### Parameter  
 `ulAppDomainID`  
 \[in\]  Bezeichner der Anwendungsdomäne.  
  
 `guidModule`  
 \[in\]  Eindeutiger Bezeichner des Moduls.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein **CDebugSymbolProvider\-Objekt** implementiert, das die [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)\-Schnittstelle verfügbar macht.  
  
```cpp#  
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
  
## Siehe auch  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)