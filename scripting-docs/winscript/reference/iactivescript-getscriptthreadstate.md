---
title: IActiveScript::GetScriptThreadState | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b11b8566857bc70aaeac5bdf8e8e357fa5d9c2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Ruft den aktuellen Status eines Threads Skript ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `stidThread`  
 [in] Bezeichner des Threads für die der Status gewünscht wird, oder eine der folgenden speziellen Thread-IDs:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Die Basis-Thread. d. h. wurde der Thread, in dem das Skript-engine-instanziiert.|  
|SCRIPTTHREADID_CURRENT|Den gerade ausgeführten Thread.|  
  
 `pstsState`  
 [out] Die Adresse einer Variablen, die den Status des angegebenen Threads empfängt. Der Status wird angezeigt, eines der benannten Konstante Werte, die definiert, indem Sie die [SCRIPTTHREADSTATE-Enumeration](../../winscript/reference/scriptthreadstate-enumeration.md) Enumeration. Wenn dieser Parameter nicht den aktuellen Thread identifiziert, kann der Status jederzeit ändern.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. das Skriptmodul wurde noch kein geladen oder initialisiert).|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode kann von nicht zur Basis Threads aufgerufen werden, ohne dass eine Legende nicht zur Basis Hostobjekte oder in der [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)