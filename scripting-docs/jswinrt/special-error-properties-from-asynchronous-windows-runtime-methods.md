---
title: Spezielle Fehlereigenschaften asynchroner Windows-Runtime-Methoden | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45155584-06d8-4e7f-93a6-8564a93f643d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 120d8f699c8bedd0fe5762300203c5d5ec18e73e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="special-error-properties-from-asynchronous-windows-runtime-methods"></a>Spezielle Fehlereigenschaften asynchroner Windows-Runtime-Methoden
Beim Debuggen asynchroner Windows-Runtime-Methoden kann es in JavaScript zu Problemen kommen, da der Fehler tief in der Aufrufliste ausgelöst werden kann. Das `Error`-Objekt von JavaScript verfügt über zusätzliche Eigenschaften, die sich nur zeigen, wenn der Fehler von einer asynchronen Windows-Runtime-Methode ausgelöst wird, wenn die App im Debugmodus ausgeführt wird.  
  
## <a name="special-error-properties"></a>Spezielle Fehlereigenschaften  
 Ein Fehlerobjekt, das durch einen fehlgeschlagenen asynchronen Windows-Runtime-Vorgang im Debugmodus entsteht, verfügt über die folgenden speziellen Eigenschaften:  
  
-   `asyncOpSource` (Objekt) Ruft Informationen über den ursprünglichen Speicherort auf, von dem der Aufruf ausging, der einen Fehler ausgelöst hat. Die Eigenschaft `asyncOpSource.originatingCall` (Zeichenfolge) zeigt den Speicherort im Benutzercode an, von dem der asynchrone Vorgang ausging.  
  
-   asyncOpType (Zeichenfolge) Ruft den Namen des asynchronen Vorgangstyps auf, der den Fehler ausgelöst hat.  
  
 Weitere Informationen zu Fehlern bei asynchronen Vorgängen finden Sie unter:  
  
-   [Behandeln von Fehlern mit Zusagen](https://msdn.microsoft.com/en-us/library/windows/apps/hh700337.aspx)  
  
-   [Problembehandlung für Windows-Runtime-Fehler](http://msdn.microsoft.com/en-us/1ef7d7df-82ac-441d-8ad0-54ab1318de64)