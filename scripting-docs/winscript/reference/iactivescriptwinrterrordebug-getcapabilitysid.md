---
title: 'Iactivescriptwinrterrordebug:: getcapabilitysid | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug::GetCapabilitySid
ms.assetid: 469463d2-5e73-4c53-9ffd-d0ca7460aa5c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93bf824dd4d290ca536cb609e24b5d14400a3e3b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577930"
---
# <a name="iactivescriptwinrterrordebuggetcapabilitysid"></a>IActiveScriptWinRTErrorDebug::GetCapabilitySid
Gibt die Funktions-sid für den Windows-Runtime Fehler zurück, falls verfügbar.  
  
> [!IMPORTANT]
> Die [iactivescriptwinrterrordebug-Schnittstelle](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) wird von PDM v 11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetCapabilitySid([out] BSTR * capabilitySid);  
```  
  
#### <a name="parameters"></a>Parameter  
 `capabilitySid`  
 Die Funktions-SID des Fehlers.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptWinRTErrorDebug-Schnittstelle](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)