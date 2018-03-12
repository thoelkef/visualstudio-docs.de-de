---
title: IActiveScriptStats::GetStatEx | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptStats.GetStatEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cb8adf27811f3046de7b447e537443ef129a8c3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
Gibt eine benutzerdefiniertes Skript Statistik zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `guid`  
 [in] Gibt an, welche Statistik zurückgegeben. Die Semantik davon welche Statistik zu einem bestimmten bekommen-GUID ist vollständig Modul definiert.  
  
 `pluHi`  
 [out] Die oberen 32 Bits einer 64-Bit-Ganzzahl ohne Vorzeichen, die die Statistik darstellt.  
  
 `pluLo`  
 [out] Die unteren 32 Bits einer 64-Bit-Ganzzahl ohne Vorzeichen, die die Statistik darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Die Methode ist nicht implementiert.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ermöglicht ein benutzerdefiniertes Skript-Modul statistische Daten zu einem benutzerdefinierten Host sinnvolle zurückzugeben.  
  
> [!NOTE]
>  Diese Methode wird derzeit nicht implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [IActiveScriptStats-Schnittstelle](../../winscript/reference/iactivescriptstats-interface.md)