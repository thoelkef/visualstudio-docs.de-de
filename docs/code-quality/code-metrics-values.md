---
title: In Visual Studio Codemetrik berechnen | Microsoft Docs
ms.custom: 
ms.date: 12/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 553ed7d6a6fcc2edef436251d720919fe399653a
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="code-metrics-values"></a>Codemetrikwerte

Zudem erhöht die zunehmenden Komplexität der modernen softwareanwendungen schwierigkeiten versteht man den Code, zuverlässig und verwaltbar. Bei der Codemetrik handelt es sich um eine Reihe von Softwaremaßstäben, die Entwicklern einen besseren Einblick in den von ihnen entwickelten Code bieten. Durch Codemetrik nutzen, können Entwickler verstehen, welche Typen und/oder Methoden überarbeitet oder mehr gründlich getestet werden sollen. Entwicklungsteams können potenzielle Risiken zu identifizieren, den aktuellen Status eines Projekts verstehen und Nachverfolgen des Status bei der Softwareentwicklung.

Entwickler können Visual Studio zum Generieren von Codemetrikdaten, die die Komplexität und verwaltbarkeit verwalteten Codeprobleme zu messen. Codemetrikdaten können für eine gesamte Projektmappe oder ein einzelnes Projekt generiert werden.

Informationen zum Generieren von Codemetrikdaten in Visual Studio finden Sie unter [wie: Generieren von Codemetrikdaten](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Software-Maßangaben

Die folgende Liste enthält den Code Metrikergebnisse, die Visual Studio berechnet:

- **Wartbarkeitsindex** -berechnet einen Indexwert zwischen 0 und 100, der relativ einfach zu pflegen des Codes darstellt. Ein hoher Wert bedeutet eine bessere Verwaltbarkeit. Farblich codiert Bewertungen können verwendet werden, um Problempunkte im Code schnell zu identifizieren. Eine grüne Bewertung liegt zwischen 20 und 100 und gibt an, dass der Code gute Verwaltbarkeit aufweist. Eine gelbe Bewertung liegt zwischen 10 und 19 und gibt an, dass der Code leicht verwaltet werden. Eine rote Bewertung wird eine Bewertung zwischen 0 und 9 und niedrig verwaltbarkeit angibt.

- **Zyklomatische Komplexität** -misst die strukturelle Komplexität des Codes. Es wird durch die Berechnung der Anzahl der unterschiedlichen Codepfaden in den Fluss des Programms erstellt. Ein Programm, das komplexe ablaufsteuerung benötigen mehr Tests guten codeabdeckung zu erreichen, und es werden weniger verwaltbar.

- **Vererbungstiefe** -gibt die Anzahl der Klassendefinitionen, die auf den Stamm der Hierarchie von Klassen erweitern. Je tiefer sich die Hierarchie der schwieriger zu verstehen, in denen bestimmte Methoden und Felder definiert sind möglicherweise oder / und neu definiert.

- **-Klasse Kopplung** -misst die Kopplung eindeutige Klassen über Parameter, lokale Variablen, Rückgabetypen, Methodenaufrufe, generische oder Vorlagenklasse Instanziierungen, Basisklassen, schnittstellenimplementierungen, Felder für externe Typen definiert und Ergänzung des Attributs. Gute Software Entwurfsprinzipien verlangen, dass die Typen und Methoden hohen Kohäsion haben und arbeitet mit einer geringen Kopplung sollten. Hohe Kopplung gibt an, einen Entwurf, die schwer zu wiederverwenden und aufgrund seiner viele Abhängigkeiten von anderen Typen verwalten.

- **Codezeilen** -gibt die ungefähre Anzahl der Zeilen im Code. Die Anzahl die basiert auf den IL-Code und ist daher nicht die genaue Anzahl der Zeilen in der Quellcodedatei. Eine sehr hohe Anzahl wird angegeben, dass ein Typ oder eine Methode versucht, zu viel Arbeit zu erledigen und aufgeteilt werden sollte. Es kann auch angeben, dass der Typ oder eine Methode möglicherweise schwer zu verwalten.

## <a name="anonymous-methods"></a>Anonymen Methoden

Ein *anonyme Methode* ist nur eine Methode, die keinen Namen hat. Anonyme Methoden werden am häufigsten verwendet, um einen Codeblock als Delegatparameter zu übergeben. Metrikergebnisse für eine anonyme Methode, die in einem Member, z. B. eine Methode oder einen Accessor, deklariert ist, sind das Element, das die Methode deklariert zugeordnet. Sie sind nicht das Element, das die Methodenaufrufe zugeordnet.

Weitere Informationen dazu, wie anonyme Methoden in der Codemetrik behandelt, finden Sie unter [anonyme Methoden und Codeanalyse](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Generierter code

Einige Softwaretools und der Compiler generiert Code, der einem Projekt hinzugefügt wird und, die der Projektentwickler erkennt nicht oder nicht ändern sollen. In den meisten Fällen ignoriert Codemetrik generierten Code, wenn die Metrikwerte berechnet. Dadurch werden die Metrikwerte widerspiegeln, was vom Entwickler angezeigt und ändern kann.

Für Windows Forms generierten Code wird nicht ignoriert, da es sich um Code handelt, die der Entwickler anzeigen und ändern kann.

## <a name="next-steps"></a>Nächste Schritte

- [Vorgehensweise: Generieren von Codemetrikdaten](../code-quality/how-to-generate-code-metrics-data.md)
- [Verwenden des Fensters Codemetrikergebnisse](../code-quality/working-with-code-metrics-data.md)