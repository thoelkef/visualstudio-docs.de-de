---
title: CONTEXT_INFO_FIELDS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 05616ba660af188c26f192b97e29d5b60e04fe8a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100659"
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
Gibt an, welche Informationen Sie über eine Speicherkontext abzurufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_CONTEXT_INFO_FIELDS {   
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
 Die Initialisierung/verwenden die `bstrModuleUrl` Feld der [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Struktur.  
  
 CIF_FUNCTION  
 Die Initialisierung/verwenden die `bstrFunction` Feld der `CONTEXT_INFO` Struktur.  
  
 CIF_FUNCTIONOFFSET  
 Die Initialisierung/verwenden die `posFunctionOffset` Feld der `CONTEXT_INFO` Struktur.  
  
 CIF_ADDRESS  
 Die Initialisierung/verwenden die `bstrAddress` Feld der `CONTEXT_INFO` Struktur.  
  
 CIF_ADDRESSOFFSET  
 Die Initialisierung/verwenden die `bstrAddressOffset` Feld der `CONTEXT_INFO` Struktur.  
  
 CIF_ALLFIELDS  
 Alle Felder des initialisieren/verwenden die `CONTEXT_INFO` Struktur.  
  
## <a name="remarks"></a>Hinweise  
 Diese Werte werden Parameter an übergeben der [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) Methode, um anzugeben, welche Felder von der [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Struktur initialisiert werden sollen.  
  
 Diese Flags werden auch verwendet, um anzugeben, welche Felder von der `CONTEXT_INFO` Struktur verwendet und gültig sind, wenn die Struktur zurückgegeben wird.  
  
 Diese Werte können mit einem bitweisen OR kombiniert werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)