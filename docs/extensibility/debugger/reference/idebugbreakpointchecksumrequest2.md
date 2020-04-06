---
title: IDebugBreakpointChecksumRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 632c3611f6c03a47a7d46e985eb6aa2685864a7f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735128"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Stellt eine Dokumentprüfsumme für eine Haltepunktanforderung dar.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointChecksumRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Vom [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugpaket implementiert und von Debug-Modulen verbraucht.

## <a name="methods"></a>Methoden
 Die folgende Tabelle zeigt `IDebugBreakpointChecksumRequest2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Ruft die Dokumentprüfsumme für eine Haltepunktanforderung ab, wenn der eindeutige Bezeichner des zu verwendenden Prüfsummenalgorithmus angegeben wird.|
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Bestimmt, ob die Prüfsumme für dieses Dokument aktiviert ist.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
