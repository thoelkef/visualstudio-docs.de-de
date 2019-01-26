---
title: IDebugExceptionEvent2::CanPassToDebuggee | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ccf980fb3d5b357b6211674ca8b99132d81fae1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041008"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Bestimmt, ob die Debug-Engine (DE) die Möglichkeit unterstützt, übergeben diese Ausnahme an die Anwendung gedebuggt wird, wenn die Ausführung fortsetzt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` (die Ausnahme kann an das Programm übergeben werden) oder `S_FALSE` (die Ausnahme kann nicht auf übergeben werden).  
  
## <a name="remarks"></a>Hinweise  
 Die DE muss es sich um eine Standardaktion für die Übergabe an die zu debuggende Komponente verfügen. Die IDE wird möglicherweise die [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) Ereignis, und rufen die [Weiter](../../../extensibility/debugger/reference/idebugprocess3-continue.md) -Methode ohne Aufruf der `CanPassToDebuggee` Methode. Aus diesem Grund müssen die DE Standardfall übergeben Sie die Ausnahme auf, oder nicht.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)