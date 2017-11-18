---
title: THREADPROPERTIES | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: THREADPROPERTIES
helpviewer_keywords: THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b4ec394deef3b317d91e6cbe22bbc1d95a6aca5e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="threadproperties"></a>THREADPROPERTIES
Beschreibt die Eigenschaften eines Threads.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
  
```csharp  
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
  
## <a name="members"></a>Member  
 dwFields  
 Eine Kombination aus Flags aus der [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) Enumeration, die beschreiben, welche Felder in dieser Struktur gültig sind.  
  
 dwThreadId  
 Die Thread-ID.  
  
 dwSuspendCount  
 Anzahl Anhalten des Threads vor.  
  
 dwThreadState  
 Ein Wert aus der [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) Enumeration, die den Status des Betriebsmodus Threads.  
  
 bstrPriority  
 Eine Zeichenfolge, die die Priorität des Threads angibt. z. B. "Höher als Normal", "Normal" oder "Kritisch Zeit".  
  
 bstName  
 Threadname.  
  
 bstrLocation  
 Threadspeicherort (in der Regel den obersten Stapelrahmen), ausgedrückt in der Regel als den Namen der Methode, in dem Ausführung derzeit angehalten wird.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird ausgefüllt, durch einen Aufruf der [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) Methode. Daher zurückgegebene Informationen wird normalerweise verwendet, Füllen der **Threads** Fenster.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)