---
title: Thread Properties | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4815a1e42b98fba812e8a3c2a53516bff16081db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204820"
---
# <a name="threadproperties"></a>THREADPROPERTIES
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Beschreibt die Eigenschaften eines Threads.  
  
## <a name="syntax"></a>Syntax  
  
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
 dwfields  
 Eine Kombination von Flags aus der [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) Enumeration, die beschreibt, welche Felder in dieser Struktur gültig sind.  
  
 dwthreadid  
 Die Thread-ID.  
  
 dwsuspendcount  
 Die Thread Anzahl für den Thread.  
  
 dwthreadstate  
 Ein Wert aus der [ThreadState](../../../extensibility/debugger/reference/threadstate.md) -Enumeration, der den Status des Betriebs Threads angibt.  
  
 bstraupriority  
 Eine Zeichenfolge, die die Thread Priorität angibt. Beispiel: "oberhalb normal", "Normal" oder "Zeit kritisch".  
  
 bstname  
 Der Thread Name.  
  
 bstrinlocation  
 Der Thread Speicherort (in der Regel der oberste Stapel Rahmen), der in der Regel als Name der Methode ausgedrückt wird, in der die Ausführung zurzeit angehalten wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Struktur wird durch einen Aufrufen der [getthreadproperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) -Methode ausgefüllt. Die Informationen, die zurückgegeben werden, werden in der Regel zum Auffüllen des **Thread** Fensters verwendet.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Getthreadproperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [ThreadState](../../../extensibility/debugger/reference/threadstate.md)
