---
title: 'IActiveScriptParse:: InitNew | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.InitNew
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_InitNew
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55d38031708694aa777f7598f261afdfc2b4f3b9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148947"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Initialisiert die Skript-Engine.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` im Erfolgsfall oder `E_FAIL` bei einem während der Initialisierung Fehler.  
  
## <a name="remarks"></a>Hinweise  
 Bevor die Skript-Engine verwendet werden kann, eine der folgenden Methoden muss aufgerufen werden: `IPersist*::Load`, `IPersist*::InitNew`, oder `IActiveScriptParse::InitNew`. Die Semantik dieser Methode ist identisch mit `IPersistStreamInit::InitNew`, darin, dass diese Methode die Skript-Engine beim selbstinitialisieren teilt. Beachten Sie, dass es nicht zulässig, beide rufen `IPersist*::InitNew` oder `IActiveScriptParse::InitNew` und `IPersist*::Load`, noch ist es zulässig, rufen Sie `IPersist*::InitNew`, `IActiveScriptParse::InitNew`, oder `IPersist*::Load` mehr als einmal.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)