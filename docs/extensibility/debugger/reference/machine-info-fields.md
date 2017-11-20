---
title: MACHINE_INFO_FIELDS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MACHINE_INFO_FIELDS
helpviewer_keywords: MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 428d5cd0eccc67c95c1866afed139402ad1c22cb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="machineinfofields"></a>MACHINE_INFO_FIELDS
Gibt an, welche Art von Informationen für einen bestimmten Computer abgerufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
typedef DWORD MACHINE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
```  
  
## <a name="members"></a>Member  
 MCIF_NAME  
 Die Initialisierung/verwenden die `bstrName` Feld in der Struktur.  
  
 MCIF_FLAGS  
 Die Initialisierung/verwenden die `Flags` Feld in der Struktur.  
  
 MIF_ALL  
 Verwenden Sie die Initialisierung/alle Felder in der Struktur.  
  
## <a name="remarks"></a>Hinweise  
 Diese Werte werden an übergeben der [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) Methode, um anzugeben, welche Member der der [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) Struktur initialisiert werden sollen.  
  
 Auch in verwendet das `Fields` Mitglied der `MACHINE_INFO` Struktur, um anzugeben, welche Felder verwendet und gültig sind.  
  
 Diese Flags können kombiniert werden, mit einem bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)