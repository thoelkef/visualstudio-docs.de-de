---
title: "JMC_CODE_SPEC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "JMC_CODE_SPEC"
helpviewer_keywords: 
  - "JMC_CODE_SPEC-Struktur"
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# JMC_CODE_SPEC
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Struktur wird verwendet, um die JustMyCode\-Informationen für ein Modul festzulegen.  
  
## Syntax  
  
```cpp#  
typedef struct _JMC_CODE_SPEC {  
   BOOL fIsUserCode;  
   BSTR bstrModuleName;  
} JMC_CODE_SPEC;  
```  
  
```c#  
public struct JMC_CODE_SPEC {  
   public int    fIsUserCode;  
   public string bstrModuleName;  
};  
```  
  
## Mitglieder  
 fIsUserCode  
 Ein Wert ungleich 0 \(`TRUE`\), wenn das Modul gelten soll als Benutzercode. Andernfalls`FALSE`\(null\), wenn das Modul als externer Code behandelt und nicht gedebuggt werden soll.  
  
 bstrModuleName  
 Name des Moduls fragliche.  
  
## Hinweise  
 Diese Struktur wird als Liste dieser Strukturen zur [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)\-Methode übergeben.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)