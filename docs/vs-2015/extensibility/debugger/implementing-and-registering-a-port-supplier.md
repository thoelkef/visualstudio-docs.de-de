---
title: Implementieren und Registrieren eines Portanbieters | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 377aa88df71fd0d3c42745fe2d3ce3b648191aa4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430259"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Implementieren und Registrieren eines Portanbieters
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Rolle eines portanbieters wird zum Nachverfolgen und Bereitstellen von Ports, die wiederum Prozesse zu verwalten. Zum Zeitpunkt ein Ports erstellt werden muss, ist die Anschlusslieferanten mit CoCreate mit den Anschlusslieferanten-GUID (sitzungsbasierter Debug-Manager [SDM] Anschlusslieferanten vom Benutzer ausgewählten oder Anschlusslieferanten angegeben, die vom Projektsystem verwenden) instanziiert. Ruft dann die SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) um festzustellen, ob alle Ports hinzugefügt werden können. Wenn ein Port hinzugefügt werden kann, ein neuer Port von Aufrufen angefordert wird [Port hinzufügen](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) und an Sie übergeben eine [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) , die den Port beschreibt. `AddPort` Gibt einen neuen Port, dargestellt durch ein [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) Schnittstelle.  
  
## <a name="discussion"></a>Diskussion  
 Ein Port wird vom eines portanbieters erstellt, das wiederum einen Computer oder Debug-Server zugeordnet ist. Ein Server kann die Portanbieter durch Aufzählen der[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) -Methode, und eines portanbieters können die Ports durch Aufzählen der [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) Methode.  
  
 Zusätzlich zu den typischen COM-Registrierung muss ein portanbieters selbst mit Visual Studio registrieren, indem die CLSID und den Namen in bestimmten Registrierungsspeicherort platzieren. Eine Debugging-SDK-Hilfsfunktion aufgerufen `SetMetric` übernimmt diese Aufgabe: Es wird einmal für jedes Element, daher registriert werden aufgerufen:  
  
```cpp#  
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
  
```cpp#  
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
> Die [SDK-Hilfsprogramme zum Debugging](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` und `RemoveMetric` statische Funktionen in dbgmetric.h definiert und in ad2de.lib kompiliert werden. Die `metrictypePortSupplier`, `metricCLSID`, und `metricName` Hilfsprogramme sind auch in dbgmetric.h definiert.  
  
 Ein portanbieters kann angeben, dessen Name und GUID mithilfe der Methoden [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) und [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)bzw.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren eines Portanbieters](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [SDK-Hilfsprogramme für das Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Portanbieter](../../extensibility/debugger/port-suppliers.md)
