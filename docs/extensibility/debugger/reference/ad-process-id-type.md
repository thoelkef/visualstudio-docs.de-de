---
title: AD_PROCESS_ID_TYPE | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 1fa934610778479551d411a4b231a4b190f29bcd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937407"
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