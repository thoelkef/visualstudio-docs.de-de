---
title: INTERCEPT_EXCEPTION_ACTION | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- INTERCEPT_EXCEPTION_ACTION
helpviewer_keywords:
- INTERCEPT_EXCEPTION_ACTION enumeration
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4fcccffecaf465af36d5e4925d43214ff132756f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147512"
---
# <a name="intercept_exception_action"></a>INTERCEPT_EXCEPTION_ACTION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt an, welche Aktionen ausgeführt werden sollen, wenn Ausnahmen abgefangen werden.  
  
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
 Ermöglicht das Abfangen der aktuellen Ausnahme. Dies ist der einzige Wert, der derzeit unterstützt wird und angegeben werden muss.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Werte werden an die [interceptaccesstexception](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) -Methode übergeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
