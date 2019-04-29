---
title: 'Iactivescriptsitedebug:: Getrootapplicationnode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.GetRootNode
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::GetRootNode
ms.assetid: 6c043aba-1dc5-41de-9711-96cde5e040f6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef8337e27bb5a666e8d5d8d38abcafb044da02ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944220"
---
# <a name="iremotedebugapplicationgetrootnode"></a>IRemoteDebugApplication::GetRootNode
Gibt den Knoten der Anwendung unter dem alle Knoten, die der Anwendung zugeordneten hinzugefügt wurden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetRootNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppdanRoot`  
 [out] Der Knoten von Debug-Anwendung unter dem alle Knoten, die der Anwendung zugeordneten hinzugefügt wurden.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt den Knoten der Anwendung unter dem alle Knoten, die der Anwendung zugeordneten hinzugefügt wurden.  
  
## <a name="see-also"></a>Siehe auch  
 [IRemoteDebugApplication-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)