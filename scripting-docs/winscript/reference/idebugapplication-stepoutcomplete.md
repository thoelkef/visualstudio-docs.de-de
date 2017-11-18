---
title: IDebugApplication::StepOutComplete | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.StepOutComplete
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::StepOutComplete
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c344f0316bda6ed5ef895c1b88ae7b1a6465e73
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
Benachrichtigt, dass ein Sprachmodul im einschrittigen Modus umgehend an den Aufrufer zurückgeben dem Debug-Prozess-Manager.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Sprache-Module aufrufen im einschrittigen Modus diese Methode, unmittelbar bevor sie sich an ihren Aufrufer zurückgeben. Der Prozess-Manager verwendet diese Möglichkeit, um Script-Module zu informieren, die bei der ersten Gelegenheit umgebrochen werden soll. Diese Technik ist wie sprachübergreifende Schritt Modi implementiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)