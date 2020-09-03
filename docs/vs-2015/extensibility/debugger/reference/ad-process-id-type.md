---
title: AD_PROCESS_ID_TYPE | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d471a73205383f0f23c5016872712a3ba2c578d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153618"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt an, wie eine Prozess-ID in der [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur interpretiert werden soll.  
  
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
 Die Prozess-ID ist ein System Bezeichner. Verwenden Sie das- `ProcessId.dwProcessId` Feld der [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur.  
  
 AD_PROCESS_ID_GUID  
 Die Prozess-ID ist eine GUID. Verwenden Sie das- `ProcessId.guidProcessId` Feld der- `AD_PROCESS_ID` Struktur.  
  
## <a name="remarks"></a>Bemerkungen  
 Wird für den `ProcessIdType` Member der [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur verwendet, um den Typ der Prozess-ID zu identifizieren, der in der Struktur enthalten ist. Bestimmt, wie die `ProcessId` Union in der-Struktur interpretiert wird.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
