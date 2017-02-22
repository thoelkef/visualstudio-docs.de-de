---
title: "IDebugDocumentContext2::EnumCodeContexts | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::EnumCodeContexts"
helpviewer_keywords: 
  - "IDebugDocumentContext2::EnumCodeContexts"
ms.assetid: 627af69c-5cce-4e1d-8233-5f4d8dbc62e5
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentContext2::EnumCodeContexts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine Liste aller Code kontexte ab, die diesem Dokumentenkontext zugeordnet sind.  
  
## Syntax  
  
```cpp#  
HRESULT EnumCodeContexts(   
   IEnumDebugCodeContexts2** ppEnumCodeCxts  
);  
```  
  
```c#  
int EnumCodeContexts(   
   out IEnumDebugCodeContexts2 ppEnumCodeCxts  
);  
```  
  
#### Parameter  
 `ppEnumCodeCxts`  
 \[out\]  Gibt ein [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)\-Objekt zurück, das eine Liste von Codekontexten enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ein Kontext des Einzelbelegs kann mehrere kontexte Code generieren, wenn das Dokument Vorlagen oder Includedateien verwendet.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein einfaches `CDebugContext`\-Objekt implementiert, das die [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)\-Schnittstelle verfügbar macht.  
  
```cpp#  
HRESULT CDebugContext::EnumCodeContexts(IEnumDebugCodeContexts2 **ppEnumCodeCxts)    
{    
   HRESULT hr;    
  
   // Check for a valid IEnumDebugCodeContexts2 interface pointer.    
   if (ppEnumCodeCxts)    
   {    
      *ppEnumCodeCxts = NULL;    
  
      // Create a CEnumDebugCodeContexts object.    
      CComObject<CEnumDebugCodeContexts>* pEnum;    
      hr = CComObject<CEnumDebugCodeContexts>::CreateInstance(&pEnum);    
      assert(hr == S_OK);    
      if (hr == S_OK)    
      {    
         // Get an IID_IDebugCodeContext2 interface.    
         CComPtr<IDebugCodeContext2> spCodeCxt;    
         hr = QueryInterface(IID_IDebugCodeContext2,  
                             (void**)&spCodeCxt);  
         assert(hr == S_OK);    
         if (hr == S_OK)    
         {    
            // Initialize the code context enumerator with the    
            // IDebugCodeContext2 information.  
            IDebugCodeContext2* rgpCodeContext[] = { spCodeCxt.p };    
            hr = pEnum->Init(rgpCodeContext,  
                             &(rgpCodeContext[1]),  
                             NULL,  
                             AtlFlagCopy);  
            assert(hr == S_OK);    
            if (hr == S_OK)    
            {    
               // Set the passed IEnumDebugCodeContexts2 pointer equal to the pointer  
               // value of the created CEnumDebugCodeContexts object.  
               hr = pEnum->QueryInterface(ppEnumCodeCxts);    
               assert(hr == S_OK);    
            }    
         }    
  
         // Otherwise, delete the CEnumDebugCodeContexts object.    
         if (FAILED(hr))    
         {    
            delete pEnum;    
         }    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## Siehe auch  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)