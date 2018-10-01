---
title: INTERCEPT_EXCEPTION_ACTION | Microsoft-Dokumentation
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
- INTERCEPT_EXCEPTION_ACTION
helpviewer_keywords:
- INTERCEPT_EXCEPTION_ACTION enumeration
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9625518ac1f24ffec41ef61a2c3c1bcf6ec0bce
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516034"
---
# <a name="interceptexceptionaction"></a>INTERCEPT_EXCEPTION_ACTION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [INTERCEPT_EXCEPTION_ACTION](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/intercept-exception-action).  
  
Gibt an, welche Aktionen an, die beim Abfangen von Ausnahmen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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

