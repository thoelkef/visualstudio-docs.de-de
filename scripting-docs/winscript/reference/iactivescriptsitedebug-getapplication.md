---
title: 'Iactivescriptsitedebug:: getapplikation | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetApplication
ms.assetid: 4400f1b1-3108-4a71-b1f1-43586fe1227c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2ad81e3b6b1707f5a23271cf0abe3832266c07f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570124"
---
# <a name="iactivescriptsitedebuggetapplication"></a>IActiveScriptSiteDebug::GetApplication
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
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Der Host unterstützt das Debugging nicht direkt.|  
  
## <a name="remarks"></a>Hinweise  
 Die `GetApplication`-Methode bietet einem Smarthost die Möglichkeit, das Anwendungs Objekt zu definieren, zu dem die einzelnen Skripts gehören. Skript-Engines sollten versuchen, diese Methode aufzurufen, um Ihre enthaltende Anwendung abzurufen und auf `IProcessDebugManager::GetDefaultApplication` zurückzugreifen, wenn dies fehlschlägt.  
  
## <a name="see-also"></a>Siehe auch  
 [Iactivescriptsitedebug-Schnittstelle](../../winscript/reference/iactivescriptsitedebug-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)