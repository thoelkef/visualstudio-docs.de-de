---
title: IActiveScript::SetScriptSite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 11fa9003abb03c42adcbf3a548bb5b90d763a344
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645570"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Informiert das Skriptmodul von der [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) Schnittstelle-Website, die vom Host bereitgestellt. Rufen Sie diese Methode vor allen anderen [IActiveScript](../../winscript/reference/iactivescript.md) Schnittstellenmethoden verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pScriptSite`  
 [in] Die Adresse der Website Host bereitgestellte Skript mit dieser Instanz des verwendeten Skriptmoduls zugeordnet werden soll. Der Standort muss diese scripting-Modulinstanz eindeutig zugewiesen werden; Er kann nicht mit anderen Skriptmodule gemeinsam genutzt werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_FAIL`|Nicht angegebener Fehler aufgetreten. das Skriptmodul konnte nicht abgeschlossen wird, initialisieren den Standort.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. eine Website wurde bereits festgelegt).|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)