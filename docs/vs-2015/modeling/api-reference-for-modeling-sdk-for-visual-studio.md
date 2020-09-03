---
title: API-Referenz für das Modellierungs-SDK
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 65f8703597d6297afde6e2685594784fdd1d755c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672843"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>API-Referenz für Modellierungs-SDK für Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Visual Studio-SDK für Visualisierung und Modellierung bietet die Plattform, auf der die domänenspezifischen Sprachen (DSL) und die UML-Tools erstellt werden.

> [!NOTE]
> Weitere Informationen zur UML-Modellierungs-API finden Sie unter [API-Referenz für die Erweiterbarkeit von UML-Modellen](../modeling/api-reference-for-uml-modeling-extensibility.md). Informationen zur Text Transformation finden Sie unter [Anpassen der T4-Text Transformation](../modeling/customizing-t4-text-transformation.md).

 Dieser Abschnitt enthält Referenzmaterial für Namespaces, deren Namen mit "Microsoft. VisualStudio. Modeling" beginnen.

|Namespace|Inhalt|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Klassen wie ModelElement, das die Basisklasse aller Domänen Klassen ist, die Sie in einer DSL definieren.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Klassen, die einen Teil einer DSL-Definition bilden.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Die Tools für den Modell Speicher-Viewer und die Leistungsmessung.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Klassen wie shapeelement, die die Basisklasse aller Formen sind, die Sie in einer DSL definieren.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Gesten-und Auswahlmethoden.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|Die API des DSL-Definitions-Designers.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Interne Klassen des DSL-Definitions-Designers.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Attribute, die es Ihnen ermöglichen, den DSL-Designer mit Befehlen, Gesten und Validierung zu erweitern.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Erweiterungs Methoden für ModelElement, die DSL-Erweiterbarkeit implementieren.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Erweiterbarkeits Attribute|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Ermöglicht es Ihnen, Teile eines Modells als schreibgeschützt zu gestalten.|
|[Microsoft. VisualStudio. Modeling. Integration](/previous-versions/ee904412(v=vs.140))|Die ModelBus-API, mit der Sie unterschiedliche Modelle integrieren können.|
|[Microsoft. VisualStudio. Modeling. Integration. Picker](/previous-versions/ee904394(v=vs.140))|Das Dialogfeld, in dem Benutzer zu Modellen und Elementen navigieren können, um ModelBus-Verweise zu erstellen.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|Der Auswahl Dienst.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell](/previous-versions/ee869435(v=vs.140))|ModelBus-Adapter Framework für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|
|[Microsoft. VisualStudio. Modeling. Integration. Shell. Picker](/previous-versions/ee886769(v=vs.140))|Das Auswahl Dialogfeld, in dem Benutzer zu Modellen und Elementen navigieren können, um ModelBus-Verweise zu erstellen.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Die Schnittstelle zwischen DSLs und [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Ermöglicht das Definieren von Kontextmenü Befehlen (Kontextmenü).|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Ermöglicht das Definieren von Validierungs Einschränkungen.|

## <a name="see-also"></a>Siehe auch

- [API-Referenz für UML-Modellierungserweiterbarkeit](../modeling/api-reference-for-uml-modeling-extensibility.md)
- [Anpassen der T4-Texttransformation](../modeling/customizing-t4-text-transformation.md)
