---
title: Implementieren und Registrieren eines Portanbieters | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 189f524ff96c8ad353425820e9f3931364951774
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990268"
---
# <a name="implement-and-register-a-port-supplier"></a>Implementieren und Registrieren eines portanbieters
Die Rolle eines portanbieters wird zum Nachverfolgen und Bereitstellen von Ports, die wiederum Prozesse zu verwalten. Wenn ein Port werden erstellt muss, wird Anschlusslieferanten instanziiert die anschlusslieferant GUID (die sitzungsbasierter Debug-Manager [SDM] verwenden, den vom Benutzer ausgewählten oder Anschlusslieferanten vom Projektsystem angegeben Anschlusslieferanten) CoCreate mit. Klicken Sie dann aufruft, das SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) um festzustellen, ob alle Ports hinzugefügt werden können. Wenn ein Port hinzugefügt werden kann, ein neuer Port von Aufrufen angefordert wird [Port hinzufügen](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) und an Sie übergeben eine [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) , die den Port beschreibt. `AddPort` Gibt einen neuen Port, dargestellt durch ein [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) Schnittstelle.  
  
## <a name="discussion"></a>Diskussion  
 Ein Port wird von eines portanbieters erstellt, die einen Computer oder Debug-Server zugeordnet ist. Ein Server listet seine Zulieferer Port, über die[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) -Methode, und eines portanbieters Listet ihre Ports über die [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) Methode.  
  
 Zusätzlich zu den typischen COM-Registrierung muss ein portanbieters selbst mit Visual Studio registrieren, indem die CLSID und den Namen in bestimmten Registrierungsspeicherort platzieren. Eine Debugging-SDK-Hilfsfunktion aufgerufen `SetMetric` übernimmt diese Aufgabe: Es wird einmal für jedes Element, daher registriert werden aufgerufen:  
  
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
  
 Ein portanbieters hebt die Registrierung auf sich selbst durch den Aufruf `RemoveMetric` (ein anderes Debugging-SDK-Hilfsfunktion) einmal für jedes Element, das daher registriert wurde:  
  
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
>  Die [SDK-Hilfsprogramme für das debugging](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` und `RemoveMetric` werden statische Funktionen, die in definierten *dbgmetric.h* und in kompilierten *ad2de.lib*. Die `metrictypePortSupplier`, `metricCLSID`, und `metricName` Hilfsprogramme sind auch im definiert *dbgmetric.h*.  
  
 Ein portanbieters kann angeben, dessen Name und GUID mithilfe der Methoden [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) und [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)bzw.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren eines portanbieters](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [SDK-Hilfsprogramme für das Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Portanbieter](../../extensibility/debugger/port-suppliers.md)