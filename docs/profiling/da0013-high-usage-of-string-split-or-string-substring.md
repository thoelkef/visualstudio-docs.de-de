---
title: 'DA0013: Umfangreiche Verwendung von String.Split oder String.Substring | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c218dd9a7ee3266de2cf9e07933ed69aa23e73e7
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749881"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Umfangreiche Verwendung von String.Split oder String.Substring
|||  
|-|-|  
|Regel-ID|DA0013|  
|Kategorie|Hinweise zur .NET Framework-Verwendung|  
|Profilerstellungsmethoden|Sampling|  
|Meldung|Sie sollten eine Reduzierung der String.Split- und String.Substring-Funktionen in Betracht ziehen.|  
|Regeltyp|Warnung|  
  
## <a name="cause"></a>Ursache  
 Aufrufe der System.String.Split-Methode oder der System.String.Substring-Methode machen einen großen Teil der Profilerstellungsdaten aus. Verwenden Sie ggf. „System.String.IndexOf“ oder „System.String.IndexOfAny“, wenn Sie testen möchten, ob in einer Zeichenfolge eine Teilzeichenfolge vorhanden ist.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Die Split-Methode wirkt auf ein Zeichenfolgenobjekt und gibt ein neues Zeichenfolgenarray zurück, das die Teilzeichenfolgen des Originals enthält. Die Funktion belegt Speicher für das zurückgegebene Arrayobjekt und ordnet ein neues Zeichenfolgenobjekt für jedes gefundene Arrayelement zu. Auf ähnliche Weise behandelt die Substr-Methode ein Zeichenfolgenobjekt und gibt eine neue Zeichenfolge zurück, die der angeforderten Teilzeichenfolge entspricht.  
  
 Wenn die Verwaltung von Speicherbelegungen in der Anwendung wichtig ist, sollten Sie Alternativen zur String.Split-Methode und String.Substr-Methode verwenden. So können Sie beispielsweise mit der IndexOf-Methode oder mit der IndexOfAny-Methode eine bestimmte Teilzeichenfolge innerhalb einer Zeichenfolge suchen, ohne eine neue Instanz der Zeichenfolgenklasse zu erstellen.  
  
## <a name="how-to-investigate-a-warning"></a>Vorgehensweise zur Überprüfung einer Warnung  
 Doppelklicken Sie auf die Meldung im Fenster **Fehlerliste**, um zur [Funktionsdetailansicht](../profiling/function-details-view.md) der Samplingprofildaten zu navigieren. Suchen Sie in den aufrufenden Funktionen nach den Programmabschnitten, in denen die System.String.Split-Methode oder die System.String.Substr-Methode am häufigsten verwendet wird. Wenn möglich können Sie mit der IndexOf-Methode oder mit der IndexOfAny-Methode eine bestimmte Teilzeichenfolge innerhalb einer Zeichenfolge suchen, ohne eine neue Instanz der Zeichenfolgenklasse zu erstellen.