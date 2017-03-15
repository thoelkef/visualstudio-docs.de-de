---
title: "IDebugSymbolProvider::GetClassTypeByName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetClassTypeByName"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetClassTypeByName-Methode"
ms.assetid: 2c748909-51dc-49b7-b193-19f96fca1138
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugSymbolProvider::GetClassTypeByName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft den Klassenfeld den Typ ab, der einen vollqualifizierten Klassennamen darstellt.  
  
## Syntax  
  
```cpp#  
HRESULT GetClassTypeByName(   
   LPCOLESTR          pszClassName,  
   NAME_MATCH         nameMatch,  
   IDebugClassField** ppField  
);  
```  
  
```c#  
int GetClassTypeByName(  
   string               pszClassName,   
   NAME_MATCH           nameMatch,   
   out IDebugClassField ppField  
);  
```  
  
#### Parameter  
 `pszClassName`  
 \[in\]  Der Klassenname.  
  
 `nameMatch`  
 \[in\]  Wählt den Typ der Übereinstimmung aus, z. B. die Groß\-\/Kleinschreibung beachtet.  Ein Wert aus der [NAME\_MATCH](../../../extensibility/debugger/reference/name-match.md)\-Enumeration.  
  
 `ppField`  
 \[out\]  Gibt den Klassentyp zurück, wie sie von der [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)\-Schnittstelle dargestellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [NAME\_MATCH](../../../extensibility/debugger/reference/name-match.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)