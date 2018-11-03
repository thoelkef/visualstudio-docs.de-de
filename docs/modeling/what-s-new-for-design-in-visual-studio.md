---
title: Neues beim Entwurf in Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee3c602dfc89aeafbfb82ae50771abc7ce66937e
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966937"
---
# <a name="whats-new-for-design-in-visual-studio"></a>Neues beim Entwurf in Visual Studio

## <a name="live-dependency-validation"></a>Liveüberprüfung von Abhängigkeiten

Entfernen unerwünschte Abhängigkeiten ist ein wichtiger Bestandteil der verwalten Ihre technischen Schulden. Live-Überprüfung von Abhängigkeiten ist jetzt enthalten, genaue Informationen zu Problemen bereitgestellt und vollständig von der neuen Funktionen in der Fehlerliste enthalten und dem Editor profitieren.

![Live-abhängigkeitsüberprüfung in Aktion](media/dep-validation-whatsnew-01.png)

Die Autoren-Benutzeroberfläche hat sich geändert, um die Auffindbarkeit und besser zugänglich sind, ändern die Terminologie von "Ebenendiagramm", "Abhängigkeitsdiagramm" abhängigkeitsüberprüfung zu machen.

Die **Architektur** enthält einen Befehl aus, um direkt zu einem Abhängigkeitsdiagramm erstellen:

![Liveüberprüfung von Abhängigkeiten-Element, auf das Menü "Architektur"](media/dep-validation-whatsnew-02.png)

... und den Eigenschaftennamen in ein Abhängigkeitsdiagramm und deren Beschreibungen, eine Ebene wurden geändert, um aussagekräftigere:

![Eigenschaftennamen aktualisiert liveüberprüfung von Abhängigkeiten](media/dep-validation-whatsnew-03.png)

Sie sehen jetzt die Auswirkungen der Änderungen sofort in die Analyseergebnisse, nach dem aktuellen Code in der Lösung jedes Mal, wenn Sie das Diagramm speichern. Sie müssen nicht mehr auf den Abschluss des Befehls "Abhängigkeiten überprüfen" zu warten.

Weitere Informationen finden Sie unter [in diesem Blogbeitrag](https://blogs.msdn.microsoft.com/devops/2016/10/07/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>UML-Designern wurden entfernt.

Die UML-Designern wurden von der Visual Studio Enterprise-Version entfernt.

* UML-Diagramme werden als XML-Dateien jetzt angezeigt.
* UML-Modell-Explorer ist nicht mehr vorhanden.
* Modellierungsprojekt, die Verweise nicht mehr, für die abhängigkeitsüberprüfung verwendet werden
* Der Knoten "Ebenenverweise" im Projektmappen-Explorer wird nicht mehr angezeigt.
* Die Buildaktion "Überprüfen", in einem Abhängigkeitsdiagramm (Layer) wird nicht mehr verwendet: der Build-Task wurde entfernt
* Die Projektstruktur wird für Roundtrips zwischen den Versionen verwaltet.
* Sie können immer noch öffnen, erstellen, bearbeiten, und speichern ein Abhängigkeitsdiagramm (Layer) als XML
* TFS-Arbeitsaufgaben, die mit einem Abhängigkeitsdiagramm (Layer) verknüpft sind, nicht auf der Entwurfsoberfläche zugegriffen werden kann
* Back Verknüpfen von DSL oder einer Ebene wird nicht mehr unterstützt.
* UML-Erweiterungen in das Modellierungs-SDK wird nicht mehr unterstützt.

Unterstützung für die Architektur von .NET und C++-Code zu visualisieren über verfügbar ist jedoch [von code Maps](map-dependencies-across-your-solutions.md), und die erheblichen Verbesserungen an der abhängigkeitsüberprüfung, die oben beschriebenen.

Wenn Sie eine erhebliche UML-Designern verwenden, können Sie weiterhin Visual Studio 2015 oder früher verwenden, während Sie möchten eine alternative Tool für Ihre Anforderungen UML.

Weitere Informationen finden Sie unter [in diesem Blogbeitrag](https://blogs.msdn.microsoft.com/devops/2016/10/14/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Edition-Unterstützung für Architektur- und Modellierungstools

Visual Studio 2017 ist in mehreren Versionen verfügbar. Nicht alle diese bieten Unterstützung für die Architektur- und Modellierungstools. Die folgende Tabelle zeigt die Verfügbarkeit jedes Tools.

|**Funktion**|**Enterprise edition**|**Professional-edition**|**Community-edition**|
|-|-|-|-|
|**Codezuordnungen**|Ja|Nur ordnet unterstützt das Lesen von Code Maps, Code zu filtern, Hinzufügen neuer allgemeiner Knoten und das Erstellen eines neuen gerichteten Diagramms aus einer Auswahl.|-|
|**Abhängigkeitsdiagramme**|Ja|Unterstützt Sie nur das Lesen von Abhängigkeitsdiagrammen.|Unterstützt Sie nur das Lesen von Abhängigkeitsdiagrammen.|
|**Gerichtete Diagramme** (DGML-Diagramme)|Ja|Ja|Ja|
|**Codeklon**|Ja|-|-|