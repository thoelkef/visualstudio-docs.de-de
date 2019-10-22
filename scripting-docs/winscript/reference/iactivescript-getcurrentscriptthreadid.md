---
title: 'IActiveScript:: getcurrentscriptthreadid | Microsoft-Dokumentation'
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
ms.openlocfilehash: dedb16e0c007ed05370fb54835f84f00784c1ae4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575769"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Ruft einen von der Skript-Engine definierten Bezeichner für den aktuell ausgeführten Thread ab. Der Bezeichner kann in nachfolgenden Aufrufen von Skript Ausführungs Steuerungsmethoden wie z. b. der [IActiveScript:: interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) -Methode verwendet werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstidThread`  
 vorgenommen Adresse einer Variablen, die den mit dem aktuellen Thread verknüpften Skript Thread Bezeichner empfängt. Die Interpretation dieses Bezeichners wird der Skript-Engine überlassen, aber es kann sich lediglich um eine Kopie der Windows-Thread Kennung handeln. Wenn der Win32-Thread beendet wird, wird dieser Bezeichner nicht zugewiesen und kann anschließend einem anderen Thread zugewiesen werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` zurück, wenn erfolgreich, oder `E_POINTER`, wenn ein ungültiger Zeiger angegeben wurde.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode kann von nicht basisthreads aus aufgerufen werden, ohne dass ein Aufruf von Objekten oder die [iactivescriptsite](../../winscript/reference/iactivescriptsite.md) -Schnittstelle durchgeführt werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)