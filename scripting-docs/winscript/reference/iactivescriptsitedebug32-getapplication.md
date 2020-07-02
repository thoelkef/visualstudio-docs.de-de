---
title: 'IActiveScriptSiteDebug32:: getapplikation | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 0b82ab6cd37f789e98ca08c635011a7e04f5b871
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835627"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
Gibt das Debug-Anwendungs Objekt zurück, das dieser Skript Site zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppda`  
 vorgenommen Zeiger auf das debuganwendungsobjekt, das der Skript Website zugeordnet ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode wurde erfolgreich ausgeführt.|  
|`E_NOTIMPL`|Der Host unterstützt das Debugging nicht direkt.|  
  
## <a name="remarks"></a>Hinweise  
 Die- `GetApplication` Methode bietet einem Smarthost die Möglichkeit, das Anwendungs Objekt zu definieren, zu dem die einzelnen Skripts gehören. Skript-Engines sollten versuchen, diese Methode aufzurufen, um Ihre enthaltende Anwendung abzurufen und auf zurückzugreifen, `IProcessDebugManager::GetDefaultApplication` Wenn dies fehlschlägt.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSiteDebug32-Schnittstelle](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)