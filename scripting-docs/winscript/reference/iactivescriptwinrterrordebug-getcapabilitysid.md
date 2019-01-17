---
title: IActiveScriptWinRTErrorDebug::GetCapabilitySid | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2e0e9f642e780b745f8b66734893345618a43460
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349821"
---
# <a name="iactivescriptwinrterrordebuggetcapabilitysid"></a>IActiveScriptWinRTErrorDebug::GetCapabilitySid
Gibt die SID-Funktion für den Windows-Runtime-Fehler zurück, sofern verfügbar.  
  
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