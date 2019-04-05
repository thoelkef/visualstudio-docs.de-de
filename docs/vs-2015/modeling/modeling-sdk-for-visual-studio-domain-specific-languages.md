---
title: Modellierungs-SDK - domänenspezifische Sprachen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
ms.assetid: 17a531e2-1964-4a9d-84fd-6fb1b4aee662
caps.latest.revision: 79
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7bcfe986877305c55f6b459b8c519e4f12f5a503
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "59001178"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Modellierungs-SDK für Visual Studio - Domänenspezifische Sprachen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe der Modellierungs-SDK für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (MSDK) können Sie leistungsstarke modellbasierte Entwicklungstools, die Sie in integrieren können erstellen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Als Beispiel werden die UML-Tools mit MSDK erstellt. Auf diese Weise können Sie eine oder mehrere Modelldefinitionen erstellen und diese in einen Toolsatz integrieren.

 Im Mittelpunkt von MSDK befindet sich die Definition eines Modells, das Sie erstellen, um Konzepte in Ihrem Geschäftsbereich darzustellen. Sie können das Modell mit einer Vielzahl von Tools umgeben, z. B. mit einer Diagrammansicht, der Möglichkeit zur Generierung von Code und anderen Artefakten, Befehlen zum Transformieren des Modells und der Möglichkeit zur Interaktion mit Code und anderen Objekten in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Während Sie das Modell entwickelt, können Sie es mit anderen Modellen und Tools kombinieren, um ein leistungsstarkes Toolset zu erstellen, das auf ihre Entwicklung ausgerichtet ist.

 Mit MSDK können Sie ein Modell schnell in Form einer domänenspezifischen Sprache (DSL) entwickeln. Sie beginnen, indem Sie einen spezialisierten Editor verwenden, um ein Schema oder eine abstrakte Syntax zusammen mit einer grafischen Schreibweise zu definieren. Aus dieser Definition generiert VMSDK Folgendes:

- Eine Implementierung des Modells mithilfe einer stark typisierten API, die in einem transaktionsbasierten Speicher ausgeführt wird.

- Ein strukturbasierter Explorer.

- Ein grafischer Editor, in dem Benutzer das Modell bzw. Teile davon, die Sie definieren, anzeigen können.

- Serialisierungsmethoden, mit denen die Modelle in lesbarem XML gespeichert werden.

- Funktionen zum Generieren des Programmcodes und anderer Artefakte mithilfe von Textvorlagen.

  Sie können alle diese Funktionen anpassen und erweitern. Ihre Erweiterungen sind so integriert, dass Sie noch die DSL-Definition aktualisieren und Funktionen erneut generieren können, ohne die Erweiterungen zu verlieren.

## <a name="samples-and-the-latest-information"></a>Beispiele und aktuelle Informationen
 [Das Modeling SDK für Visual Studio 2015 herunterladen](http://www.microsoft.com/download/details.aspx?id=48148)

 [Beispiele für](http://go.microsoft.com/fwlink/?LinkId=186128) für den Modellierungs-SDK für Visual Studio.

 Die Anleitung in fortgeschrittenen Techniken und Problembehandlung, finden Sie unter [Forum von Visual Studio DSL & Modellierungstool-Erweiterbarkeit](http://go.microsoft.com/fwlink/?LinkID=186074).

## <a name="in-this-section"></a>In diesem Abschnitt
 [Erste Schritte mit domänenspezifischen Sprachen](../modeling/getting-started-with-domain-specific-languages.md)

 [Grundlagen von Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md)

 [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)

 [Anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md)

 [Validierung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md)

 [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)

 [Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)

 [Grundlegendes zum DSL-Code](../modeling/understanding-the-dsl-code.md)

 [Anpassen von Dateispeicher und XML-Serialisierung](../modeling/customizing-file-storage-and-xml-serialization.md)

 [Bereitstellen von domänenspezifischen Sprachlösungen](../modeling/deploying-domain-specific-language-solutions.md)

 [Erstellen einer Windows Forms-basierten domänenspezifischen Sprache](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

 [Erstellen einer WPF-basierten domänenspezifischen Sprache](../modeling/creating-a-wpf-based-domain-specific-language.md)

 [Vorgehensweise: Erweitern des DSL-Designers](../modeling/how-to-extend-the-domain-specific-language-designer.md)

 [Unterstützte Visual Studio-Versionen für das Visualisierungs- und Modellierungs-SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)

 [Vorgehensweise: Migrieren einer domänenspezifischen Sprache zu einer neuen Version](../modeling/how-to-migrate-a-domain-specific-language-to-a-new-version.md)

 [API-Referenz für Modellierungs-SDK für Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
