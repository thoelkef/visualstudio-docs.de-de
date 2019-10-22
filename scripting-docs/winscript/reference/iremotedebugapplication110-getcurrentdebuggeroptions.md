---
title: 'IRemoteDebugApplication110:: GetCurrentDebuggerOptions | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetCurrentDebuggerOptions
ms.assetid: a6e9cae1-e8f3-4d62-b133-52e9ca12ba7a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6ae042a5d4d1c1ee350b328fdc5a9b7420d9928
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577431"
---
# <a name="iremotedebugapplication110getcurrentdebuggeroptions"></a>IRemoteDebugApplication110::GetCurrentDebuggerOptions
Gibt den Satz von Optionen zurück, die derzeit aktiviert sind.  
  
> [!IMPORTANT]
> Die [iremotedebuapplication-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md) wird von PDM v 11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetCurrentDebuggerOptions([out] enum SCRIPT_DEBUGGER_OPTIONS* pCurrentOptions);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pCurrentOptions`  
 vorgenommen Die aktuellen Optionen.  
  
## <a name="see-also"></a>Siehe auch  
 [Iremotedebuapplication-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)    
 [IRemoteDebugApplication110-Schnittstelle](../../winscript/reference/iremotedebugapplication110-interface.md)