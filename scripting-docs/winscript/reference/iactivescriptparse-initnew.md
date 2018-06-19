---
title: IActiveScriptParse::InitNew | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: e34094bcc25c0316fa670f570d8b2664acc0ba78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724480"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Initialisiert das Skriptmodul.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` im Erfolgsfall oder `E_FAIL` bei einem während der Initialisierung Fehler.  
  
## <a name="remarks"></a>Hinweise  
 Bevor das Skriptmodul verwendet werden kann, eine der folgenden Methoden muss aufgerufen werden: `IPersist*::Load`, `IPersist*::InitNew`, oder `IActiveScriptParse::InitNew`. Die Semantik dieser Methode ist identisch mit `IPersistStreamInit::InitNew`in dieser weist diese des Skriptmoduls in sich selbst zu initialisieren. Beachten Sie, dass es nicht zulässig, beide rufen `IPersist*::InitNew` oder `IActiveScriptParse::InitNew` und `IPersist*::Load`, noch ist es zulässig, rufen Sie `IPersist*::InitNew`, `IActiveScriptParse::InitNew`, oder `IPersist*::Load` mehr als einmal.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)