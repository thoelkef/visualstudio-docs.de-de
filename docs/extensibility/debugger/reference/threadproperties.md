---
title: THREADPROPERTIES | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14db7869717a2edf1ac64be744ab1f6058455c1a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845315"
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
 Eine Kombination von Flags aus der [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) Enumeration, die beschreibt, welche Felder in dieser Struktur gültig sind.  
  
 dwThreadId  
 Die Thread-ID.  
  
 dwSuspendCount  
 Das Anhalten des Threads Anzahl.  
  
 dwThreadState  
 Ein Wert aus der [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) Enumeration, die den Zustand des Betriebssystem Threads angibt.  
  
 bstrPriority  
 Eine Zeichenfolge, die die Priorität des Threads angibt. z. B. "Höher als Normal", "Normal" oder "Time Critical".  
  
 bstName  
 Der Threadname.  
  
 bstrLocation  
 Der Threadspeicherort (in der Regel den obersten Stapelrahmen), ausgedrückt in der Regel als Name der Methode, in dem Ausführung zurzeit angehalten wird.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird ausgefüllt, durch einen Aufruf der [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) Methode. Die Informationen zurückgegeben, daher wird normalerweise verwendet, füllen die **Threads** Fenster.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)