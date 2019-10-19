---
title: 'Iapplicationdebugger:: OnClose | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onClose
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onClose
ms.assetid: f3d6ca9f-6697-4d02-9d1a-16e3859bf282
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e31b2a77effc729f0e7df1e36116ee554446093
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577872"
---
# <a name="iapplicationdebuggeronclose"></a>IApplicationDebugger::onClose
Behandelt ein Ereignis zum Schließen der Debuganwendung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT onClose();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter an.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird aufgerufen, wenn `IDebugApplication::Close` aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Iapplicationdebugger-Schnittstelle](../../winscript/reference/iapplicationdebugger-interface.md)    
 [IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)