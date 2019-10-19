---
title: 'IRemoteDebugApplication110:: setdebuggeroptions | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: e7168a4ef8ec70368c0ff691ba1f721275f9d65d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577426"
---
# <a name="iremotedebugapplication110setdebuggeroptions"></a>IRemoteDebugApplication110::SetDebuggerOptions
Wird aufgerufen, um Debuggeroptionen zu aktualisieren. Diese Methode sollte nach [iremotedebugapplication:: connectdebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)aufgerufen werden. Die [iremotedebugapplication::D isconnectdebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md) -Methode setzt automatisch auf die Standardoptionen zurück. Die Optionen werden standardmäßig auf 0 (SDO_NONE) eingestellt.  
  
> [!IMPORTANT]
> Die [iremotedebuapplication-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md) wird von PDM v 11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetDebuggerOptions(        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,        [in] enum SCRIPT_DEBUGGER_OPTIONS value    );  
```  
  
#### <a name="parameters"></a>Parameter  
 `mask`  
 Die [SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md) -enumerationsmaske.  
  
 `value`  
 Der [SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md) -Enumerationswert.  
  
## <a name="see-also"></a>Siehe auch  
 [Iremotedebuapplication-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)    
 [IRemoteDebugApplication110-Schnittstelle](../../winscript/reference/iremotedebugapplication110-interface.md)