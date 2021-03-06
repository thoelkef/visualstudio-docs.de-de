---
title: THREADPROPERTY_FIELDS | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc0e0f7cae4aed887809c22bda0cd6a9ed50307f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204811"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt an, welche Informationen über einen Thread abgerufen werden sollen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```csharp  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Member  
 TPF_ID  
 Initialisieren/verwenden Sie das- `dwThreadId` Feld der [Thread Properties](../../../extensibility/debugger/reference/threadproperties.md) -Struktur.  
  
 TPF_SUSPENDCOUNT  
 Initialisieren/verwenden Sie das- `dwSuspendCount` Feld der `THREADPROPERTIE` S-Struktur.  
  
 TPF_STATE  
 Initialisieren/verwenden Sie das- `dwThreadState` Feld der `THREADPROPERTIE` S-Struktur.  
  
 TPF_PRIORITY  
 Initialisieren/verwenden Sie das- `bstrPriority` Feld der `THREADPROPERTIE` S-Struktur.  
  
 TPF_NAME  
 Initialisieren/verwenden Sie das- `bstrName` Feld der `THREADPROPERTIE` S-Struktur.  
  
 TPF_LOCATION  
 Initialisieren/verwenden Sie das- `bstrLocation` Feld der `THREADPROPERTIE` S-Struktur.  
  
 TPF_ALLFIELDS  
 Gibt alle Felder an.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Werte werden als Argument an die [getthreadproperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) -Methode übermittelt, um anzugeben, welche Felder der [Thread Properties](../../../extensibility/debugger/reference/threadproperties.md) -Struktur initialisiert werden sollen.  
  
 Diese Werte werden auch im- `dwFields` Member der `THREADPROPERTIES` -Struktur verwendet, um anzugeben, welche Felder verwendet und gültig sind.  
  
 Diese Flags können mit einem bitweisen kombiniert werden `OR` .  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Thread Properties](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
