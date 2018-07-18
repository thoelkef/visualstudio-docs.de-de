---
title: DUMPTYPE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa44dfa59f4883fa29a1724344124267f28bce9f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099635"
---
# <a name="dumptype"></a>DUMPTYPE
Gibt an, welcher Anteil der Programmzustand (z. B. ausgeführten Threads, Stapelrahmen und aktuelle Anweisungsadresse) zu speichern.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
typedef DWORD DUMPTYPE;  
```  
  
```csharp  
public enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
```  
  
## <a name="members"></a>Member  
 DUMP_MINIDUMP  
 Gibt eine kleine, compact-Dump an.  
  
 DUMP_FULLDUMP  
 Gibt einen großen, vollständigen Dump an.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Argument an die [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)