---
title: SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8eb089efbf608b488465809f997ffc82fc2c2e3c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574411"
---
# <a name="script_error_debug_exception_thrown_kind-enumeration"></a>SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND-Enumeration
Gibt die Art der ausgelösten Ausnahme an. Diese Enumeration wird von der [IActiveScriptErrorDebug110:: getexceptionthrownkind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) -Methode verwendet.  
  
> [!IMPORTANT]
> Diese Konstanten werden durch PDM-Version 11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Member  
  
|Member|Wert|Beschreibung|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|Die Ausnahme ist eine Ausnahme der ersten Chance.|  
|ETK_USER_UNHANDLED|0x00000001|Die Ausnahme wird im Benutzercode nicht behandelt.|  
|ETK_UNHANDLED|0x00000002|Die Ausnahme wird im Code nicht behandelt.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptErrorDebug110-Schnittstelle](../../winscript/reference/iactivescripterrordebug110-interface.md)