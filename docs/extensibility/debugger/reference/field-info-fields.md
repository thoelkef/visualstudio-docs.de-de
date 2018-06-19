---
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d74f39ce8e9e350c791371f20b7401d685fb1d18
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102492"
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
Gibt an, welche Informationen zum Abrufen einer [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## <a name="members"></a>Member  
 FIF_FULLNAME  
 Initialisieren/verwenden die `bstrFullName` -Feld in der [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Struktur.  
  
 FIF_NAME  
 Initialisieren/verwenden die `bstrName` -Feld in der `FIELD_INFO` Struktur.  
  
 FIF_TYPE  
 Initialisieren/verwenden die `bstrType` -Feld in der `FIELD_INFO` Struktur.  
  
 FIF_MODIFIERS  
 Initialisieren/verwenden die `bstrModifiers` -Feld in der `FIELD_INFO` Struktur.  
  
## <a name="remarks"></a>Hinweise  
 Diese Werte werden auch als Argument übergeben der [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) Methode an, welche Felder von der [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Struktur initialisiert werden sollen.  
  
 Diese Werte werden auch verwendet, der `dwFields` Mitglied der `FIELD_INFO` Struktur, um anzugeben, welche Felder verwendet und gültig sind.  
  
 Diese Flags können kombiniert werden, mit einem bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)