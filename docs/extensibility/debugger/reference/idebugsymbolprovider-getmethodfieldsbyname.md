---
title: "IDebugSymbolProvider::GetMethodFieldsByName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetMethodFieldsByName"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetMethodFieldsByName-Methode"
ms.assetid: 1f781320-81ef-4037-b068-f1864b271258
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugSymbolProvider::GetMethodFieldsByName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft das Feld ab, das einen vollqualifizierten Methodennamen darstellt.  
  
## Syntax  
  
```cpp#  
HRESULT GetMethodFieldsByName(   
   LPCOLESTR          pszFullName,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int GetMethodFieldsByName(  
   string               pszFullName,   
   NAME_MATCH           nameMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parameter  
 `pszFullName`  
 \[in\]  Der Methodenname.  
  
 `nameMatch`  
 \[in\]  Wählt den Typ der Übereinstimmung aus, z. B. die Groß\-\/Kleinschreibung beachtet.  
  
 `ppEnum`  
 \[out\]  Gibt einen [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Enumerator für die Felder zurück, die dieser Methode zugeordneten.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Eine Methode kann mit mehreren Feldern zugeordnet sind, z. B., wenn sie überladen wird.  
  
## Siehe auch  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)