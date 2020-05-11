---
title: IDebugPortSupplierBeschreibung2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69853e34788a2f24afe183dfbb7070e48f14aa46
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724355"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Ermöglicht [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] der Benutzeroberfläche die Anzeige von Text im Abschnitt **Transportinformationen** im Dialogfeld An fügen an **den Prozess** an.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Hafenlieferanten implementiert.

## <a name="methods"></a>Methoden
 Die folgende Tabelle zeigt `IDebugPortSupplierDescription2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Ruft die Beschreibungs- und Beschreibungsmetadaten für den Portanbieter ab.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
