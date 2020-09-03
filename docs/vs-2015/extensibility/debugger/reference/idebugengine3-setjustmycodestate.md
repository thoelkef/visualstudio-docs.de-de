---
title: 'IDebugEngine3:: setjustmycodestate | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebaf697bfdfff435c12eee1002ff93f4eba7ed65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195865"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode teilt der Debug-Engine die Statusinformationen "justMyCode" mit.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `fUpdate`  
 in Ungleich NULL ( `TRUE` ) zum Aktualisieren aktueller Informationen, 0 (null), `FALSE` um alle Informationen zurückzusetzen (wobei zuvor festgelegte Elemente ignoriert werden).  
  
 `dwModules`  
 in Anzahl von Informationsstrukturen in `rgJMCSpec.`  
  
 `rgJMCSpec`  
 in Array der zu verwendenden [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Strukturen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 JustMyCode ist das Konzept, nur den Code zu debuggen, der einem Benutzer angehört, und alle zwischen Codes, wie z. b. Systemcode, zu ignorieren – auch wenn Quellcode für diesen Systemcode verfügbar ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
