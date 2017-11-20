---
title: IActiveScriptWinRTErrorDebug::GetCapabilitySid | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptWinRTErrorDebug::GetCapabilitySid
ms.assetid: 469463d2-5e73-4c53-9ffd-d0ca7460aa5c
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78d53b498ba88fae50cfaca106a65a2bb07d21a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptwinrterrordebuggetcapabilitysid"></a>IActiveScriptWinRTErrorDebug::GetCapabilitySid
Gibt die Funktion SID für den Windows-Runtime-Fehler zurück, sofern verfügbar.  
  
> [!IMPORTANT]
>  [IActiveScriptWinRTErrorDebug-Schnittstelle](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) wird implementiert von PDM V11. 0 und höher. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetCapabilitySid([out] BSTR * capabilitySid);  
```  
  
#### <a name="parameters"></a>Parameter  
 `capabilitySid`  
 Die Funktion die SID des Fehlers.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptWinRTErrorDebug-Schnittstelle](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)