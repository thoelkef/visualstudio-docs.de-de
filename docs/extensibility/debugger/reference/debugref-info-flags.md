---
title: "DEBUGREF_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUGREF_INFO_FLAGS"
helpviewer_keywords: 
  - "DEBUGREF_INFO_FLAGS-enumeration"
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# DEBUGREF_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt an, welche über eine Debug\- Verweisobjekt Informationen abzurufen.  
  
## Syntax  
  
```cpp#  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```c#  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## Mitglieder  
 DEBUGREF\_INFORMATION\_NAME  
 Initialisieren Sie verwenden das\/ `bstrName` Feld in der Struktur.  
  
 DEBUGREF\_INFORMATION\_TYPE  
 Initialisieren Sie verwenden das\/ `bstrType` Feld in der Struktur.  
  
 DEBUGREF\_INFORMATION\_VALUE  
 Initialisieren Sie verwenden das\/ `bstrValue` Feld in der Struktur.  
  
 DEBUGREF\_INFORMATION\_ATTRIB  
 Initialisieren Sie verwenden das\/`dwAttrib` Feld in der Struktur.  
  
 DEBUGREF\_INFORMATION\_REFTYPE  
 Initialisieren Sie verwenden das\/ `dwRefType` Feld in der Struktur.  
  
 DEBUGREF\_INFORMATION\_REF  
 Initialisieren Sie verwenden das\/ `pReference` Feld in der Struktur.  
  
 DEBUGREF\_INFORMATION\_VALUE\_AUTOEXPAND  
 Im Feld Wert sollte mit dem AUTO\-erweiterten Wert enthalten, sofern verfügbar, für diesen Objekttyp.  
  
 DEBUGREF\_INFORMATION\_NONE  
 Gibt an, dass keine Flags festgelegt werden.  
  
 DEBUGREF\_INFORMATION\_ALL  
 Gibt eine Maske der Flags an.  
  
## Hinweise  
 Diese Flags werden auf die [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) und [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)\-Methode übergeben, um anzugeben, welche Felder der [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Struktur initialisiert werden sollen.  
  
 Wird für den `dwFields`\-Member der `DEBUG_REFERENCE_INFO` Struktur, um anzugeben, welche Felder verwendet und gültig sind, wenn die Struktur zurückgegeben wird.  
  
 Diese Werte können mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)