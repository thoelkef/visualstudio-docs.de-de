---
title: IActiveScriptSiteDebug32::GetApplication | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: bb7fdf5a6d0b380a8024cfdfa70282bcf80ba16d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
Gibt die Debug-Application-Objekt mit diesem Skript-Site verknüpft sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppda`  
 [out] Ein Zeiger auf die Debug-Application-Objekt mit dem Skript-Site verknüpft sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Der Host unterstützt nicht direkt debuggen.|  
  
## <a name="remarks"></a>Hinweise  
 Die `GetApplication` Methode bietet eine Möglichkeit für einen Smarthost des Anwendungsobjekts definieren, der jedes Skript angehört. Script-Module sollten versuchen, rufen Sie diese Methode, um die enthaltende Anwendung abrufen und hierfür auf `IProcessDebugManager::GetDefaultApplication` schlägt der Vorgang fehl.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSiteDebug32-Schnittstelle](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)