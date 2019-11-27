---
title: 'Iactivescriptstats:: getstatex | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStatEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ca7cdb81fd7e228b26bfaa12d45e81335674a74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576127"
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
Gibt eine benutzerdefinierte Skript Statistik zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `guid`  
 in Gibt an, welche Statistik zurückgegeben werden soll. Die Semantik der Statistik, die einer bestimmten GUID entspricht, ist vollständig Modul definiert.  
  
 `pluHi`  
 vorgenommen Die hohen 32 Bits einer 64-Bit-Ganzzahl ohne Vorzeichen, die die Statistik darstellt.  
  
 `pluLo`  
 vorgenommen Die unteren 32 Bits einer 64-Bit-Ganzzahl ohne Vorzeichen, die die Statistik darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Die Methode ist nicht implementiert.|  
  
## <a name="remarks"></a>Hinweise  
 Mit dieser Methode kann eine benutzerdefinierte Skript-Engine Statistiken für einen benutzerdefinierten Host zurückgeben.  
  
> [!NOTE]
> Diese Methode ist derzeit nicht implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [IActiveScriptStats-Schnittstelle](../../winscript/reference/iactivescriptstats-interface.md)