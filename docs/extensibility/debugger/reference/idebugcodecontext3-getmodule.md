---
title: "IDebugCodeContext3::GetModule | Microsoft Docs"
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
  - "IDebugCodeContext3::GetModule"
ms.assetid: 8e4317b8-8255-486c-a896-a68ed94f8aa1
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCodeContext3::GetModule
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft einen Verweis auf die Schnittstelle des Debugmoduls ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetModule(   
   IDebugModule2 **ppModule  
);  
```  
  
```c#  
public int GetModule(   
   out IDebugModule2 ppModule  
);  
```  
  
#### Parameter  
 `ppModule`  
 \[out\]  Verweis auf die Schnittstelle Modul Debuggen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein **CDebugCodeContext\-Objekt** implementiert, das die [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)\-Schnittstelle verfügbar macht.  
  
```cpp#  
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
  
## Siehe auch  
 [IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)