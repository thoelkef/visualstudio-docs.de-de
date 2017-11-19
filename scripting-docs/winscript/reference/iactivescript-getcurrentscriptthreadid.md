---
title: IActiveScript::GetCurrentScriptThreadID | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetCurrentScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5921dc4d0f9a9bf0d505fece0f47354cb16d440c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Ruft einen Bezeichner scripting-Engine-definiert, für den gerade ausgeführten Thread ab. Der Bezeichner kann z. B. bei nachfolgenden Funktionsaufrufen Skript Thread ausführungssteuerung Methoden verwendet werden die [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstidThread`  
 [out] Die Adresse einer Variablen, die den aktuellen Thread zugeordneten Skript Threadbezeichner empfängt. Die Interpretation dieser Bezeichner obliegt dem Skriptmodul, aber es kann nur eine Kopie des Windows-Thread-ID sein. Wenn der Win32-Thread beendet wird, wird dieser Bezeichner wird nicht zugewiesen und kann anschließend an einen anderen Thread zugewiesen werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` im Erfolgsfall oder `E_POINTER` , wenn ein ungültiger Zeiger angegeben wurde.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode kann von nicht zur Basis Threads aufgerufen werden, ohne dass eine Legende nicht zur Basis Hostobjekte oder in der [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)