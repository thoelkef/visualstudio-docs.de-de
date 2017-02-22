---
title: "IPropertyProxyEESide::GetManagedViewerCreationData | Microsoft Docs"
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
  - "IPropertyProxyEESide::GetManagedViewerCreationData"
helpviewer_keywords: 
  - "IPropertyProxyEESide::GetManagedViewerCreationData"
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IPropertyProxyEESide::GetManagedViewerCreationData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft Informationen über den Viewer für diesen Eigenschaftentyp ab, die diesen Viewer zu instanziieren.  
  
## Syntax  
  
```cpp#  
HRESULT GetManagedViewerCreationData(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  className,  
   ASSEMBLYLOCRESOLUTION* alr,  
   BOOL*                  replacementOk  
);  
```  
  
```c#  
int GetManagedViewerCreationData(  
   out string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     className,  
   out enum_ASSEMBLYLOCRESOLUTION alr,  
   out int                        replacementOk  
);  
```  
  
#### Parameter  
 `assemName`  
 \[out\]  Gibt den Namen der Assembly zurück, die dieses Objekt enthält.  
  
 `assemBytes`  
 \[out\]  Gibt ein Objekt zurück, das die [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) Bytes Assembly dieses Objekts enthält \(dies ist ein NULL\-Wert, falls keine Bytes verfügbar sind\).  
  
 `assemPdb`  
 \[out\]  Gibt ein Objekt zurück, das die `IEEDataStorage` Symbolspeichers für dieses Objekt enthält \(dies ist ein NULL\-Wert, falls kein Symbolspeicher verfügbar ist\).  
  
 `className`  
 \[out\]  Gibt den Klassennamen zurück, der dieses Objekt enthält.  
  
 `alr`  
 \[out\]  Gibt einen Wert aus der [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)\-Enumeration zurück, der den Speicherort der Assembly angibt.  
  
 `replacementOk`  
 \[out\]  Gibt Wert ungleich 0 \(null\) zurück \(`TRUE`\), wenn sich der Wert des Objekts geändert werden kann.`FALSE`\(null\), wenn das Objekt schreibgeschützt ist.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird vom Typ schnellansichten verwendet, um einen verwalteten Viewer zu instanziieren.  
  
## Siehe auch  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)