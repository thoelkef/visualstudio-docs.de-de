---
title: 'Iactivescriptparamese:: InitNew | Microsoft-Dokumentation'
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
ms.openlocfilehash: b4817e103d7408124f35eb7dbaa16e955dd18f17
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573508"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Initialisiert die Skript-Engine.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` zurück, wenn erfolgreich, oder `E_FAIL`, wenn während der Initialisierung ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
 Bevor die Skript-Engine verwendet werden kann, muss eine der folgenden Methoden aufgerufen werden: `IPersist*::Load`, `IPersist*::InitNew` oder `IActiveScriptParse::InitNew`. Die Semantik dieser Methode ist identisch mit `IPersistStreamInit::InitNew`, da diese Methode die Skript-Engine anweist, sich selbst zu initialisieren. Beachten Sie, dass es nicht zulässig ist, sowohl `IPersist*::InitNew` als auch `IActiveScriptParse::InitNew` und `IPersist*::Load` aufzurufen, und es ist auch nicht zulässig, `IPersist*::InitNew`, `IActiveScriptParse::InitNew` oder `IPersist*::Load` mehrmals aufzurufen.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)