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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301494"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Neuerungen beim Entwurf in Visual Studio 2017

## <a name="live-dependency-validation"></a>Live-Abhängigkeitsvalidierung

Das Entfernen unerwünschter Abhängigkeiten ist ein wichtiger Teil der Verwaltung Ihrer technischen Schulden. Visual Studio bietet eine Live-Validierung von Abhängigkeiten, einschließlich präziser Informationen zu Problemen, z. B. dem Ort, an dem sie sich befinden. Die Live-Abhängigkeitsüberprüfung nutzt die Vorteile neuer Funktionen in der Fehlerliste und im Editor voll aus.

![Live-Abhängigkeitsvalidierung in Aktion](media/dep-validation-whatsnew-01.png)

Die Erstellungserfahrung hat sich geändert, um die Abhängigkeitsüberprüfung besser auffindbar und zugänglicher zu machen. Die Terminologie wurde von "Layer-Diagramm" in "Abhängigkeitsdiagramm" geändert.

Das Menü **Architektur** enthält nun einen Befehl zum direkten Erstellen eines Abhängigkeitsdiagramms:

![Live-Abhängigkeitselement im Menü Architektur](media/dep-validation-whatsnew-02.png)

Layer-Eigenschaftsnamen und -beschreibungen wurden geändert, um sie aussagekräftiger zu gestalten:

![Live-Abhängigkeit aktualisierte Eigenschaftsnamen](media/dep-validation-whatsnew-03.png)

Sie sehen sofort die Auswirkungen Ihrer Änderungen in den Analyseergebnissen für den aktuellen Code in der Projektmappe jedes Mal, wenn Sie das Diagramm speichern. Sie müssen nicht auf den Abschluss des Befehls **Abhängigkeiten** überprüfen warten.

Weitere Informationen finden Sie in [diesem Blogbeitrag](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>UML-Designer wurden entfernt

Die UML-Designer wurden aus Visual Studio entfernt.

* UML-Diagramme werden jetzt als XML-Dateien dargestellt
* Der UML-Modell-Explorer ist nicht mehr vorhanden.
* Modellierungsprojektreferenzen werden nicht mehr für die Abhängigkeitsüberprüfung verwendet.
* Der Knoten "Layer-Referenzen" im Projektmappen-Explorer wird nicht mehr angezeigt
* Die Buildaktion "Validieren" für ein Abhängigkeitsdiagramm (Layer) wird nicht mehr verwendet - der Build-Task wurde entfernt.
* Die Projektstruktur wird für das Round-Tripping zwischen Versionen
* Sie können ein Abhängigkeitsdiagramm (Layer) weiterhin als XML öffnen, erstellen, bearbeiten und speichern.
* AUF TFS-Arbeitsaufgaben, die mit einem Abhängigkeitsdiagramm (Layer) verknüpft sind, kann auf der Entwurfsoberfläche nicht zugegriffen werden.
* Die Wiederverknüpfung von zu DSL oder einem Layer wird nicht mehr unterstützt
* UML-Erweiterbarkeit im Modeling SDK wird nicht mehr unterstützt

Unterstützung für die Visualisierung der Architektur von .NET- und C++-Code ist über [Codemaps](map-dependencies-across-your-solutions.md)verfügbar.

Wenn Sie ein wichtiger Benutzer der UML-Designer sind, können Sie Visual Studio 2015 oder frühere Versionen weiterhin verwenden, während Sie sich für ein alternatives Tool für Ihre UML-Anforderungen entscheiden.

Weitere Informationen finden Sie in [diesem Blogbeitrag](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Edition-Unterstützung für Architektur- und Modellierungstools

Visual Studio ist in mehreren Editionen verfügbar. Nicht alle bieten Unterstützung für die Architektur und Modellierungstools. Die folgende Tabelle zeigt die Verfügbarkeit jedes Tools.

|**Feature**|**Enterprise-Edition**|**Professionelle Ausgabe**|**Community-Ausgabe**|
|-|-|-|-|
|**Codezuordnungen**|Ja|Unterstützt nur das Lesen von Codezuordnungen, das Filtern von Codezuordnungen, das Hinzufügen neuer generischer Knoten und das Erstellen eines neuen gerichteten Diagramms aus einer Auswahl.|-|
|**Abhängigkeitsdiagramme**|Ja|Unterstützt nur das Lesen von Abhängigkeitsdiagrammen.|Unterstützt nur das Lesen von Abhängigkeitsdiagrammen.|
|**Gerichtete Diagramme** (DGML-Diagramme)|Ja|Ja|Ja|
|**Codeklon**|Ja|-|-|
