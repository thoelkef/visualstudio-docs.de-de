---
title: DEBUGREF_INFO_FLAGS | Microsoft-Dokumentation
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
ms.openlocfilehash: 9957b0aaf81048c5040e3f7ff54f3fa9be742dc1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858562"
---
# <a name="debugrefinfoflags"></a>DEBUGREF_INFO_FLAGS
Gibt an, welche Informationen Sie über ein Debug-Verweis-Objekt abzurufen.  
  
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
 Initialisieren und Verwenden der `bstrName` Feld in der Struktur.  
  
 DEBUGREF_INFO_TYPE  
 Initialisieren und Verwenden der `bstrType` Feld in der Struktur.  
  
 DEBUGREF_INFO_VALUE  
 Initialisieren und Verwenden der `bstrValue` Feld in der Struktur.  
  
 DEBUGREF_INFO_ATTRIB  
 Initialisieren und Verwenden der `dwAttrib` Feld in der Struktur.  
  
 DEBUGREF_INFO_REFTYPE  
 Initialisieren und Verwenden der `dwRefType` Feld in der Struktur.  
  
 DEBUGREF_INFO_REF  
 Initialisieren und Verwenden der `pReference` Feld in der Struktur.  
  
 DEBUGREF_INFO_VALUE_AUTOEXPAND  
 Feld mit dem Wert sollte den Wert automatisch erweitert, für diesen Objekttyp enthalten.  
  
 DEBUGREF_INFO_NONE  
 Gibt an, dass keine Flags festgelegt sind.  
  
 DEBUGREF_INFO_ALL  
 Gibt eine Maske der Flags an.  
  
## <a name="remarks"></a>Hinweise  
 Diese Flags werden an übergeben der [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) und [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) Methoden zum Erkennen der Felder der [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) sind, dass die Struktur initialisiert werden.  
  
 Verwendet für die `dwFields` Mitglied der `DEBUG_REFERENCE_INFO` Struktur, um anzugeben, welche Felder sind gültig und verwendet, wenn die Struktur zurückgegeben wird.  
  
 Diese Werte können kombiniert werden, mit einer bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)