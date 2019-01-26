---
title: CONTEXT_INFO_FIELDS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 712876c38996b0e9b5f0b65cf0b0269d43b15907
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028430"
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
Gibt an, welche Informationen Sie über eine Speicherkontext abzurufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## <a name="members"></a>Member  
 CIF_MODULEURL  
 Initialisieren und Verwenden der `bstrModuleUrl` Feld der [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Struktur.  
  
 CIF_FUNCTION  
 Initialisieren und Verwenden der `bstrFunction` Feld der `CONTEXT_INFO` Struktur.  
  
 CIF_FUNCTIONOFFSET  
 Initialisieren und Verwenden der `posFunctionOffset` Feld der `CONTEXT_INFO` Struktur.  
  
 CIF_ADDRESS  
 Initialisieren und Verwenden der `bstrAddress` Feld der `CONTEXT_INFO` Struktur.  
  
 CIF_ADDRESSOFFSET  
 Initialisieren und Verwenden der `bstrAddressOffset` Feld der `CONTEXT_INFO` Struktur.  
  
 CIF_ALLFIELDS  
 Alle Felder initialisiert und Verwenden der `CONTEXT_INFO` Struktur.  
  
## <a name="remarks"></a>Hinweise  
 Diese Werte werden übergeben einen Parameter für die [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) Methode, um die Felder anzugeben der [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) sind, dass die Struktur initialisiert werden.  
  
 Diese Flags werden auch verwendet, welche Felder der an die `CONTEXT_INFO` -Struktur sind gültig und verwendet, wenn die Struktur zurückgegeben wird.  
  
 Diese Werte können mit einem bitweisen OR kombiniert werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)