---
title: "IDebugSymbolProvider::GetTypeByName | Microsoft Docs"
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
  - "IDebugSymbolProvider::GetTypeByName"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetTypeByName-Methode"
ms.assetid: b9d88d3b-8b75-484a-b9cc-dc8c0fbb4bc8
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProvider::GetTypeByName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ordnet einen Symbolnamen auf ein Symbol für den Typ.  
  
## Syntax  
  
```cpp#  
HRESULT GetTypeByName(   
   LPCOLESTR     pszClassName,  
   NAME_MATCH    nameMatch,  
   IDebugField** ppField  
);  
```  
  
```c#  
int GetTypeByName(  
   string          pszClassName,   
   NAME_MATCH      nameMatch,   
   out IDebugField ppField  
);  
```  
  
#### Parameter  
 `pszClassName`  
 \[in\]  Der Symbolname.  
  
 `nameMatch`  
 \[in\]  Wählt den Typ der Übereinstimmung aus, z. B. die Groß\-\/Kleinschreibung beachtet.  Ein Wert aus der [NAME\_MATCH](../../../extensibility/debugger/reference/name-match.md)\-Enumeration.  
  
 `ppField`  
 \[out\]  Gibt den Typ des Symbols als [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekt zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode ist eine generische Version von [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md).  
  
## Siehe auch  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [NAME\_MATCH](../../../extensibility/debugger/reference/name-match.md)   
 [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)