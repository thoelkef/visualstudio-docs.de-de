---
title: 'Iprocessdebugmanager:: getdefaultappliation | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.GetDefaultApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::GetDefaultApplication
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3532177c32e0d7eb0b7a67a445845cee753d316
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576799"
---
# <a name="iprocessdebugmanagergetdefaultapplication"></a>IProcessDebugManager::GetDefaultApplication
Gibt ein Standard Anwendungs Objekt für den aktuellen Prozess zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetDefaultApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppda`  
 vorgenommen Das debuganwendungsobjekt für diese Anwendung.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode erstellt ein neues debuganwendungsobjekt und fügt es der Liste der laufenden Anwendungen hinzu, falls erforderlich.  
  
 Sprachmodule sollten die Anwendung verwenden, die von der `GetDefaultApplication`-Methode angegeben wird, wenn Sie auf einem Host ausgeführt werden, der keine Anwendung bereitstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [IProcessDebugManager-Schnittstelle](../../winscript/reference/iprocessdebugmanager-interface.md)