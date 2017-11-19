---
title: IProcessDebugManager::GetDefaultApplication | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IProcessDebugManager.GetDefaultApplication
apilocation: pdm.dll
helpviewer_keywords: IProcessDebugManager::GetDefaultApplication
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27fc46e8a5e07c4eb25c5e246db138a27e5511ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iprocessdebugmanagergetdefaultapplication"></a>IProcessDebugManager::GetDefaultApplication
Gibt ein Standardobjekt für die Anwendung für den aktuellen Prozess zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetDefaultApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppda`  
 [out] Das Debug-Application-Objekt für diese Anwendung.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode erstellt ein neues Objekt der Debug-Anwendung und fügt es mit der Ausführung Anwendungsliste, falls erforderlich.  
  
 Sprache-Module sollte die angegebene Anwendung verwenden die `GetDefaultApplication` Methode, wenn sie auf einem Host ausgeführt werden, die eine Anwendung nicht bereitstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [IProcessDebugManager-Schnittstelle](../../winscript/reference/iprocessdebugmanager-interface.md)