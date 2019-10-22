---
title: 'Iactivescriptstats:: resetstats | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.ResetStats
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::ResetStats
ms.assetid: d98276fc-ad47-4e7b-aae4-254d63aece77
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2767bb1e2cce3a11661ebaca37e66d33f95beb2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577965"
---
# <a name="iactivescriptstatsresetstats"></a>IActiveScriptStats::ResetStats
Setzt die Statistik für dieses Skript zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT ResetStats();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter an.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode setzt die Statistik für dieses Skript zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptStats-Schnittstelle](../../winscript/reference/iactivescriptstats-interface.md)