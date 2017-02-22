---
title: "DisplayKind | Microsoft Docs"
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
  - "DisplayKind-enumeration"
ms.assetid: 940968c5-6065-4bda-8ee6-c31597db4d71
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# DisplayKind
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Listet die gültigen Werte, die die Arten von Informationen darstellen, die von einem [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekt und dem Benutzer angezeigt.  
  
## Syntax  
  
```cpp#  
enum enum_DisplayKind  
{  
   DisplayKind_Value = 0x1,  
   DisplayKind_Name = 0x2,  
   DisplayKind_Type = 0x3,  
};  
typedef DWORD DisplayKind;  
```  
  
```c#  
public enum enum_DisplayKind  
{  
   DisplayKind_Value = 0x1,  
   DisplayKind_Name = 0x2,  
   DisplayKind_Type = 0x3,  
};  
```  
  
#### Parameter  
 DisplayKind\_Value  
 Der Wert des Felds.  
  
 DisplayKind\_Name  
 Name des Felds.  
  
 DisplayKind\_Type  
 Der Typ des Felds.  
  
## Anforderungen  
 Header: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)