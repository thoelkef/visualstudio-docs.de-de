---
title: IActiveScriptParse32::InitNew | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 685c596caa61a5cbd5042fad3a1bfb39c349c1b1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094691"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Initialisiert die Skript-Engine.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` im Erfolgsfall oder `E_FAIL` bei einem während der Initialisierung Fehler.  
  
## <a name="remarks"></a>Hinweise  
 Bevor die Skript-Engine verwendet werden kann, eine der folgenden Methoden muss aufgerufen werden: `IPersist*::Load`, `IPersist*::InitNew`, oder `IActiveScriptParse32::InitNew`. Die Semantik dieser Methode ist identisch mit `IPersistStreamInit::InitNew`, darin, dass diese Methode die Skript-Engine beim selbstinitialisieren teilt. Beachten Sie, dass es nicht zulässig, beide rufen `IPersist*::InitNew` oder `IActiveScriptParse32::InitNew` und `IPersist*::Load`, noch ist es zulässig, rufen Sie `IPersist*::InitNew`, `IActiveScriptParse32::InitNew`, oder `IPersist*::Load` mehr als einmal.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)