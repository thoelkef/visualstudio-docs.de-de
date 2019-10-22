---
title: 'Iactivescriptstats:: getstat | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStat
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStat
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 096f1cf5b9bf8b5533bd5c36d33f014c747ff9aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574335"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Gibt eine der Standardskript Statistiken zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `stid`  
 in Gibt an, welche Statistik zurückgegeben werden soll. Muss der Wert sein:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Gibt die Anzahl der Anweisungen zurück, die seit dem Start des Skripts oder der zurück setzung der Statistiken ausgeführt wurden.|  
  
 `pluHi`  
 vorgenommen Die hohen 32 Bits einer 64-Bit-Ganzzahl ohne Vorzeichen, die die Statistik darstellt.  
  
 `pluLo`  
 vorgenommen Die unteren 32 Bits einer 64-Bit-Ganzzahl ohne Vorzeichen, die die Statistik darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliche Werte sind, sind jedoch nicht auf die Werte in der folgenden Tabelle beschränkt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt eine der Standardskript Statistiken zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Iactivescriptstats:: getstatex](../../winscript/reference/iactivescriptstats-getstatex.md)    
 [IActiveScriptStats-Schnittstelle](../../winscript/reference/iactivescriptstats-interface.md)