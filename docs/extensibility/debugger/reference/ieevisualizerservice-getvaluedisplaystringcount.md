---
title: "IEEVisualizerService::GetValueDisplayStringCount | Microsoft Docs"
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
  - "IEEVisualizerService::GetValueDisplayStringCount"
  - "GetValueDisplayStringCount"
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerService::GetValueDisplayStringCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Anzahl der Wert von Zeichenfolgen ab, die für die angegebene Eigenschaft oder das Feld anzuzeigen.  
  
## Syntax  
  
```cpp#  
HRESULT GetValueDisplayStringCount (  
   DWORD         displayKind,   
   IDebugField * propertyOrField,   
   ULONG *       pcelt  
);  
```  
  
```c#  
int GetValueDisplayStringCount (  
   uint        displayKind,   
   IDebugField propertyOrField,   
   out ulong   pcelt  
);  
```  
  
#### Parameter  
 `displayKind`  
 \[in\]  Ein Wert aus der [DisplayKind](../../../extensibility/debugger/reference/displaykind.md)\-Enumeration.  
  
 `propertyOrField`  
 \[in\]  Eine [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Schnittstelle, die eine Eigenschaft oder ein Feld darstellt.  
  
 `pcelt`  
 \[out\]  Gibt die Anzahl der Werte von Zeichenfolgen zurück, die angezeigt werden sollen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)