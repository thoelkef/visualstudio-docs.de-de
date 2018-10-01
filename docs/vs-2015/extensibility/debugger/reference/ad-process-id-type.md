---
title: AD_PROCESS_ID_TYPE | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c9327c84b8cdac8eab1a00b7dd2b665456dcaaa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513406"
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [AD_PROCESS_ID_TYPE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ad-process-id-type).  
  
Gibt an, wie eine Prozess-ID interpretieren die [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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

