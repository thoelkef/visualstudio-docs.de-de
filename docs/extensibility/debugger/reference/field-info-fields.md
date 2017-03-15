---
title: "FIELD_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_INFO_FIELDS"
helpviewer_keywords: 
  - "FIELD_INFO_FIELDS-enumeration"
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# FIELD_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt an, welche Informationen über ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekt abzurufen.  
  
## Syntax  
  
```cpp#  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```c#  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## Mitglieder  
 FIF\_FULLNAME  
 Initialisieren Sie verwenden das\/ `bstrFullName` Feld in der [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) Struktur.  
  
 FIF\_NAME  
 Initialisieren Sie verwenden das\/ `bstrName` Feld in der `FIELD_INFO` Struktur.  
  
 FIF\_TYPE  
 Initialisieren Sie verwenden das\/ `bstrType` Feld in der `FIELD_INFO` Struktur.  
  
 FIF\_MODIFIERS  
 Initialisieren Sie verwenden das\/ `bstrModifiers` Feld in der `FIELD_INFO` Struktur.  
  
## Hinweise  
 Diese Werte werden auch als Argument an die [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)\-Methode übergeben, um anzugeben, welche Felder der [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) Struktur initialisiert werden sollen.  
  
 Diese Werte werden auch im `dwFields`\-Member der `FIELD_INFO` Struktur verwendet, um anzugeben, welche Felder verwendet und gültig sind.  
  
 Diese Flags werden mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)