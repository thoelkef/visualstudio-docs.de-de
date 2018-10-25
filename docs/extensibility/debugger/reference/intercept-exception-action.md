---
title: INTERCEPT_EXCEPTION_ACTION | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- INTERCEPT_EXCEPTION_ACTION
helpviewer_keywords:
- INTERCEPT_EXCEPTION_ACTION enumeration
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1249e6b435f7cd396ea7912cb7aebf8d78cf94f7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948381"
---
# <a name="interceptexceptionaction"></a>INTERCEPT_EXCEPTION_ACTION
Gibt an, welche Aktionen an, die beim Abfangen von Ausnahmen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_INTERCEPT_EXCEPTION_ACTION  
{  
   IEA_INTERCEPT = 0x0001  
}  
typedef DWORD INTERCEPT_EXCEPTION_ACTION;  
```  
  
```csharp  
public enum enum_INTERCEPT_EXCEPTION_ACTION  
{  
   IEA_INTERCEPT = 0x0001  
}  
```  
  
#### <a name="parameters"></a>Parameter  
 IEA_INTERCEPT  
 Ermöglicht das Abfangen von der aktuellen Ausnahme. Dies ist der einzige derzeit unterstützte Wert und muss angegeben werden.  
  
## <a name="remarks"></a>Hinweise  
 Diese Werte werden übergeben, in der [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)