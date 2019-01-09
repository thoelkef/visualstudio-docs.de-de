---
title: IActiveScriptSiteDebug::GetApplication | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a485a7195f64754bc28d0c1905d30d6f22747c31
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090115"
---
# <a name="iactivescriptsitedebuggetapplication"></a>IActiveScriptSiteDebug::GetApplication
Gibt zurück, das Debug-Application-Objekt mit diesem Skript Standort verbunden ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppda`  
 [out] Zeiger auf das Debug-Anwendungsobjekt der skriptwebsite zugeordnet.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Der Host unterstützt nicht direkt debuggen.|  
  
## <a name="remarks"></a>Hinweise  
 Die `GetApplication` -Methode bietet eine Möglichkeit für einen Smarthost auf das Anwendungsobjekt zu definieren, zu der jedes Skript gehört. Skript-Engines sollten versuchen, rufen diese Methode, um ihre Anwendung zu erhalten und auf die zurückgegriffen `IProcessDebugManager::GetDefaultApplication` schlägt dies fehl.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSiteDebug-Schnittstelle](../../winscript/reference/iactivescriptsitedebug-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)