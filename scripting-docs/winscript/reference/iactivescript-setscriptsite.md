---
title: IActiveScript::SetScriptSite | Microsoft-Dokumentation
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
ms.openlocfilehash: 3fdf5f3ae84d1a991d67170b5f2b02114b91ee05
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157067"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Informiert die Skript-Engine, der die [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) Schnittstelle-Website, die vom Host bereitgestellt wird. Rufen Sie diese Methode vor allen anderen [IActiveScript](../../winscript/reference/iactivescript.md) Schnittstellenmethoden verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pScriptSite`  
 [in] Die Adresse der skriptwebsite-Host bereitgestellte mit dieser Instanz des verwendeten Skriptmoduls zugeordnet werden soll. Dieses Skript-Engine-Instanz muss eindeutig der Standort zugewiesen werden; Es kann nicht auf die Skript-Engines freigegeben werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_FAIL`|Ein Unbekannter Fehler aufgetreten. die Skript-Engine konnte nicht abgeschlossen wird, initialisieren den Standort.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. eine Site wurde bereits festgelegt).|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)