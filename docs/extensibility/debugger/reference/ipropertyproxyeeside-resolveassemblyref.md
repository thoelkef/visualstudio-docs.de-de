---
title: "IPropertyProxyEESide::ResolveAssemblyRef | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide::ResolveAssemblyRef"
helpviewer_keywords: 
  - "IPropertyProxyEESide::ResolveAssemblyRef"
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IPropertyProxyEESide::ResolveAssemblyRef
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bestimmt die Position des angegebenen verwalteten Assemblyverweises.  
  
## Syntax  
  
```cpp#  
HRESULT ResolveAssemblyRef(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  assemLocation,  
   ASSEMBLYLOCRESOLUTION* alr  
);  
```  
  
```c#  
int ResolveAssemblyRef(  
   ref string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     assemLocation,  
   out enum_ASSEMBLYLOCRESOLUTION alr  
);  
```  
  
#### Parameter  
 `assemName`  
 \[in\]  Name der Assembly aufzulösen.  
  
 `assemBytes`  
 \[out\]  Gibt ein Objekt zurück, das die [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) Bytes Assembly enthält, die mit dem Verweis zugeordnet sind.  
  
 `assemPdb`  
 \[out\]  Gibt ein `IEEDataStorage` Symbolspeichers Objekt zurück, das die Daten enthält, die mit diesen Verweis zugeordnet sind.  
  
 `assemLocation`  
 \[out\]  Gibt den Speicherort der Pfad dieses Verweises zurück.  
  
 `alr`  
 \[out\]  Gibt einen Wert aus der [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)\-Enumeration zurück, der den Speicherort der Assembly diesen Verweis angibt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird i. d. R. nicht über einen benutzerdefinierten Ausdrucksauswertung implementiert.  
  
## Siehe auch  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)