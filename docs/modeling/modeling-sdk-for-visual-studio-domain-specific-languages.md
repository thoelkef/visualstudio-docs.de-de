---
title: "Modeling SDK für Visual Studio - domänenspezifische Sprachen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
ms.assetid: 17a531e2-1964-4a9d-84fd-6fb1b4aee662
caps.latest.revision: "77"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 4bc85e0b5d03af1a34676030144f36457c1366ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Modellierungs-SDK für Visual Studio - Domänenspezifische Sprachen
Mithilfe der Modellierungs-SDK für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], können Sie leistungsstarke modellbasierten Entwicklungstools, die Sie in integrieren können erstellen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Auf diese Weise können Sie eine oder mehrere Modelldefinitionen erstellen und diese in einen Toolsatz integrieren.  
  
 Im Mittelpunkt von MSDK befindet sich die Definition eines Modells, das Sie erstellen, um Konzepte in Ihrem Geschäftsbereich darzustellen. Sie können das Modell mit einer Vielzahl von Tools umgeben, z. B. mit einer Diagrammansicht, der Möglichkeit zur Generierung von Code und anderen Artefakten, Befehlen zum Transformieren des Modells und der Möglichkeit zur Interaktion mit Code und anderen Objekten in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Während Sie das Modell entwickelt, können Sie es mit anderen Modellen und Tools kombinieren, um ein leistungsstarkes Toolset zu erstellen, das auf ihre Entwicklung ausgerichtet ist.  
  
 Mit MSDK können Sie ein Modell schnell in Form einer domänenspezifischen Sprache (DSL) entwickeln. Sie beginnen, indem Sie einen spezialisierten Editor verwenden, um ein Schema oder eine abstrakte Syntax zusammen mit einer grafischen Schreibweise zu definieren. Aus dieser Definition generiert VMSDK Folgendes:  
  
-   Eine Implementierung des Modells mithilfe einer stark typisierten API, die in einem transaktionsbasierten Speicher ausgeführt wird.  
  
-   Ein strukturbasierter Explorer.  
  
-   Ein grafischer Editor, in dem Benutzer das Modell bzw. Teile davon, die Sie definieren, anzeigen können.  
  
-   Serialisierungsmethoden, mit denen die Modelle in lesbarem XML gespeichert werden.  
  
-   Funktionen zum Generieren des Programmcodes und anderer Artefakte mithilfe von Textvorlagen.  
  
 Sie können alle diese Funktionen anpassen und erweitern. Ihre Erweiterungen sind so integriert, dass Sie noch die DSL-Definition aktualisieren und Funktionen erneut generieren können, ohne die Erweiterungen zu verlieren.  
  
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 
 [Verwandte Blogbeiträge](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
  
 Um Hilfe bei der erweiterten Techniken und Problembehandlung, besuchen Sie [Visual Studio DSL & Modeling Tools Extensibility Forum](http://go.microsoft.com/fwlink/?LinkID=186074).  
  
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
  
 [Gewusst wie: Erweitern des DSL-Designers](../modeling/how-to-extend-the-domain-specific-language-designer.md)  
  
 [Unterstützte Visual Studio-Versionen für das Visualisierungs- und Modellierungs-SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)  
  
 [Gewusst wie: Migrieren einer domänenspezifischen Sprache zu einer neuen Version](../modeling/how-to-migrate-a-domain-specific-language-to-a-new-version.md)  
  
 [API-Referenz für Modellierungs-SDK für Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
