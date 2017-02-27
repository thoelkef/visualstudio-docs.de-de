---
title: "IDebugDocumentContext2::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::GetName"
helpviewer_keywords: 
  - "IDebugDocumentContext2::GetName"
ms.assetid: 546c5b2e-f166-4edb-9e61-57d797ca98a1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugDocumentContext2::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den anzeigbaren Namen des Dokuments ab, das den Dokumentenkontext enthält.  
  
## Syntax  
  
```cpp#  
HRESULT GetName(   
   GETNAME_TYPE gnType,  
   BSTR*        pbstrFileName  
);  
```  
  
```c#  
int GetName(   
   enum_GETNAME_TYPE  gnType,  
   out string         pbstrFileName  
);  
```  
  
#### Parameter  
 `gnType`  
 \[in\]  Ein Wert aus der [GETNAME\_TYPE](../../../extensibility/debugger/reference/getname-type.md)\-Enumeration, der den Typ des Namens angibt, die zurückgegeben werden soll.  
  
 `pbstrFileName`  
 \[out\]  Gibt den Namen der Datei zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird i. d. R. den Aufruf an die [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)\-Methode weitergegeben, sofern der Dokumentenkontext geschrieben wird, um den Dokumentnamen selbst zu speichern \(als Beispielen werden\).  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein einfaches `CDebugContext`\-Objekt implementiert, das die [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)\-Schnittstelle verfügbar macht.  
  
```cpp#  
HRESULT CDebugContext::GetName(GETNAME_TYPE gnType, BSTR* pbstrFileName)    
{    
   HRESULT hr;    
  
   // Check for a valid file name argument.    
   if (pbstrFileName)    
   {    
      *pbstrFileName = NULL;    
  
      switch (gnType)    
      {    
         case GN_NAME:    
         case GN_FILENAME:    
         {    
            // Copy the member file name into the local file name.    
            *pbstrFileName = SysAllocString(m_sbstrFileName);    
            // Check for successful copy.    
            hr = (*pbstrFileName) ? S_OK : E_OUTOFMEMORY;    
            break;    
         }    
         default:    
         {    
            hr = E_FAIL;    
            break;    
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
 [GETNAME\_TYPE](../../../extensibility/debugger/reference/getname-type.md)