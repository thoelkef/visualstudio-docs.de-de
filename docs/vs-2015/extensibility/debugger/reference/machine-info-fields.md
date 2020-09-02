---
title: MACHINE_INFO_FIELDS | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cce5300a795922162f2e0b979e553f4235ceacc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147447"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt an, welche Art von Informationen für einen bestimmten Computer abgerufen werden sollen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
typedef DWORD MACHINE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
```  
  
## <a name="members"></a>Member  
 MCIF_NAME  
 Initialisieren/verwenden Sie das- `bstrName` Feld in der-Struktur.  
  
 MCIF_FLAGS  
 Initialisieren/verwenden Sie das- `Flags` Feld in der-Struktur.  
  
 MIF_ALL  
 Initialisieren/verwenden Sie alle Felder in der Struktur.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Werte werden an die [getmachineingefo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) -Methode übermittelt, um anzugeben, welche Member der [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) Struktur initialisiert werden sollen.  
  
 Wird auch im- `Fields` Member der `MACHINE_INFO` -Struktur verwendet, um anzugeben, welche Felder verwendet und gültig sind.  
  
 Diese Flags können mit einem bitweisen kombiniert werden `OR` .  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
