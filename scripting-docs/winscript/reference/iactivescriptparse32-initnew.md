---
title: IActiveScriptParse32::InitNew | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 31de8258ae13855741c6dd5ca9e4ff2c589e97bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Initialisiert das Skriptmodul.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` im Erfolgsfall oder `E_FAIL` bei einem während der Initialisierung Fehler.  
  
## <a name="remarks"></a>Hinweise  
 Bevor das Skriptmodul verwendet werden kann, eine der folgenden Methoden muss aufgerufen werden: `IPersist*::Load`, `IPersist*::InitNew`, oder `IActiveScriptParse32::InitNew`. Die Semantik dieser Methode ist identisch mit `IPersistStreamInit::InitNew`in dieser weist diese des Skriptmoduls in sich selbst zu initialisieren. Beachten Sie, dass es nicht zulässig, beide rufen `IPersist*::InitNew` oder `IActiveScriptParse32::InitNew` und `IPersist*::Load`, noch ist es zulässig, rufen Sie `IPersist*::InitNew`, `IActiveScriptParse32::InitNew`, oder `IPersist*::Load` mehr als einmal.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)