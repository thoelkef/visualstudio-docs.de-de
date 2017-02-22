---
title: "Implementieren und registrieren einen Port Lieferanten | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK], Port Lieferanten registrieren"
  - "Port-Lieferanten, registrieren"
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Implementieren und registrieren einen Port Lieferanten
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die Rolle eines Anschlusslieferanten ist nachzuverfolgen und stellt anschlüsse, die wiederum Prozesse verwalten.  Zum Zeitpunkt als Port erstellt werden muss, ist der Port beteiligt ist. lieferant mit dem GUID des Anschlusslieferanten instanziiert, die die Sitzung \(Multithreaded Manager \[SDM\] den Anschlusslieferanten der ausgewählte Benutzer oder den Anschlusslieferanten verwendet, die durch das Projektsystem an\).  Das SDM ruft dann [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) an, um festzustellen, dass Ports ggf. hinzugefügt werden können.  Wenn ein Anschluss hinzugefügt werden kann, wird ein neuer Anschluss angefordert, indem [Port hinzufügen](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) aufruft, und es [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) übergeben wird, das den Port beschreibt.  `AddPort` gibt einen neuen Anschluss zurück, der eine [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)\-Schnittstelle dargestellt wird.  
  
## Erörterung  
 Ein Port wird von einem Anschlusslieferanten erstellt, der wiederum mit einem Computer oder in einem Debugbuild Server zugeordnet ist.  Ein Server kann den Anschlusslieferanten von der[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)\-Methode aufgelistet werden, und ein Anschluss lieferant kann die Ports von der [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)\-Methode aufgelistet.  
  
 Neben der typischen COM\-Registrierung muss ein Anschluss lieferant mit Visual Studio registrieren, indem er der CLSID und Namen in den jeweiligen Registrierungsdaten speicherorten platziert.  Zu debuggendes SDK Hilfsfunktion mit dem Namen `SetMetric` behandelt diese Aufgabe: Er wird einmal aufgerufen, sodass jedes Element registriert werden kann, sodass:  
  
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
  
 Ein Port lieferant hebt die Registrierung indem er einmal `RemoveMetric` \(eine andere debuggende SDK\-Hilfsfunktion\) für jedes Element, das gerade registriert wird, so aufrufen:  
  
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
>  [SDK\-Hilfsprogramme für das Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` und `RemoveMetric` werden die statischen Funktionen, die in dbgmetric.h definiert und in ad2de.lib kompiliert sind.  `metrictypePortSupplier`, `metricCLSID`und hilft`metricName` werden auch in dbgmetric.h definiert.  
  
 Ein Port kann lieferant sein Name und GUID mithilfe der Methoden [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) und [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)angeben.  
  
## Siehe auch  
 [Implementieren einen Port Lieferanten](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [SDK\-Hilfsprogramme für das Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Port\-Lieferanten](../../extensibility/debugger/port-suppliers.md)