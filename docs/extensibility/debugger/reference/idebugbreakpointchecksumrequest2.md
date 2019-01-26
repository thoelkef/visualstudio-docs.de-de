---
title: IDebugBreakpointChecksumRequest2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ff19ac7cfc05e198e49dccdc0a24f198cd1be02
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013248"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Stellt eine Dokument-Prüfsumme für eine Haltepunkt-Anforderung dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Implementiert durch die [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debug-Paket, und von Debug-Engines verwendet.  
  
## <a name="methods"></a>Methoden  
 Die folgende Tabelle zeigt die Methoden der `IDebugBreakpointChecksumRequest2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Ruft die Dokument-Prüfsumme für eine Haltepunkt-Anforderung den eindeutigen Bezeichner des Prüfsummenalgorithmus ab.|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Bestimmt, ob die Prüfsumme für dieses Dokument aktiviert ist.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll