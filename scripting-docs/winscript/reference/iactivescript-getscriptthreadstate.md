---
title: 'IActiveScript:: getscriptthreadstate | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 38f6ef4b0acdf6e3b746316bef8abe9a3f0f8225
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578008"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Ruft den aktuellen Zustand eines Skript Threads ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `stidThread`  
 in Der Bezeichner des Threads, für den der Status gewünscht ist, oder einer der folgenden speziellen Thread Bezeichner:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Der Basis Thread. Das heißt, der Thread, in dem die Skript-Engine instanziiert wurde.|  
|SCRIPTTHREADID_CURRENT|Der derzeit ausgeführte Thread.|  
  
 `pstsState`  
 vorgenommen Adresse einer Variablen, die den Zustand des bestimmten Threads empfängt. Der Status wird durch einen der benannten Konstanten Werte angegeben, der durch die [scriptthreadstate-Enumeration](../../winscript/reference/scriptthreadstate-enumeration.md) festgelegt wird. Wenn dieser Parameter den aktuellen Thread nicht identifiziert, kann sich der Status jederzeit ändern.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der-Befehl wurde nicht erwartet (z. b. wurde die Skript-Engine noch nicht geladen oder initialisiert).|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode kann von nicht basisthreads aus aufgerufen werden, ohne dass ein Aufruf von Objekten oder die [iactivescriptsite](../../winscript/reference/iactivescriptsite.md) -Schnittstelle durchgeführt werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)