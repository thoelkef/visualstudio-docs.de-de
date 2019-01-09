---
title: IActiveScript::GetScriptThreadState | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b191f1b70aa522cba0a04e0781ada69a8fe5ca5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097525"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Ruft den aktuellen Status eines Threads Skript ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `stidThread`  
 [in] Bezeichner des Threads für den der Zustand gewünscht wird, oder eine der folgenden speziellen Thread-IDs:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Die Basis-Thread. instanziiert wurde, also die in dem der Skript-Engine-Threads.|  
|SCRIPTTHREADID_CURRENT|Der aktuell ausgeführten Thread.|  
  
 `pstsState`  
 [out] Die Adresse einer Variablen, die den Zustand der angegebenen Threads empfängt. Der Status wird angegeben, von einem der benannten Konstanten Werte von definiert die [SCRIPTTHREADSTATE-Enumeration](../../winscript/reference/scriptthreadstate-enumeration.md) Enumeration. Wenn dieser Parameter den aktuellen Thread nicht identifiziert, kann der Zustand zu einem beliebigen Zeitpunkt ändern.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. die Skript-Engine wurde noch nicht wurden geladen oder initialisiert).|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode kann von nicht-Base Threads aufgerufen werden, ohne dass eine nicht-Base-Legende Hostobjekte oder in der [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)