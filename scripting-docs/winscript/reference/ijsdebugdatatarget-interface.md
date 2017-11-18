---
title: IJsDebugDataTarget-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94e158ced0da6d59bfcadeb87bf206c94a6099ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatarget-interface"></a>IJsDebugDataTarget-Schnittstelle
Implementiert durch den Debugger zur Bereitstellung von Funktionen, um auf den Zustand des Zieldebuggerprozesses zuzugreifen und diesen zu ändern.  
  
## <a name="syntax"></a>Syntax  
  
```  
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Mitglieder  
  
### <a name="public-methods"></a>Öffentliche Methoden  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[IJsDebugDataTarget::AllocateVirtualMemory-Methode](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Reserviert und/oder führt Commit eines Arbeitsspeicherbereich innerhalb des virtuellen Adressraums des Zielprozesses aus.|  
|[IJsDebugDataTarget::CreateStackFrameEnumerator-Methode](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Erstellt einen Enumerator für Stapelrahmen.|  
|[IJsDebugDataTarget::FreeVirtualMemory-Methode](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Führt Freigabe und/oder Aufhebung der Zusage eines Arbeitsspeicherbereich innerhalb des virtuellen Adressraums des Zielprozesses aus.|  
|[IJsDebugDataTarget::GetThreadContext-Methode](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Ruft den Kontext zum angegebenen Thread ab.|  
|[IJsDebugDataTarget::GetTlsValue-Methode](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Für den Thread, der debuggt wird, wird der Wert im Slot des threadlokalen Speichers (TLS) für den angegebenen TLS-Index abgerufen.|  
|[IJsDebugDataTarget::ReadBSTR-Methode](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Liest ein BSTR vom Debugziel.|  
|[IJsDebugDataTarget::ReadMemory-Methode](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Liest den Arbeitsspeicher des Zielprozesses.|  
|[IJsDebugDataTarget::ReadNullTerminatedString-Methode](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Liest die angegebene Anzahl von Zeichen aus dem Ziel.|  
|[IJsDebugDataTarget::WriteMemory-Methode](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Liest den Arbeitsspeicher des Zielprozesses.|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Script-Schnittstellenreferenz](../../winscript/reference/windows-script-interfaces-reference.md)