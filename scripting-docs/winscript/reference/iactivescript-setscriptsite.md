---
title: 'IActiveScript:: setscriptsite | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptSite
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 063dcc7b580334bff9780e9c209b621ef7e25656
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575328"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Informiert die Skript-Engine über die [iactivescriptsite](../../winscript/reference/iactivescriptsite.md) Interface-Website, die vom Host bereitgestellt wird. Diese Methode muss aufgerufen werden, bevor andere [IActiveScript](../../winscript/reference/iactivescript.md) -Schnittstellen Methoden verwendet werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pScriptSite`  
 in Adresse der vom Host bereitgestellten Skript Site, die dieser Instanz der Skript-Engine zugeordnet werden soll. Die Website muss dieser Skript-Engine-Instanz eindeutig zugewiesen werden. Sie kann nicht für andere Skript-Engines freigegeben werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_FAIL`|Ein nicht angegebener Fehler ist aufgetreten. die Skript-Engine konnte die Initialisierung der Site nicht abschließen.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der-Befehl wurde nicht erwartet (z. b. wurde eine Website bereits festgelegt).|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)