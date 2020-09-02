---
title: Ausführen von schnellen Aktionen mit Glühbirnen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 990ee487-cf9a-4b89-9784-e7b47c220e8c
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 78ac9b0aba4e56b2240ef65783231d31d77e5144
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670352"
---
# <a name="perform-quick-actions-with-light-bulbs"></a>Ausführen von schnellen Aktionen mit Glühbirnen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Glühbirnen sind ein neues Produktivitätsfeature in Visual Studio 2015. Es sind Symbole, die im Visual Studio-Editor angezeigt werden und auf die Sie klicken können, um schnelle Aktionen auszuführen, einschließlich des Refactorings und der Fehlerbehebung. Glühbirnen bieten eine Fehlerbehebungs- und Refactoringunterstützung an einem einzelnen Blickpunkt, und zwar oftmals rechts von der Zeile, in der Sie Ihre Eingaben vornehmen.

 ![Kleines Glühbirnensymbol](../ide/media/vs2015-lightbulbsmall.png "VS2015_LightBulbSmall")

 In C# und Visual Basic sehen Sie eine Glühbirne, wenn eine rote Wellenlinie vorhanden ist und Visual Studio über eine Empfehlung verfügt, um das Problem zu beheben. Wenn beispielsweise ein Fehler durch eine rote Wellenlinie gekennzeichnet ist, wird eine Glühbirne angezeigt, wenn Behebungsmaßnahmen für diesen Fehler verfügbar sind. Wenn Sie in C++ einer Headerdatei eine neue Funktion hinzufügen, wird eine Glühbirne angezeigt, die das Erstellen einer Stubimplementierung dieser Funktion ermöglicht. Für jede Sprache können Drittanbieter benutzerdefinierte Diagnosen und Empfehlungen bereitstellen, beispielsweise als Bestandteil eines SDKs. Anhand dieser Regeln leuchten Visual Studio-Glühbirnen dann auf.

## <a name="to-see-a-light-bulb"></a>So zeigen Sie eine Glühbirne an

1. In vielen Fällen werden Glühbirnen spontan angezeigt, wenn Sie mit dem Mauszeiger auf die Position eines Fehlers zeigen, oder am linken Rand des Editors, wenn Sie die Einfügemarke in eine Zeile verschieben, die einen Fehler enthält. Wenn eine rote Wellenlinie angezeigt wird, können Sie den Mauszeiger darüber bewegen, um die Glühbirne anzuzeigen. Sie können auch veranlassen, dass eine Glühbirne angezeigt wird, wenn Sie die Maus oder Tastatur verwenden, um zu einem beliebigen Punkt in der Zeile zu wechseln, wo das Problem auftritt.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG+.**, um die Glühbirne aufzurufen und direkt zur Liste mit den potenziellen Fehlerbehebungen zu wechseln.

   ![Glühbirne mit Mauszeigerbewegung](../ide/media/vs2015-lightbulb-hover.png "VS2015_LightBulb_Hover")

## <a name="to-see-potential-fixes"></a>So zeigen Sie potenzielle Fehlerbehebungen an
 Klicken Sie entweder auf den Pfeil nach unten oder auf den Link zum Anzeigen von potenziellen Fehlerbehebungen, um eine Liste von schnellen Aktionen anzuzeigen, die die Glühbirne für Sie vornehmen kann.

 ![Erweiterte Glühbirne](../ide/media/vs2015-lightbulb-hover-expanded.png "VS2015_LightBulb_hover_expanded")

## <a name="to-do-a-refactoring"></a>So nehmen Sie ein Refactoring vor
 Sie können weiterhin Umgestaltungen vornehmen, indem Sie mit der rechten Maustaste klicken, um das Kontextmenü anzuzeigen. Sie können dazu jedoch auch die STRG-Taste + . drücken, um Umgestaltungsoptionen anzuzeigen. In der folgenden Abbildung wird die Umgestaltung "Methode extrahieren" nach dem Drücken auf die STRG-Taste + . angezeigt, und zwar auf einem beliebigen Punkt auf der Zeile, die den `Math.Abs`-Aufruf enthält:

 ![Glühbirne, die Umgestaltungsoptionen zeigt](../ide/media/vs2015-lightbulbs-refactor.png "VS2015_LightBulbs_refactor")
