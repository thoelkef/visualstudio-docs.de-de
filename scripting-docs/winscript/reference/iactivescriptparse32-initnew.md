---
title: 'IActiveScriptParse32:: InitNew | Microsoft-Dokumentation'
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
ms.openlocfilehash: 8b5304d60aed8145e7a68d89b2c6d4386db0d745
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561663"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32:: InitNew
Initialisiert die Skript-Engine.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` zurück, wenn erfolgreich, oder `E_FAIL`, wenn während der Initialisierung ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
 Bevor die Skript-Engine verwendet werden kann, muss eine der folgenden Methoden aufgerufen werden: `IPersist*::Load`, `IPersist*::InitNew` oder `IActiveScriptParse32::InitNew`. Die Semantik dieser Methode ist identisch mit `IPersistStreamInit::InitNew`, da diese Methode die Skript-Engine anweist, sich selbst zu initialisieren. Beachten Sie, dass es nicht zulässig ist, sowohl `IPersist*::InitNew` als auch `IActiveScriptParse32::InitNew` und `IPersist*::Load` aufzurufen, und es ist auch nicht zulässig, `IPersist*::InitNew`, `IActiveScriptParse32::InitNew` oder `IPersist*::Load` mehrmals aufzurufen.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)