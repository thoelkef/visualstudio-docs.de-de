---
title: Implementieren und Registrieren eines Port Anbieters | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841218"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Implementieren und Registrieren eines Portanbieters
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Rolle eines Port Lieferanten besteht im nachverfolgen und Bereitstellen von Ports, die wiederum Prozesse verwalten. Zu dem Zeitpunkt, zu dem ein Port erstellt werden muss, wird der Port Lieferant mit CoCreate mit der GUID des Port Anbieters instanziiert (der Sitzungs-Debug-Manager [SDM] verwendet den vom Benutzer ausgewählten Port Lieferanten oder den vom Projekt System angegebenen Port Lieferanten). Der SDM ruft dann [canaddport](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) auf, um zu überprüfen, ob Ports hinzugefügt werden können. Wenn ein Port hinzugefügt werden kann, wird ein neuer Port angefordert, indem [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) aufgerufen und ein [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) übergeben wird, der den Port beschreibt. `AddPort` Gibt einen neuen Port zurück, der durch eine [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) -Schnittstelle dargestellt wird.  
  
## <a name="discussion"></a>Diskussion (Discussion)  
 Ein Port wird von einem Port Lieferanten erstellt, der wiederum einem Computer oder einem debugserver zugeordnet ist. Ein Server kann seine Port Lieferanten über die[enumportsuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) -Methode auflisten, und ein Port Lieferant kann seine Ports über die [enumports](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) -Methode auflisten.  
  
 Neben der typischen com-Registrierung muss sich ein Port Lieferant bei Visual Studio registrieren, indem er seine CLSID und den Namen an bestimmten Registrierungsstellen platziert. Eine debugginghilfsfunktion `SetMetric` , die aufgerufen wird, behandelt dieses Chore: Sie wird für jedes zu registrierende Element einmal aufgerufen, sodass Folgendes gilt:  
  
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
  
 Ein Port Lieferant hebt die Registrierung selbst `RemoveMetric` auf, indem er für jedes registrierte Element einmal aufruft (eine andere debugginghilfsfunktion):  
  
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
> Die [SDK-Hilfsprogramme für das Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` und `RemoveMetric` sind statische Funktionen, die in "dbgmetric. h" definiert und in ad2de. lib kompiliert werden. Die Hilfsprogramme `metrictypePortSupplier` , `metricCLSID` und `metricName` werden auch in dbgmetric. h definiert.  
  
 Ein Port Lieferant kann seinen Namen und die GUID über die Methoden " [getportsuppliername](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) " und " [getportsupplierid](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)" angeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren eines Port Anbieters](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [SDK-Hilfsprogramme zum Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Portanbieter](../../extensibility/debugger/port-suppliers.md)
