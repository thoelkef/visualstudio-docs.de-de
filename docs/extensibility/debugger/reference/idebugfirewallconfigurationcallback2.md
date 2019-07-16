---
title: IDebugFirewallConfigurationCallback2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09b4c04b996d180f1975ee1e9ad3a9a95cd1b76a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337448"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Ermöglicht es eine Debug-Engine, die DCOM verwendet wird, stellen die [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche, um sicherzustellen, dass die Firewall das Remotedebugging nicht blockiert wird.

## <a name="syntax"></a>Syntax

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Durch die Port-Objekt, von der Sitzungs-Manager implementiert.

## <a name="methods"></a>Methoden
 Die folgende Tabelle zeigt die Methoden der `IDebugFirewallConfigurationCallback2`.

|Methode|Beschreibung|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Fordert an, dass der Firewall kein Remotedebugging blockiert.|

## <a name="requirements"></a>Anforderungen
 Header: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll