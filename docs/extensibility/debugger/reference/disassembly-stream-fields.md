---
title: "DISASSEMBLY_STREAM_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_STREAM_FIELDS"
helpviewer_keywords: 
  - "DISASSEMBLY_STREAM_FIELDS-enumeration"
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# DISASSEMBLY_STREAM_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt an, welche über ein Feld Disassemblys Informationen abzurufen.  
  
## Syntax  
  
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
  
```c#  
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
  
## Mitglieder  
 DSF\_ADDRESS  
 Initialisieren Sie das Feld `bstrAddress` \/verwenden.  
  
 DSF\_ADDRESSOFFSET  
 Initialisieren Sie das Feld `bstrAddressOffset` \/verwenden.  
  
 DSF\_CODEBYTES  
 Initialisieren Sie das Feld `bstrCodeBytes` \/verwenden.  
  
 DSF\_OPCODE  
 Initialisieren Sie das Feld `bstrOpCode` \/verwenden.  
  
 DSF\_OPERANDS  
 Initialisieren Sie das Feld `bstrOperands` \/verwenden.  
  
 DSF\_SYMBOL  
 Initialisieren Sie das Feld `bstrSymbol` \/verwenden.  
  
 DSF\_CODELOCATIONID  
 Initialisieren Sie das Feld `uCodeLocationId` \/verwenden.  
  
 DSF\_POSITION  
 Initialisieren Sie die `posBeg` \/verwenden, und `posEnd` Felder.  
  
 DSF\_DOCUMENTURL  
 Initialisieren Sie das Feld `bstrDocumentUrl` \/verwenden.  
  
 DSF\_BYTEOFFSET  
 Initialisieren Sie das Feld `dwByteOffset` \/verwenden.  
  
 DSF\_FLAGS  
 Initialisieren Sie das Feld\/verwenden, `dwFlags` \([DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)\).  
  
 DSF\_OPERANDS\_SYMBOLS  
 Zu den Namen `bstrOperands` Feld auf dem Symbol.  
  
 DSF\_ALL  
 Gibt alle Felder für den Disassemblysdatenstrom an.  
  
## Hinweise  
 Übergabe als Parameter an die [Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)\-Methode, um anzugeben, welche Felder der [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Struktur initialisiert werden sollen.  
  
 Wird für den `dwFields`\-Member der `DisassemblyData` Struktur, um anzugeben, welche Felder verwendet und gültig sind, wenn die Struktur zurückgegeben wird.  
  
 Diese Werte können mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)