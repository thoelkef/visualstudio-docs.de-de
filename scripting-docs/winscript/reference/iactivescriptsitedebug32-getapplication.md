---
title: IActiveScriptSiteDebug32::GetApplication | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: c71e33445db7745f71e374c586d079a9665776b2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087899"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
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
 [IActiveScriptSiteDebug32-Schnittstelle](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)