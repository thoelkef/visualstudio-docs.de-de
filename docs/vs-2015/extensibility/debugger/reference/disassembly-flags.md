---
title: DISASSEMBLY_FLAGS | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d48fcf9dd941194b56e2c794ad7f5673f8e58421
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159313"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt die Flags für die Disassembly an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>Member  
 DF_DOCUMENTCHANGE  
 Gibt an, dass sich diese Anweisung in einem anderen Dokument als die vorherige Anweisung befindet.  
  
 DF_DISABLED  
 Gibt an, dass diese Anweisung nicht ausgeführt wird.  
  
 DF_INSTRUCTION_ACTIVE  
 Gibt an, dass es sich bei dieser Anweisung um eine der nächsten auszuführenden Anweisungen handelt (möglicherweise gibt es mehr als eine).  
  
 DF_DATA  
 Gibt an, dass diese Anweisung wirklich Daten (nicht Code) ist.  
  
 DF_HASSOURCE  
 Gibt an, dass diese Anweisung über eine Quelle verfügt. Einige Anweisungen, wie z. b. Profilerstellung oder Garbage Collection Code, verfügen nicht über die entsprechende Quelle.  
  
 DF_DOCUMENT_CHECKSUM  
 Gibt an, dass das `bstrDocumentUrl` Feld Prüfsummen Daten nach der Dokument-URL enthält. Weitere Informationen zur Speicherung der Prüfsummen Daten finden Sie im Abschnitt "Hinweise" für die [disassemblydata](../../../extensibility/debugger/reference/disassemblydata.md) -Struktur.  
  
## <a name="remarks"></a>Bemerkungen  
 Wird als `dwFlags` Member der [disassemblydata](../../../extensibility/debugger/reference/disassemblydata.md) -Struktur verwendet.  
  
 Diese Flags können mit einem bitweisen kombiniert werden `OR` .  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
