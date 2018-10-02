---
title: Implementieren und Registrieren eines Portanbieters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fe8e5cac0b1737d7c3dbd7e9301e0ca25d778db4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522148"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Implementieren und Registrieren eines Portanbieters
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [implementieren und Registrieren eines Portanbieters](https://docs.microsoft.com/visualstudio/extensibility/debugger/implementing-and-registering-a-port-supplier).  
  
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
>  Die [SDK-Hilfsprogramme zum Debugging](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` und `RemoveMetric` statische Funktionen in dbgmetric.h definiert und in ad2de.lib kompiliert werden. Die `metrictypePortSupplier`, `metricCLSID`, und `metricName` Hilfsprogramme sind auch in dbgmetric.h definiert.  
  
 Ein portanbieters kann angeben, dessen Name und GUID mithilfe der Methoden [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) und [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)bzw.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren eines Portanbieters](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [SDK-Hilfsprogramme für das Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Portanbieter](../../extensibility/debugger/port-suppliers.md)

