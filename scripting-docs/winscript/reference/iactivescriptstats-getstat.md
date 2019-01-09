---
title: IActiveScriptStats::GetStat | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0d00c438f0fe03566dfb7efb93645cad02dc7477
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095393"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Gibt einen von der standard-Skripterstellung für Statistiken.  
  
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
 [in] Gibt an, welche Statistik zurückgeben. Der Wert muss sein:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Zurückgeben der Anzahl der Anweisungen, die ausgeführt werden, da das Skript gestartet oder die Statistik zurückgesetzt wurden.|  
  
 `pluHi`  
 [out] Die oberen 32 Bits einer 64-Bit-Ganzzahl ohne Vorzeichen, die die Statistik darstellt.  
  
 `pluLo`  
 [out] Die unteren 32 Bits einer 64-Bit-Ganzzahl ohne Vorzeichen, die die Statistik darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliche Werte enthalten, aber Sie sind nicht auf die Werte in der folgenden Tabelle beschränkt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt einen von der standard-Skripterstellung für Statistiken.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [IActiveScriptStats-Schnittstelle](../../winscript/reference/iactivescriptstats-interface.md)