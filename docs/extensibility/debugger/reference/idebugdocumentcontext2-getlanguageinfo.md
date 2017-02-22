---
title: "IDebugDocumentContext2::GetLanguageInfo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::GetLanguageInfo"
helpviewer_keywords: 
  - "IDebugDocumentContext2::GetLanguageInfo"
ms.assetid: 6a212ee5-414c-4eb5-ab11-19db1786943d
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentContext2::GetLanguageInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Sprache ab, die diesem Dokumentenkontext zugeordnet ist.  
  
## Syntax  
  
```cpp#  
HRESULT GetLanguageInfo(   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```c#  
int GetLanguageInfo(   
   out string pbstrLanguage,  
   out Guid   pguidLanguage  
);  
```  
  
#### Parameter  
 `pbstrLanguage`  
 \[out\]  Gibt den Namen der Sprache zurück, das den Dokumentenkontext diesem Code implementiert werden.  
  
 `pguidLanguage`  
 \[out\]  Gibt die GUID der Sprache zurück, das den Dokumentenkontext diesem Code implementiert werden.  Beispielsweise `guidVBScriptLang` oder `guidCPPLang`.  Dieses GUID ist nicht auf Sprachen beschränkt, die von [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]angegeben werden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein einfaches `CDebugContext`\-Objekt implementiert, das die [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)\-Schnittstelle verfügbar macht.  
  
```cpp#  
HRESULT CDebugContext::GetLanguageInfo(BSTR* pbstrLanguage, GUID* pguidLanguage)    
{    
   HRESULT hr;    
  
   // Check for a valid language argument pointers.    
   if (pbstrLanguage && pguidLanguage)    
   {    
      *pguidLanguage = GUID_NULL;    
      *pbstrLanguage = SysAllocString(L"Batch File");    
      if (*pbstrLanguage)    
      {    
         *pguidLanguage = guidBatLang;    
         hr = S_OK;    
      }    
      else    
      {    
         hr = E_OUTOFMEMORY;    
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