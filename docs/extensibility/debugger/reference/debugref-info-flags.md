---
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5864b3503b19e8a473f45e4167aad835181da50
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="debugrefinfoflags"></a>DEBUGREF_INFO_FLAGS
Gibt an, welche Informationen über ein Debug-Verweis-Objekt abgerufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_DEBUGREF_INFO_FLAGS {   
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
  
```csharp  
public enum enum_DEBUGREF_INFO_FLAGS {   
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
  
## <a name="members"></a>Member  
 DEBUGREF_INFO_NAME  
 Die Initialisierung/verwenden die `bstrName` Feld in der Struktur.  
  
 DEBUGREF_INFO_TYPE  
 Die Initialisierung/verwenden die `bstrType` Feld in der Struktur.  
  
 DEBUGREF_INFO_VALUE  
 Die Initialisierung/verwenden die `bstrValue` Feld in der Struktur.  
  
 DEBUGREF_INFO_ATTRIB  
 Die Initialisierung/verwenden die `dwAttrib` Feld in der Struktur.  
  
 DEBUGREF_INFO_REFTYPE  
 Die Initialisierung/verwenden die `dwRefType` Feld in der Struktur.  
  
 DEBUGREF_INFO_REF  
 Die Initialisierung/verwenden die `pReference` Feld in der Struktur.  
  
 DEBUGREF_INFO_VALUE_AUTOEXPAND  
 Das Wertfeld, sollte den Wert automatisch erweitert für diesen Objekttyp enthalten.  
  
 DEBUGREF_INFO_NONE  
 Gibt an, dass keine Flags festgelegt sind.  
  
 DEBUGREF_INFO_ALL  
 Gibt eine Maske der Flags an.  
  
## <a name="remarks"></a>Hinweise  
 Diese Flags werden zum Übergeben der [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) und [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) Methoden, um anzugeben, welche Felder der der [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Struktur initialisiert werden sollen.  
  
 Verwendet für die `dwFields` Mitglied der `DEBUG_REFERENCE_INFO` Struktur, um anzugeben, welche Felder sind gültig und verwendet, wenn die Struktur zurückgegeben wird.  
  
 Diese Werte können kombiniert werden, mit einem bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)