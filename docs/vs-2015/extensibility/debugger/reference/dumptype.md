---
title: Dumptype | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e74785f3843f0755cebb5a1f0cd93cf158806d57
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180952"
---
# <a name="dumptype"></a>DUMPTYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt an, wie viel von einem Programmzustand (z. b. das Ausführen von Threads, Stapel Rahmen und aktuelle Anweisungs Adresse) zum Absichern angezeigt werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
typedef DWORD DUMPTYPE;  
```  
  
```csharp  
public enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
```  
  
## <a name="members"></a>Member  
 DUMP_MINIDUMP  
 Gibt ein kleines, kompaktes Abbild an.  
  
 DUMP_FULLDUMP  
 Gibt ein großes, Abbild Abbild an.  
  
## <a name="remarks"></a>Bemerkungen  
 Wird als Argument an die " [Write-Dump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) "-Methode übermittelt.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)
