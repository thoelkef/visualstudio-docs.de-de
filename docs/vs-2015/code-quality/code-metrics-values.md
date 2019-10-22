---
title: Codemetrikwerte | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics
- code analysis
- measure code quality
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23dba7b7c29c05b55af2c461f36bdaa4b46b948f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667721"
---
# <a name="code-metrics-values"></a>Codemetrikwerte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bei der Codemetrik handelt es sich um eine Reihe von Softwaremaßstäben, die Entwicklern einen besseren Einblick in den von ihnen entwickelten Code bieten. Durch die Nutzung von Codemetriken können Entwickler erkennen, welche Typen und/oder Methoden überarbeitet oder gründlich getestet werden sollen. Entwicklungsteams können potenzielle Risiken erkennen, den aktuellen Status eines Projekts verstehen und den Fortschritt während der Softwareentwicklung nachverfolgen.

## <a name="software-measurements"></a>Software Messungen
 In der folgenden Liste sind die Ergebnisse der Codemetriken aufgeführt, die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] berechnet:

- **Wart barkeits Index** – berechnet einen Indexwert zwischen 0 und 100, der die relative einfache Verwaltung des Codes darstellt. Ein hoher Wert bedeutet eine bessere Wartbarkeit. Farb codierte Bewertungen können verwendet werden, um schnell Probleme im Code zu erkennen. Eine grüne Bewertung liegt zwischen 20 und 100 und zeigt an, dass der Code eine gute Wartbarkeit hat. Eine gelbe Bewertung liegt zwischen 10 und 19 und gibt an, dass der Code nicht nur in der Lage ist. Eine rote Bewertung ist eine Bewertung zwischen 0 und 9 und deutet auf eine geringe Wartbarkeit hin.

- **Zyklomatische Komplexität** – misst die strukturelle Komplexität des Codes. Sie wird erstellt, indem die Anzahl der unterschiedlichen Codepfade im Fluss des Programms berechnet wird. Ein Programm, das eine komplexe Ablauf Steuerung aufweist, erfordert mehr Tests, um eine gute Code Coverage zu erzielen, und es ist weniger wart Bar.

    > [!NOTE]
    > In einigen Fällen unterscheidet sich die Berechnung der zyklomatischen Komplexität für eine Methode in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] von früheren Versionen. Weitere Informationen finden Sie im Abschnitt "Änderungen in Visual Studio 2010 Code Komplexitäts Berechnungen" unter [Problembehandlung bei Code metrikproblemen](../code-quality/troubleshooting-code-metrics-issues.md).

- **Vererbungs Tiefe** – gibt die Anzahl der Klassendefinitionen an, die sich auf den Stamm der Klassenhierarchie ausdehnen. Die tiefere Hierarchie umso schwieriger ist es, zu verstehen, wo bestimmte Methoden und Felder definiert oder/neu definiert werden.

- **Klassen Kopplung** – misst die Kopplung mit eindeutigen Klassen durch Parameter, lokale Variablen, Rückgabe Typen, Methodenaufrufe, generische oder Vorlagen Instanziierungen, Basisklassen, Schnittstellen Implementierungen, für externe Typen definierte Felder und Attribute Auszeichnung. Ein guter Software Entwurf legt fest, dass die Typen und Methoden eine hohe Kohäsion und eine geringe Kopplung aufweisen sollten. Hohe Kopplung weist auf einen Entwurf hin, der aufgrund der vielen Abhängigkeiten von anderen Typen schwierig zu verwenden und zu warten ist.

- **Codezeilen** – gibt die ungefähre Anzahl von Zeilen im Code an. Die Anzahl basiert auf dem IL-Code und ist daher nicht die genaue Anzahl von Zeilen in der Quell Code Datei. Eine sehr hohe Anzahl kann darauf hindeuten, dass ein Typ oder eine Methode versucht, zu viele Aufgaben zu erledigen, und dass Sie aufgeteilt werden sollte. Es kann auch darauf hindeuten, dass der Typ oder die Methode möglicherweise schwierig zu verwalten ist.

## <a name="anonymous-methods"></a>Anonyme Methoden
 Eine *anonyme Methode* ist nur eine Methode, die über keinen Namen verfügt. Anonyme Methoden werden am häufigsten verwendet, um einen Codeblock als Delegatparameter zu übergeben. Metrikergebnisse für eine anonyme Methode, die in einem Member deklariert wird, z. b. eine Methode oder ein Accessor, werden dem Member zugeordnet, der die Methode deklariert. Sie sind nicht mit dem Member verknüpft, der die-Methode aufruft.

 Weitere Informationen zur Vorgehensweise beim behandeln anonymer Methoden durch Codemetriken finden Sie unter [Anonyme Methoden und Code Analyse](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Generierter Code
 Einige Software Tools und Compiler generieren Code, der einem Projekt hinzugefügt wird und der vom Projektentwickler entweder nicht angezeigt wird oder nicht geändert werden darf. Größtenteils ignoriert Codemetriken generierten Code, wenn die Metrikwerte berechnet werden. Dadurch können die Metrikwerte angeben, was der Entwickler sehen und ändern kann.

 Für Windows Forms generierter Code wird nicht ignoriert, da es sich um einen Code handelt, den der Entwickler sehen und ändern kann.

## <a name="see-also"></a>Siehe auch
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
