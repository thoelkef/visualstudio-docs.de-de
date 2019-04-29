---
title: IActiveScript::GetCurrentScriptThreadID | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetCurrentScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e1b6e7bae7d78c18e11cd1aac8d0844fb9e90a5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935655"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Ruft eine scripting-Engine-definierten Bezeichner für den aktuell ausgeführten Thread ab. Der Bezeichner kann z. B. bei nachfolgenden Aufrufen von Skripts Thread ausführungssteuerung Methoden verwendet werden die [IActiveScript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstidThread`  
 [out] Die Adresse einer Variablen, die die dem aktuellen Thread zugeordneten Skript Threadbezeichner empfängt. Die Interpretation dieser Bezeichner ist die Skript-Engine überlassen, aber es kann nur eine Kopie der Windows-Thread-Bezeichner sein. Wenn der Win32-Thread beendet wird, wird dieser Bezeichner wird nicht zugewiesen und kann anschließend an einen anderen Thread zugewiesen werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` im Erfolgsfall oder `E_POINTER` Wenn ein ungültiger Zeiger angegeben wurde.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode kann von nicht-Base Threads aufgerufen werden, ohne dass eine nicht-Base-Legende Hostobjekte oder in der [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)