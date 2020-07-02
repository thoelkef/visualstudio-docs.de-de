---
title: 'IActiveScriptParse32:: InitNew | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 887e4ce44662cc591fee64f5e0549edcdcbc14af
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835705"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Initialisiert die Skript-Engine.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt zurück `S_OK` , wenn erfolgreich, oder, `E_FAIL` Wenn während der Initialisierung ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
 Bevor die Skript-Engine verwendet werden kann, muss eine der folgenden Methoden aufgerufen werden: `IPersist*::Load` , `IPersist*::InitNew` oder `IActiveScriptParse32::InitNew` . Die Semantik dieser Methode ist identisch mit `IPersistStreamInit::InitNew` , da diese Methode die Skript-Engine anweist, sich selbst zu initialisieren. Beachten Sie, dass es nicht zulässig ist, sowohl die `IPersist*::InitNew` -als auch die-Eigenschaft oder die-Eigenschaft aufzurufen `IActiveScriptParse32::InitNew` `IPersist*::Load` , auch `IPersist*::InitNew` Wenn, oder mehrmals aufgerufen `IActiveScriptParse32::InitNew` `IPersist*::Load` werden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)