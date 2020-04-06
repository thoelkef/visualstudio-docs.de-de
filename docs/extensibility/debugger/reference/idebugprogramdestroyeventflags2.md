---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d869304dd8b6dc82db78cc09ed9d51a54acdc3c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722503"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Ermöglicht einem Debugmodul, das Standardverhalten [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] der Benutzeroberfläche zu überschreiben, wenn Sie eine Debugsitzung beenden.

## <a name="syntax"></a>Syntax

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Debug-Engines implementiert. Es ist nützlich für Hosts, die mehrere Programme während der Lebensdauer eines Prozesses erstellen und zerstören können.

## <a name="methods"></a>Methoden
 Die folgende Tabelle zeigt `IDebugProgramDestroyEventFlags2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Ruft das Programm zum Zerstören von Flags ab.|

## <a name="remarks"></a>Bemerkungen
 Das Standardverhalten [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] der Benutzeroberfläche besteht darin, in den Entwurfsmodus zurückzukehren, nachdem alle Programme ein Programm-Zerstörungsereignis gesendet haben. Diese Schnittstelle ermöglicht es einem Debugmodul, dieses Verhalten zu ändern.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
