---
title: IRemoteDebugApplication::ResumeFromBreakPoint | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ResumeFromBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ResumeFromBreakPoint
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0603ef19426e27324daa39bf769e2c0667477be3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089075"
---
# <a name="iremotedebugapplicationresumefrombreakpoint"></a>IRemoteDebugApplication::ResumeFromBreakPoint
Wird eine Anwendung, die derzeit an einem Haltepunkt wird fortgesetzt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `prptFocus`  
 [in] Für die schrittweise Ausführung Modi, dem Thread handelt es sich im schrittweisen Modus betroffen sind.  
  
 `bra`  
 [in] Die auszuführende Aktion, durch das Fortsetzen der Anwendungs.  
  
 `era`  
 [in] Die Aktion, die in die Groß-/Kleinschreibung zu nutzen, die die Anwendung aufgrund eines Fehlers beendet.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird eine Anwendung, die derzeit an einem Haltepunkt wird fortgesetzt.  
  
## <a name="see-also"></a>Siehe auch  
 [IRemoteDebugApplication-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)   
 [BREAKRESUMEACTION-Enumeration](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION-Enumeration](../../winscript/reference/errorresumeaction-enumeration.md)