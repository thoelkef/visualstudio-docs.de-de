---
title: Implementieren und Registrieren eines Hafenlieferanten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efa9cdd8740648b66fe7190177b5fe769c4b2539
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738535"
---
# <a name="implement-and-register-a-port-supplier"></a>Implementieren und Registrieren eines Hafenlieferanten
Die Rolle eines Hafenlieferanten besteht darin, Ports zu verfolgen und zu versorgen, die wiederum Prozesse verwalten. Wenn ein Port erstellt werden muss, wird der Portlieferant mit CoCreate mit der GUID des Portlieferanten instanziiert (der Sitzungsdebug-Manager [SDM] verwendet den Portlieferanten, den der vom Benutzer ausgewählte oder der Vom Projektsystem angegebene Portlieferant ausgewählt hat). Das SDM ruft dann [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) auf, um zu sehen, ob Ports hinzugefügt werden können. Wenn ein Port hinzugefügt werden kann, wird ein neuer Port angefordert, indem [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) aufgerufen und ein [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) übergeben wird, der den Port beschreibt. `AddPort`gibt einen neuen Port zurück, der durch eine [IDebugPort2-Schnittstelle](../../extensibility/debugger/reference/idebugport2.md) dargestellt wird.

## <a name="discussion"></a>Diskussion
 Ein Port wird von einem Portlieferanten erstellt, der einem Computer oder Debugserver zugeordnet ist. Ein Server zählt seine Portlieferanten über die[EnumPortSuppliers-Methode](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) auf, und ein Portlieferant zählt seine Ports über die [EnumPorts-Methode](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) auf.

 Zusätzlich zur typischen COM-Registrierung muss sich ein Portanbieter bei Visual Studio registrieren, indem er seine CLSID und seinen Namen an bestimmten Registrierungsspeicherorten platziert. Eine Debugging-SDK-Hilfsfunktion namens `SetMetric` Handles diese Aufgabe: Sie wird einmal aufgerufen, damit jedes Element registriert werden kann, also:

```cpp
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricCLSID,
          <CLSID of your port supplier>,
          false,
          NULL)
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricName,
          <name of your port supplier>,
          false,
          NULL);
```

 Ein Portlieferant entmeldet sich `RemoveMetric` selbst, indem er (eine andere Debugging SDK-Hilfsfunktion) einmal für jedes registrierte Element aufruft, also:

```cpp
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricCLSID,
             NULL);
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricName,
             NULL);
```

> [!NOTE]
> Die [SDK-Hilfsprogramme zum Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` und `RemoveMetric` sind statische Funktionen, die in *dbgmetric.h* definiert und in *ad2de.lib*kompiliert werden. Die `metrictypePortSupplier` `metricCLSID`, `metricName` und Die Helpers sind auch in *dbgmetric.h*definiert.

 Ein Portlieferant kann seinen Namen und seine GUID über die Methoden [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) bzw. [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)angeben.

## <a name="see-also"></a>Weitere Informationen
- [Implementieren eines Portlieferanten](../../extensibility/debugger/implementing-a-port-supplier.md)
- [SDK-Hilfsprogramme zum Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Hafenlieferanten](../../extensibility/debugger/port-suppliers.md)
