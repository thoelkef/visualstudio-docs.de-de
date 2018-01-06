---
title: Implementieren und registrieren einen Port Lieferanten | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1c05dc0bd15dc5c1959024327396d848cd0b1112
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-and-registering-a-port-supplier"></a>Implementieren und registrieren einen Port Lieferanten
Die Rolle eines Lieferanten Port ist zu verfolgen, und geben Sie die Ports, die wiederum Prozesse zu verwalten. Zum Zeitpunkt der erstellt werden muss, ist der Lieferant Port mit CoCreate mit den Port Lieferanten-GUID (die Sitzung Debug-Manager [SDM] Port Lieferanten, die ausgewählten Benutzer oder die Port-Lieferanten, die vom Projektsystem angegeben verwenden) instanziiert. Ruft die SDM dann [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) um festzustellen, ob es sich bei allen Ports hinzugefügt werden können. Wenn Sie ein Port hinzugefügt werden kann, ein neuer Port von Aufrufen angefordert wird [hinzufügen](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) und zur Übergabe an ein [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) , den Port beschreibt. `AddPort`Gibt einen neuen Port dargestellte zurück ein [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) Schnittstelle.  
  
## <a name="discussion"></a>Diskussion  
 Ein Port wird ein Lieferant Port erstellt, die wiederum von einem Computer oder Debug-Server zugeordnet ist. Ein Server kann seine Lieferanten Port, über Auflisten der[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) -Methode, und ein Lieferant Port können die Ports durch Auflisten der [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) Methode.  
  
 Zusätzlich zu den normalen COM-Registrierung muss ein Port Lieferanten selbst mit Visual Studio registrieren, indem deren Namen und CLSID in bestimmten Registrierungsspeicherorte platzieren. Eine Debugging-SDK-Hilfsfunktion aufgerufen `SetMetric` übernimmt diese Aufgabe: einmal für jedes Element, daher zu registrierende aufgerufen wird:  
  
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
  
 Ein Lieferant Port hebt die Registrierung selbst durch Aufrufen von `RemoveMetric` (eine andere Debugging-SDK-Hilfsfunktion) einmal für jedes Element, das daher registriert wurde:  
  
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
>  Die [SDK-Hilfsprogramme zum Debugging](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` und `RemoveMetric` statische Funktionen in dbgmetric.h definiert und in ad2de.lib kompiliert werden. Die `metrictypePortSupplier`, `metricCLSID`, und `metricName` Hilfsprogramme auch in dbgmetric.h definiert sind.  
  
 Ein Lieferant Port kann Geben Sie seinen Namen und GUID mithilfe der Methoden [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) und [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)zugeordnet.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren einen Port Lieferanten](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [SDK-Hilfsprogramme für das Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Portanbieter](../../extensibility/debugger/port-suppliers.md)