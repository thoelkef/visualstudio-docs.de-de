---
title: "DateTime- und TimeSpan-Darstellungen in Windows-Runtime | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DateTime [JavaScript]"
  - "JavaScript, Datums- und Uhrzeitangaben für Windows-Runtime"
  - "TimeSpan [JavaScript]"
ms.assetid: 9743e9ac-9054-463e-8264-427183e4905f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# DateTime- und TimeSpan-Darstellungen in Windows-Runtime
Die Darstellung von Datum und Uhrzeit in JavaScript unterscheidet sich von der Windows\-Runtime\-Version.  Die Struktur von Windows Runtime [DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx) wird in JavaScript als [Datum](../javascript/reference/date-object-javascript.md) mit einem Sicherungsspeicher dargestellt, der den `DateTime`\-Daten entspricht \(und gegenüber dem JavaScript\-`Date` einen anderen Bereich und eine andere Genauigkeit aufweist\).  Modifiziert man dieses benutzerdefinierte `Date`\-Objekt, so wird es ein standardmäßiges JavaScript\-`Date` und verliert die Genauigkeit.  JavaScript\-`Date`werte können an ein Windows\-Runtime\-`DateTime` übergeben werden und werden hinsichtlich des Bereichs überprüft, was zu Ausnahmen führen kann.  
  
 Die Struktur der Windows\-Runtime\-[TimeSpan](http://msdn.microsoft.com/de-de/c5defb66-819c-4796-85b5-07ed249a5d86) wird in Millisekunden konvertiert und als eine JavaScript\-Nummer ausgegeben.  
  
## Siehe auch  
 [Verwenden von Windows\-Runtime in JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)