---
title: "THREADPROPERTIES | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "THREADPROPERTIES"
helpviewer_keywords: 
  - "THREADPROPERTIES-Struktur"
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# THREADPROPERTIES
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beschreibt die Eigenschaften eines Threads.  
  
## Syntax  
  
```cpp#  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```c#  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## Mitglieder  
 dwFields  
 Eine Kombination von Flags aus der [THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)\-Enumeration beschreiben, welche Felder in der Struktur gültig sind.  
  
 dwThreadId  
 Die Thread ID.  
  
 dwSuspendCount  
 Der Threadunterbrechungszähler.  
  
 dwThreadState  
 Ein Wert aus der [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)\-Enumeration, der den Zustand des Ausführen von Threads angibt.  
  
 bstrPriority  
 Eine Zeichenfolge, die die Threadpriorität angibt. Beispielsweise „Normal“, „Normal“ oder „Zeitpunkt wichtig“.  
  
 bstName  
 Der Name des Threads.  
  
 bstrLocation  
 Der Threadspeicherort \(normalerweise der oberste Stapelrahmen\), ausgedrückt in der Regel als Name der Methode, in der Ausführung derzeit angehalten wird.  
  
## Hinweise  
 Diese Struktur wird von einem Aufruf der [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)\-Methode gefüllt.  Die Informationen, die zurückgegeben werden, werden in der Regel verwendet, wenn das Fenster **Threads** auffüllt.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)