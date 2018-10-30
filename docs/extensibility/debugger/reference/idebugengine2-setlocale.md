---
title: IDebugEngine2::SetLocale | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5575a96a438cc0dced0e1508776320747bf4d921
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866037"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
Legt das Gebietsschema die Debug-Engine (DE) fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(   
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `wLangID`  
 [in] Gibt das Gebietsschema an. Beispiel: 1033 für Englisch.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird aufgerufen, durch die sitzungsbasierter Debug-Manager (SDM), um den gebietsschemaeinstellungen der IDE weiterzugeben, damit, dass durch die DE zurückgegebene Zeichenfolgen ordnungsgemäß lokalisiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)