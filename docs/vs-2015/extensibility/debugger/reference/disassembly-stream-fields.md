---
title: DISASSEMBLY_STREAM_FIELDS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d65c51f1589d245ab0fcbbfe8c62d77277d925ee
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775796"
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt an, welche Informationen Sie über ein Feld für die Disassembly abzurufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
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
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
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
 Initialisieren und Verwenden der `bstrAddress` Feld.  
  
 DSF_ADDRESSOFFSET  
 Initialisieren und Verwenden der `bstrAddressOffset` Feld.  
  
 DSF_CODEBYTES  
 Initialisieren und Verwenden der `bstrCodeBytes` Feld.  
  
 DSF_OPCODE  
 Initialisieren und Verwenden der `bstrOpCode` Feld.  
  
 DSF_OPERANDS  
 Initialisieren und Verwenden der `bstrOperands` Feld.  
  
 DSF_SYMBOL  
 Initialisieren und Verwenden der `bstrSymbol` Feld.  
  
 DSF_CODELOCATIONID  
 Initialisieren und Verwenden der `uCodeLocationId` Feld.  
  
 DSF_POSITION  
 Initialisieren und Verwenden der `posBeg` und `posEnd` Felder.  
  
 DSF_DOCUMENTURL  
 Initialisieren und Verwenden der `bstrDocumentUrl` Feld.  
  
 DSF_BYTEOFFSET  
 Initialisieren und Verwenden der `dwByteOffset` Feld.  
  
 DSF_FLAGS  
 Initialisieren und Verwenden der `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) Feld.  
  
 DSF_OPERANDS_SYMBOLS  
 Symbolnamen in umfassen die `bstrOperands` Feld.  
  
 DSF_ALL  
 Gibt alle Felder für den Disassembly-Stream an.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Parameter an die [lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) Methode, um die Felder anzugeben der [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) sind, dass die Struktur initialisiert werden.  
  
 Verwendet für die `dwFields` Mitglied der `DisassemblyData` Struktur, um anzugeben, welche Felder sind gültig und verwendet, wenn die Struktur zurückgegeben wird.  
  
 Diese Werte können kombiniert werden, mit einer bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)

