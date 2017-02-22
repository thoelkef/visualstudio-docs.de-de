---
title: "IDebugComPlusSymbolProvider::GetLocalVariablelayout | Microsoft Docs"
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
  - "GetLocalVariablelayout"
  - "IDebugComPlusSymbolProvider::GetLocalVariablelayout"
ms.assetid: b7328d85-e5e9-4d9f-bcd1-e7711fd33878
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugComPlusSymbolProvider::GetLocalVariablelayout
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft das Lay\-out von lokalen Variablen für eine Gruppe von Methoden ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetLocalVariablelayout(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   ULONG32   cMethods,  
   _mdToken  rgMethodTokens[],  
   IStream** pStreamLayout  
);  
```  
  
```c#  
int GetLocalVariablelayout(  
   uint        ulAppDomainID,  
   Guid        guidModule,  
   uint        cMethods,  
   int[]       rgMethodTokens,  
   out IStream pStreamLayout  
);  
```  
  
#### Parameter  
 `ulAppDomainID`  
 \[in\]  Bezeichner der Anwendungsdomäne.  
  
 `guidModule`  
 \[in\]  Eindeutiger Bezeichner des Moduls.  
  
 `cMethods`  
 \[in\]  Zahl Methodentoken im `rgMethodTokens` Array.  
  
 `rgMethodTokens`  
 \[in\]  Array Methodentoken.  
  
 `pStreamLayout`  
 \[out\]  Ein Textstream, der das variable Lay\-out enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein **CDebugSymbolProvider\-Objekt** implementiert, das die [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)\-Schnittstelle verfügbar macht.  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetLocalVariablelayout(  
    ULONG32 ulAppDomainID,   
    GUID guidModule,   
    ULONG32 cMethods,   
    _mdToken rgMethodTokens[],   
    IStream** ppStreamLayout)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY(CDebugSymbolProvider::GetLocalVariablelayout);  
  
    CComPtr<ISymUnmanagedReader> symReader;  
    IfFailRet(GetSymUnmanagedReader(ulAppDomainID, guidModule, (IUnknown **) &symReader));  
    CComPtr<IStream> stream;  
    IfFailRet(CreateStreamOnHGlobal(NULL, true, &stream));  
  
    for (ULONG32 iMethod = 0; iMethod < cMethods; iMethod += 1)  
    {  
        CComPtr<ISymUnmanagedMethod> method;  
        IfFailRet(symReader->GetMethod(rgMethodTokens[iMethod], &method));  
        CComPtr<ISymUnmanagedScope> rootScope;  
        IfFailRet(method->GetRootScope(&rootScope));  
  
        //  
        // Add the method's variables to the stream  
        //  
        IfFailRet(AddScopeToStream(rootScope, 0, stream));  
  
        // do end of method marker  
        ULONG32 depth = 0xFFFFFFFF;  
        ULONG cb = 0;  
        IfFailRet(stream->Write(&depth, sizeof(depth), &cb));  
    }  
  
    LARGE_INTEGER pos;  
    pos.QuadPart = 0;  
    IfFailRet(stream->Seek(pos, STREAM_SEEK_SET, 0));  
    *ppStreamLayout = stream.Detach();  
  
    METHOD_EXIT(CDebugSymbolProvider::GetLocalVariablelayout, hr);  
    return hr;  
}  
```  
  
## Siehe auch  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)