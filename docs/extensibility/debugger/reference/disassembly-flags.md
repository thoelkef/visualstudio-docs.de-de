---
title: "DISASSEMBLY_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_FLAGS"
helpviewer_keywords: 
  - "DISASSEMBLY_FLAGS-enumeration"
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DISASSEMBLY_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt Flags für die Disassembly anzeigen.  
  
## Syntax  
  
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
  
```c#  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## Mitglieder  
 DF\_DOCUMENTCHANGE  
 Gibt an, dass diese Anweisung in einem anderen Dokument als die vorherige ist.  
  
 DF\_DISABLED  
 Gibt an, dass diese Anweisung nicht ausgeführt wird.  
  
 DF\_INSTRUCTION\_ACTIVE  
 Gibt an, dass diese Anweisung eine der folgenden Anweisungen ausgeführt werden soll \(es gibt mehrere\).  
  
 DF\_DATA  
 Gibt an, dass die Daten tatsächlich Anweisung \(kein Code\).  
  
 DF\_HASSOURCE  
 Gibt an, dass diese Anweisung Quelle hat.  Einige Anweisungen, z. B. die Profilerstellung oder Garbage Collections\-Code, haben keine entsprechende Quelle.  
  
 DF\_DOCUMENT\_CHECKSUM  
 Gibt an, dass `bstrDocumentUrl` Feld Prüfsummendaten nach dem Dokument URL enthält.  Weitere Informationen finden Sie im Abschnitt " Hinweise " für die [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Struktur für, wie die Prüfsummendaten gespeichert wird.  
  
## Hinweise  
 Wird als `dwFlags`\-Member der [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Struktur.  
  
 Diese Flags werden mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)