---
title: "IDebugSymbolProvider::GetContainerField | Microsoft Docs"
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
  - "IDebugSymbolProvider::GetContainerField"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetContainerField-Methode"
ms.assetid: d6b56b4f-a96b-4fa7-87c1-bac4e58fa766
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProvider::GetContainerField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft das Feld ab, das die Debuginformationen Adresse enthält.  
  
## Syntax  
  
```cpp#  
HRESULT GetContainerField(   
   IDebugAddress*         pAddress,  
   IDebugContainerField** ppContainerField  
);  
```  
  
```c#  
int GetContainerField(  
   IDebugAddress            pAddress,   
   out IDebugContainerField ppContainerField  
);  
```  
  
#### Parameter  
 `pAddress`  
 \[in\]  Die Adresse, die durch eine [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Schnittstelle dargestellt.  
  
 `ppContainerField`  
 \[out\]  Gibt ein Feld für den Container zurück, das durch eine [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)\-Schnittstelle dargestellt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)