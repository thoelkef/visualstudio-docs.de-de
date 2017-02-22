---
title: "IDebugComPlusSymbolProvider::AreSymbolsLoaded | Microsoft Docs"
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
  - "AreSymbolsLoaded"
  - "IDebugComPlusSymbolProvider::AreSymbolsLoaded"
ms.assetid: bbf8707d-f89c-4177-b019-d519f1ec6f4a
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugComPlusSymbolProvider::AreSymbolsLoaded
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob die Programmdebuginformationen Symbole für das angegebene Modul der angegebene Bezeichner der Anwendungsdomäne geladen werden.  
  
## Syntax  
  
```cpp#  
HRESULT AreSymbolsLoaded (  
   ULONG32 ulAppDomainID,  
   GUID    guidModule  
);  
```  
  
```c#  
int AreSymbolsLoaded (  
   uint ulAppDomainID,  
   Guid guidModule  
);  
```  
  
#### Parameter  
 `ulAppDomainID`  
 \[in\]  Bezeichner der Anwendungsdomäne.  
  
 `guidModule`  
 \[in\]  Eindeutiger Bezeichner für das Modul.  
  
## Rückgabewert  
 Wenn die Programmdebuginformationen Symbole geladen sind, gibt `S_OK`zurück. andernfalls gibt `S_FALSE`zurück.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein **CDebugSymbolProvider\-Objekt** implementiert, das die [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)\-Schnittstelle verfügbar macht.  
  
```cpp#  
HRESULT CDebugSymbolProvider::AreSymbolsLoaded(  
    ULONG32 ulAppDomainID,  
    GUID guidModule  
)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    METHOD_ENTRY( CDebugSymbolProvider::AreSymbolsLoaded );  
  
    IfFalseGo( GetModule( idModule, &pModule ) == S_OK, S_FALSE );  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::AreSymbolsLoaded, hr );  
    return hr;  
}  
```  
  
## Siehe auch  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)