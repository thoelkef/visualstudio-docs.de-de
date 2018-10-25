---
title: DISASSEMBLY_FLAGS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f6d42a7c5e9247359abfcdb4d65db5a4e0de247e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916393"
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
Gibt die Flags für die Disassemblierung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_DISASSEMBLY_FLAGS {   
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
public enum enum_DISASSEMBLY_FLAGS {   
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
 Gibt an, dass diese Anweisung in einem anderen Dokument als die vorherige Version.  
  
 DF_DISABLED  
 Gibt an, dass diese Anweisung nicht ausgeführt wird.  
  
 DF_INSTRUCTION_ACTIVE  
 Gibt an, dass diese Anweisung den nächsten Anweisungen ausgeführt werden (möglicherweise mehr als eine).  
  
 DF_DATA  
 Gibt an, dass diese Anweisung wirklich Daten (nicht Code).  
  
 DF_HASSOURCE  
 Gibt an, dass diese Anweisung Quelle verfügt. Einige Anweisungen, z. B. profilerstellung oder Garbage Collection-Code, verfügen über keine entsprechende Quelle.  
  
 DF_DOCUMENT_CHECKSUM  
 Gibt an, dass `bstrDocumentUrl` Feld Prüfsummendaten enthält, nach der Dokument-URL. Finden Sie im Abschnitt "Hinweise" der [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Struktur wie die Prüfsummendaten gespeichert werden.  
  
## <a name="remarks"></a>Hinweise  
 Verwendet als die `dwFlags` Mitglied der [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Struktur.  
  
 Diese Flags können kombiniert werden, mit einer bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)