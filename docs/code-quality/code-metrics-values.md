---
title: Codemetrik berechnen
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ece5c08ca3aa4a9f5e5329dbf6d5fd6c9087d085
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886416"
---
# <a name="code-metrics-values"></a>Codemetrikwerte

Die höhere Komplexität der modernen Anwendungen erhöht sich auch die Schwierigkeit den Code zuverlässig und verwaltbar zu machen. Bei der Codemetrik handelt es sich um eine Reihe von Softwaremaßstäben, die Entwicklern einen besseren Einblick in den von ihnen entwickelten Code bieten. Durch die Codemetrik nutzen, können Entwickler verstehen, die Methoden und/oder überarbeitet oder gründlicher getestet werden soll. Entwicklungsteams können identifizieren potenzielle Risiken bestehen, den aktuellen Status eines Projekts verstehen und Nachverfolgen des Status bei der Softwareentwicklung.

Entwickler können Visual Studio verwenden, zum Generieren von Codemetrikdaten werden, die die Komplexität und verwaltbarkeit ihrer verwalteten Codes messen. Codemetrikdaten können für eine gesamte Projektmappe oder ein einzelnes Projekt generiert werden.

Weitere Informationen zum Generieren von Codemetrikdaten werden in Visual Studio, finden Sie unter [wie: Generieren von Codemetrikdaten](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Software-Messungen

Die folgende Liste enthält den Code Metriken dazu führt, die Visual Studio berechnet:

- **Wartbarkeitsindex** -berechnet einen Indexwert zwischen 0 und 100 an, der relativ einfachen pflegen des Codes darstellt. Ein hoher Wert bedeutet, dass eine bessere Verwaltbarkeit. Farbcodiert Bewertungen können verwendet werden, um Problemstellen in Ihrem Code schnell zu identifizieren. Eine grüne Bewertung zwischen 20 und 100 und gibt an, dass der Code gute wartbarkeit. Eine gelbe Bewertung liegt zwischen 10 und 19 und gibt an, dass der Code nicht so verwaltet werden. Eine rote Bewertung wird eine Bewertung zwischen 0 und 9 und niedrige wartbarkeit. Weitere Informationen finden Sie im Abschnitt [Wartbarkeitsindex Bereich und Bedeutung](https://blogs.msdn.microsoft.com/codeanalysis/2007/11/20/maintainability-index-range-and-meaning/) .

- **Zyklomatische Komplexität** -misst die strukturelle Komplexität des Codes. Es wird durch die Berechnung der Anzahl der unterschiedlichen Codepfaden im Datenfluss des Programms erstellt. Ein Programm, das eine komplexe Ablauf Steuerung aufweist, erfordert mehr Tests, um eine gute Code Coverage zu erzielen und weniger wart Bar zu sein. Weitere Informationen finden Sie im [Wikipedia-Eintrag für die zyklomatische Komplexität](https://wikipedia.org/wiki/Cyclomatic_complexity).

- **Vererbungs Tiefe** : gibt die Anzahl der verschiedenen Klassen an, die von einem anderen erben, bis hin zur Basisklasse. Die Vererbungs Tiefe ähnelt der Klassen Kopplung darin, dass sich eine Änderung in einer Basisklasse auf eine beliebige geerbte Klasse auswirken kann. Je höher diese Zahl ist, desto tiefer die Vererbung und desto höher ist das Potenzial für Basisklassen Änderungen, die zu einer Breaking Change führen. Bei einer tiefen Vererbung ist ein niedriger Wert gut, und ein hoher Wert ist schlecht.

- **-Klasse Kopplung** -misst die Kopplung auf eindeutige Klassen über Parameter, lokale Variablen, Rückgabetypen, Methodenaufrufe, generische oder Vorlagenklasse Instanziierungen, Basisklassen, schnittstellenimplementierungen, Felder, die auf externe Typen definiert und Attributdekoration. Guter Software Entwurfsprinzipien verlangen, dass die Typen und Methoden sollten eine hohen Kohäsion aufweisen und loser Kopplung. Hohe Kopplung gibt an, ein Design, das ist schwierig, wiederverwenden und verwalten aufgrund der vielen Abhängigkeiten auf anderen Typen. Weitere Informationen finden Sie im Blogbeitrag [Klassen Kopplung](https://blogs.msdn.microsoft.com/zainnab/2011/05/25/code-metrics-class-coupling/) .

::: moniker range=">=vs-2019"

- **Zeilen des Quellcodes** : gibt die genaue Anzahl von Quell Codezeilen an, die in der Quelldatei vorhanden sind, einschließlich leerer Zeilen. Diese Metrik ist ab Visual Studio 2019 Version 16,4 und Microsoft. Code Analysis. metics (2.9.5) verfügbar.

- **Zeilen des ausführbaren Codes** : gibt die ungefähre Anzahl von ausführbaren Codezeilen oder Vorgängen an. Dies ist eine Anzahl von Vorgängen in ausführbarem Code. Diese Metrik ist ab Visual Studio 2019 Version 16,4 und Microsoft. Code Analysis. metics (2.9.5) verfügbar. Der Wert ist in der Regel eine genaue Entsprechung zur vorherigen Metrik, **Code Zeilen**, bei der es sich um die auf MSIL-Anweisungen basierende Metrik handelt, die im Legacy Modus verwendet wird.
::: moniker-end
::: moniker range="vs-2017"

- **Codezeilen** -gibt die ungefähre Anzahl der Zeilen im Code. Die Anzahl wird basierend auf den IL-Code und ist daher nicht die genaue Anzahl von Zeilen in der Quellcodedatei. Eine hohe Anzahl kann darauf hindeuten, dass ein Typ oder eine Methode versucht, zu viele Aufgaben zu erledigen und aufgeteilt zu werden. Es möglicherweise, dass der Typ oder die Methode möglicherweise schwer zu verwalten.

   > [!NOTE]
   > Die [Befehlszeilenversion](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) des Codes Metriken Tool zählt tatsächliche Codezeilen erforderlich, da den Quellcode anstelle von IL analysiert.
::: moniker-end

## <a name="anonymous-methods"></a>Anonymen Methoden

Ein *anonyme Methode* ist einfach eine Methode, die keinen Namen hat. Anonyme Methoden werden am häufigsten verwendet, um einen Codeblock als Delegatparameter zu übergeben. Codemetrikergebnisse für eine anonyme Methode, die in einem Member deklariert wird, z. b. eine Methode oder ein Accessor, werden dem Member zugeordnet, der die Methode deklariert. Sie sind nicht das Element, das die Methode ruft zugeordnet.

## <a name="generated-code"></a>Generierter code

Einige Softwaretools und Compiler Generieren von Code zu einem Projekt hinzugefügt wird und, die der Projektentwickler wird nicht angezeigt oder sollte nicht geändert werden. In der Regel ignoriert Codemetrik generierten Code, wenn die Metrikwerte berechnet. Dies ermöglicht die Metrikwerte widerspiegeln, was Entwickler anzeigen und ändern kann.

Für Windows Forms generierten Code wird nicht ignoriert, da es sich um Code handelt, die der Entwickler anzeigen und ändern kann.

## <a name="next-steps"></a>Nächste Schritte

- [Gewusst wie: Generieren von Codemetrikdaten](../code-quality/how-to-generate-code-metrics-data.md)
- [Verwenden Sie das Fenster Codemetrikergebnisse](../code-quality/working-with-code-metrics-data.md)
