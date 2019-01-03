---
title: AD_PROCESS_ID_TYPE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f27791b555d2f18e1e0a338bbfb5893f9047fd4e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53819590"
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
Gibt an, wie eine Prozess-ID interpretieren die [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```csharp  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## <a name="members"></a>Member  
 AD_PROCESS_ID_SYSTEM  
 Prozess-ID ist ein Systembezeichner. Verwenden der `ProcessId.dwProcessId` Feld der [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur.  
  
 AD_PROCESS_ID_GUID  
 Prozess-ID ist eine GUID. Verwenden der `ProcessId.guidProcessId` Feld der `AD_PROCESS_ID` Struktur.  
  
## <a name="remarks"></a>Hinweise  
 Verwendet für die `ProcessIdType` Mitglied der [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur, die den Typ des Prozess-ID zu identifizieren, die in der Struktur enthalten ist. Bestimmt, wie zum Interpretieren der `ProcessId` union in der Struktur.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)