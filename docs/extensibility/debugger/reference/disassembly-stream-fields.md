---
title: DISASSEMBLY_STREAM_FIELDS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a8735992574699ba2b108fc493e9003ca52c9b2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
Gibt an, welche Informationen Sie über ein Feld für die Disassembly abzurufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
typedef DWORD DISASSEMBLY_STREAM_FIELDS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
```  
  
## <a name="members"></a>Member  
 DSF_ADDRESS  
 Die Initialisierung/verwenden die `bstrAddress` Feld.  
  
 DSF_ADDRESSOFFSET  
 Die Initialisierung/verwenden die `bstrAddressOffset` Feld.  
  
 DSF_CODEBYTES  
 Die Initialisierung/verwenden die `bstrCodeBytes` Feld.  
  
 DSF_OPCODE  
 Die Initialisierung/verwenden die `bstrOpCode` Feld.  
  
 DSF_OPERANDS  
 Die Initialisierung/verwenden die `bstrOperands` Feld.  
  
 DSF_SYMBOL  
 Die Initialisierung/verwenden die `bstrSymbol` Feld.  
  
 DSF_CODELOCATIONID  
 Die Initialisierung/verwenden die `uCodeLocationId` Feld.  
  
 DSF_POSITION  
 Die Initialisierung/verwenden die `posBeg` und `posEnd` Felder.  
  
 DSF_DOCUMENTURL  
 Die Initialisierung/verwenden die `bstrDocumentUrl` Feld.  
  
 DSF_BYTEOFFSET  
 Die Initialisierung/verwenden die `dwByteOffset` Feld.  
  
 DSF_FLAGS  
 Die Initialisierung/verwenden die `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) Feld.  
  
 DSF_OPERANDS_SYMBOLS  
 Symbolnamen dürfen in umfassen die `bstrOperands` Feld.  
  
 DSF_ALL  
 Gibt alle Felder für die Disassembly-Datenstrom.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Parameter an die [lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) Methode, um anzugeben, welche Felder von der [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Struktur initialisiert werden, sind.  
  
 Verwendet für die `dwFields` Mitglied der `DisassemblyData` Struktur, um anzugeben, welche Felder sind gültig und verwendet, wenn die Struktur zurückgegeben wird.  
  
 Diese Werte können kombiniert werden, mit einem bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)