---
title: DateTime- und TimeSpan-Darstellungen in Windows-Runtime | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime dates and times
- TimeSpan [JavaScript]
- DateTime [JavaScript]
ms.assetid: 9743e9ac-9054-463e-8264-427183e4905f
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d7c394b57eb0215e3dff857d935b367e602c2b0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="windows-runtime-datetime-and-timespan-representations"></a>DateTime- und TimeSpan-Darstellungen in Windows-Runtime
Die Darstellung von Datum und Uhrzeit in JavaScript unterscheidet sich von der Windows-Runtime-Version. Die Struktur von [DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx) in Windows Runtime wird in JavaScript als [Datum](../javascript/reference/date-object-javascript.md) mit einem Sicherungsspeicher dargestellt, der den `DateTime`-Daten entspricht (und gegenüber dem JavaScript-`Date` einen anderen Bereich und eine andere Genauigkeit aufweist). Modifiziert man dieses benutzerdefinierte `Date`-Objekt, so wird es ein standardmäßiges JavaScript-`Date` und verliert die Genauigkeit. JavaScript-`Date`werte können an ein Windows-Runtime-`DateTime` übergeben werden und werden hinsichtlich des Bereichs überprüft, was zu Ausnahmen führen kann.  
  
 Die Struktur von [TimeSpan](http://msdn.microsoft.com/en-us/c5defb66-819c-4796-85b5-07ed249a5d86) in Windows-Runtime wird in Millisekunden konvertiert und als JavaScript-Nummer ausgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Windows-Runtime in JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)