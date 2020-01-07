---
title: Neuerungen beim Entwurf in Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 6f81cc32604abe6d90ac0d263574e97df35c63bd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593498"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Neuerungen beim Entwurf in Visual Studio 2017

## <a name="live-dependency-validation"></a>Liveüberprüfung von Abhängigkeiten

Entfernen unerwünschte Abhängigkeiten ist ein wichtiger Bestandteil der verwalten Ihre technischen Schulden. Visual Studio bietet eine Live Validierung der Abhängigkeiten, einschließlich präziser Informationen zu Problemen, z. b. wo Sie sich befinden. Die Live-Abhängigkeits Überprüfung bietet vollständige Vorteile der neuen Features im Fehlerliste und im Editor.

![Live-abhängigkeitsüberprüfung in Aktion](media/dep-validation-whatsnew-01.png)

Die Erstellungs Funktion wurde geändert, damit die Abhängigkeits Überprüfung leichter erkennbar und leichter zugänglich ist. Die Terminologie wurde von "ebenendiagramm" in "Abhängigkeits Diagramm" geändert.

Die **Architektur** enthält einen Befehl aus, um direkt zu einem Abhängigkeitsdiagramm erstellen:

![Liveüberprüfung von Abhängigkeiten-Element, auf das Menü "Architektur"](media/dep-validation-whatsnew-02.png)

Ebeneneigenschaftennamen und Beschreibungen wurden geändert, um Sie aussagekräftiger zu machen:

![Eigenschaftennamen aktualisiert liveüberprüfung von Abhängigkeiten](media/dep-validation-whatsnew-03.png)

Wenn Sie das Diagramm speichern, sehen Sie sofort die Auswirkung Ihrer Änderungen in den Analyseergebnissen auf den aktuellen Code in der Projekt Mappe. Sie müssen nicht auf den Abschluss des Befehls " **Abhängigkeiten** überprüfen" warten.

Weitere Informationen finden Sie unter [in diesem Blogbeitrag](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>UML-Designern wurden entfernt.

Die UML-Designer wurden aus Visual Studio entfernt.

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

Unterstützung für die Visualisierung der Architektur von .net C++ und Code ist über [Code Maps](map-dependencies-across-your-solutions.md)verfügbar.

Wenn Sie eine erhebliche UML-Designern verwenden, können Sie weiterhin Visual Studio 2015 oder früher verwenden, während Sie möchten eine alternative Tool für Ihre Anforderungen UML.

Weitere Informationen finden Sie unter [in diesem Blogbeitrag](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Edition-Unterstützung für Architektur- und Modellierungstools

Visual Studio ist in verschiedenen Editionen verfügbar. Nicht alle diese bieten Unterstützung für die Architektur- und Modellierungstools. Die folgende Tabelle zeigt die Verfügbarkeit jedes Tools.

|**Funktion**|**Enterprise edition**|**Professional-edition**|**Community-edition**|
|-|-|-|-|
|**Codezuordnungen**|Ja|Nur ordnet unterstützt das Lesen von Code Maps, Code zu filtern, Hinzufügen neuer allgemeiner Knoten und das Erstellen eines neuen gerichteten Diagramms aus einer Auswahl.|-|
|**Abhängigkeitsdiagramme**|Ja|Unterstützt Sie nur das Lesen von Abhängigkeitsdiagrammen.|Unterstützt Sie nur das Lesen von Abhängigkeitsdiagrammen.|
|**Gerichtete Diagramme** (DGML-Diagramme)|Ja|Ja|Ja|
|**Codeklon**|Ja|-|-|
