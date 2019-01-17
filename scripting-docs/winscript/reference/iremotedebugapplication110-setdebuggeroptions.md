---
title: IRemoteDebugApplication110::SetDebuggerOptions | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::SetDebuggerOptions
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74662b6cfcfb641a59ac93c862bd38c6fa16a900
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346773"
---
# <a name="iremotedebugapplication110setdebuggeroptions"></a>IRemoteDebugApplication110::SetDebuggerOptions
Wird aufgerufen, um Optionen für den Debugger zu aktualisieren. Diese Methode sollte aufgerufen werden, nachdem [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md). Die [IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md) Methode automatisch zurückgesetzt wird, um die Standardoptionen. Die Optionen standardmäßig auf 0 (SDO_NONE).  
  
> [!IMPORTANT]
>  [IRemoteDebugApplication-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md) wird implementiert von PDM V11. 0 und höher. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetDebuggerOptions(        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,        [in] enum SCRIPT_DEBUGGER_OPTIONS value    );  
```  
  
#### <a name="parameters"></a>Parameter  
 `mask`  
 Die [SCRIPT_DEBUGGER_OPTIONS-Enumeration](../../winscript/reference/script-debugger-options-enumeration.md) Maske.  
  
 `value`  
 Die [SCRIPT_DEBUGGER_OPTIONS-Enumeration](../../winscript/reference/script-debugger-options-enumeration.md) Wert.  
  
## <a name="see-also"></a>Siehe auch  
 [IRemoteDebugApplication-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110-Schnittstelle](../../winscript/reference/iremotedebugapplication110-interface.md)