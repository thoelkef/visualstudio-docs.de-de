---
title: Idebugapplication::D ebugoutput | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.DebugOutput
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::DebugOutput
ms.assetid: 6c02939c-3c2d-474a-ab15-49a37e22b4a7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d52acf0e4b32f0ced63b53a6b37ffe62f1d948e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575021"
---
# <a name="idebugapplicationdebugoutput"></a>IDebugApplication::DebugOutput
Bewirkt, dass die angegebene Zeichenfolge von der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Debugger angezeigt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT DebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstr`  
 in Zeichenfolge, die im Debugger angezeigt werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ermöglicht einer Sprach-Engine, die sprachspezifische debuggabeunterstützung zu implementieren. Die Zeichenfolge wird in der Regel im Ausgabefenster des Debuggers angezeigt.  
  
 Diese Methode bewirkt, dass `IApplicationDebugger::onDebugOutput` aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugapplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)