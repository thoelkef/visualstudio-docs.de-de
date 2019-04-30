---
title: IDebugApplication::DebugOutput | Microsoft-Dokumentation
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
ms.openlocfilehash: a67a16e3fd4868726087df6f2596571d14630f80
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990965"
---
# <a name="idebugapplicationdebugoutput"></a>IDebugApplication::DebugOutput
Bewirkt, dass die angegebene Zeichenfolge von der Debugger-integrierten Entwicklungsumgebung (IDE) angezeigt werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT DebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstr`  
 [in] Die Zeichenfolge, die im Debugger angezeigt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ermöglicht eine Sprach-Engine, um sprachspezifische Debugunterstützung Ausgabe implementieren. Die Zeichenfolge wird in der Regel im Ausgabefenster des Debuggers angezeigt.  
  
 Diese Methode bewirkt, dass `IApplicationDebugger::onDebugOutput` aufgerufen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)