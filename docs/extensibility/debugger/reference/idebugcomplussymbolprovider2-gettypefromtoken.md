---
title: "IDebugComPlusSymbolProvider2::GetTypeFromToken | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugComPlusSymbolProvider2::GetTypeFromToken"
  - "GetTypeFromToken"
ms.assetid: 4452bc5d-0225-40e0-a467-c472a5c7c4ee
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugComPlusSymbolProvider2::GetTypeFromToken
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft einen angegebenen Typ das Token ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetTypeFromToken(  
   ULONG32       appDomain,  
   GUID          guidModule,  
   DWORD         tdToken,  
   IDebugField** ppField  
);  
```  
  
```c#  
int GetTypeFromToken(  
   uint            appDomain,  
   Guid            guidModule,  
   uint            tdToken,  
   out IDebugField ppField  
);  
```  
  
#### Parameter  
 `appDomain`  
 \[in\]  Bezeichner der Anwendungsdomäne.  
  
 `guidModule`  
 \[in\]  Eindeutiger Bezeichner des Moduls.  
  
 `tdToken`  
 \[in\]  Token des abzurufenden Typs.  
  
 `ppField`  
 \[out\]  Gibt den Typ zurück, der durch [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)dargestellt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein **CDebugSymbolProvider\-Objekt** implementiert, das die [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)\-Schnittstelle verfügbar macht.  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetTypeFromToken(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    DWORD tdToken,  
    IDebugField **ppField)  
{  
    HRESULT hr = E_FAIL;  
  
    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetTypeFromToken );  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidWritePtr(ppField, IDebugField*));  
  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    IfFailGo( this->CreateClassType(idModule, tdToken, ppField) );  
  
Error:  
  
    METHOD_EXIT( CDebugDynamicFieldSymbol::GetTypeFromToken, hr );  
  
    return hr;  
}  
```  
  
## Siehe auch  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)