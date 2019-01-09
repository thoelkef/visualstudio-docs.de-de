---
title: IDebugApplication::StartDebugSession | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.StartDebugSession
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::StartDebugSession
ms.assetid: 737f8424-bbcf-473f-9cf1-6601b9aa250d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 453286e310a6f16576d947cceb1947945f8627d3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086488"
---
# <a name="idebugapplicationstartdebugsession"></a>IDebugApplication::StartDebugSession
Startet die standardmäßigen Debugger integrierten Entwicklungsumgebung (IDE), und fügt eine Debugsitzung dieser Anwendung, wenn noch nicht angefügt ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT StartDebugSession();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode akzeptiert keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird verwendet, um just-in-Time-Debuggen zu implementieren.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)