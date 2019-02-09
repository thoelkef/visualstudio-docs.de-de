---
title: Codemetrik berechnen
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f989e5ec028f3a296585c54eb17b54f4da7c1cf0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55917726"
---
# <a name="code-metrics-values"></a>Codemetrikwerte

Die höhere Komplexität der modernen Anwendungen erhöht sich auch die Schwierigkeit den Code zuverlässig und verwaltbar zu machen. Bei der Codemetrik handelt es sich um eine Reihe von Softwaremaßstäben, die Entwicklern einen besseren Einblick in den von ihnen entwickelten Code bieten. Durch die Codemetrik nutzen, können Entwickler verstehen, die Methoden und/oder überarbeitet oder gründlicher getestet werden soll. Entwicklungsteams können identifizieren potenzielle Risiken bestehen, den aktuellen Status eines Projekts verstehen und Nachverfolgen des Status bei der Softwareentwicklung.

Entwickler können Visual Studio verwenden, zum Generieren von Codemetrikdaten werden, die die Komplexität und verwaltbarkeit ihrer verwalteten Codes messen. Codemetrikdaten können für eine gesamte Projektmappe oder ein einzelnes Projekt generiert werden.

Weitere Informationen zum Generieren von Codemetrikdaten werden in Visual Studio, finden Sie unter [Vorgehensweise: Generieren von Codemetrikdaten](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Software-Messungen

Die folgende Liste enthält den Code Metriken dazu führt, die Visual Studio berechnet:

- **Wartbarkeitsindex** -berechnet einen Indexwert zwischen 0 und 100 an, der relativ einfachen pflegen des Codes darstellt. Ein hoher Wert bedeutet, dass eine bessere Verwaltbarkeit. Farbcodiert Bewertungen können verwendet werden, um Problemstellen in Ihrem Code schnell zu identifizieren. Eine grüne Bewertung zwischen 20 und 100 und gibt an, dass der Code gute wartbarkeit. Eine gelbe Bewertung liegt zwischen 10 und 19 und gibt an, dass der Code nicht so verwaltet werden. Eine rote Bewertung wird eine Bewertung zwischen 0 und 9 und niedrige wartbarkeit.

- **Zyklomatische Komplexität** -misst die strukturelle Komplexität des Codes. Es wird durch die Berechnung der Anzahl der unterschiedlichen Codepfaden im Datenfluss des Programms erstellt. Ein Programm, das komplexe ablaufsteuerung hat ist benötigen weitere Tests gute Code Coverage zu erreichen und schlechter zu verwalten.

- **Vererbungstiefe** -gibt die Anzahl von Klassendefinitionen, die auf den Stamm der Hierarchie von Klassen erweitern. Je tiefer sich der Hierarchie der schwieriger zu verstehen, in denen bestimmte Methoden und Felder definiert sind möglicherweise oder / und neu definiert.

- **-Klasse Kopplung** -misst die Kopplung auf eindeutige Klassen über Parameter, lokale Variablen, Rückgabetypen, Methodenaufrufe, generische oder Vorlagenklasse Instanziierungen, Basisklassen, schnittstellenimplementierungen, Felder, die auf externe Typen definiert und Attributdekoration. Guter Software Entwurfsprinzipien verlangen, dass die Typen und Methoden sollten eine hohen Kohäsion aufweisen und loser Kopplung. Hohe Kopplung gibt an, ein Design, das ist schwierig, wiederverwenden und verwalten aufgrund der vielen Abhängigkeiten auf anderen Typen.

- **Codezeilen** -gibt die ungefähre Anzahl der Zeilen im Code. Die Anzahl wird basierend auf den IL-Code und ist daher nicht die genaue Anzahl von Zeilen in der Quellcodedatei. Eine sehr hohe Anzahl hinweisen, dass ein Typ oder Methode zu viel Arbeit zu erledigen möchte und verteilt werden soll. Es möglicherweise, dass der Typ oder die Methode möglicherweise schwer zu verwalten.

   > [!NOTE]
   > Die [Befehlszeilenversion](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) des Codes Metriken Tool zählt tatsächliche Codezeilen erforderlich, da den Quellcode anstelle von IL analysiert.

## <a name="anonymous-methods"></a>Anonymen Methoden

Ein *anonyme Methode* ist einfach eine Methode, die keinen Namen hat. Anonyme Methoden werden am häufigsten verwendet, um einen Codeblock als Delegatparameter zu übergeben. Metrikergebnisse für eine anonyme Methode, die in einem Element, z. B. eine Methode oder der Accessor deklariert wird werden das Element, das die Methode deklariert zugeordnet. Sie sind nicht das Element, das die Methode ruft zugeordnet.

Weitere Informationen dazu, wie der Codemetrik anonyme Methoden behandelt, finden Sie unter [anonyme Methoden und Codeanalyse](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Generierter code

Einige Softwaretools und Compiler Generieren von Code zu einem Projekt hinzugefügt wird und, die der Projektentwickler wird nicht angezeigt oder sollte nicht geändert werden. In der Regel ignoriert Codemetrik generierten Code, wenn die Metrikwerte berechnet. Dies ermöglicht die Metrikwerte widerspiegeln, was Entwickler anzeigen und ändern kann.

Für Windows Forms generierten Code wird nicht ignoriert, da es sich um Code handelt, die der Entwickler anzeigen und ändern kann.

## <a name="next-steps"></a>Nächste Schritte

- [Vorgehensweise: Generieren von Codemetrikdaten](../code-quality/how-to-generate-code-metrics-data.md)
- [Verwenden Sie das Fenster Codemetrikergebnisse](../code-quality/working-with-code-metrics-data.md)