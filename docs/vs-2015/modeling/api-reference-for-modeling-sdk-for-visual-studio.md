---
title: API-Referenz für Modellierungs-SDK
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6a290227b120958b5bb3407393dcff33b247b20d
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68872019"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>API-Referenz für Modellierungs-SDK für Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Visual Studio-SDK für Visualisierung und Modellierung bietet die Plattform, auf der die domänenspezifischen Sprachen (DSL) und die UML-Tools erstellt werden.

> [!NOTE]
> Weitere Informationen zur UML-Modellierungs-API finden Sie unter [API-Referenz für die Erweiterbarkeit von UML-Modellen](../modeling/api-reference-for-uml-modeling-extensibility.md). Informationen zur Text Transformation finden Sie unter [Anpassen der T4-Text Transformation](../modeling/customizing-t4-text-transformation.md).

 Dieser Abschnitt enthält Referenzmaterial für Namespaces, deren Namen mit "Microsoft.VisualStudio.Modeling" beginnen.

|Namespace|Content|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Klassen wie z. B. ModelElement, die die Basisklasse aller Domänenklassen ist, die Sie in einer DSL zu definieren.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Klassen, die Teil einer DSL-Definition an.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Das Modell Store Viewer und die Leistung Messtools.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Klassen wie z. B. von ShapeElement, die die Basisklasse aller Formen ist, die Sie in einer DSL zu definieren.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Gesten und Auswahl von Methoden.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|Die API des DSL-Definition-Designers.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Interne Klassen-Designer die DSL-Definition.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Attribute, die es Ihnen ermöglichen, den DSL-Designer mit Befehlen, Gesten und Validierung zu erweitern.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Erweiterungsmethoden für ModelElement, die DSL-Erweiterbarkeit implementieren.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Erweiterbarkeit Attribute|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Können Sie die Teile eines Modells Schreibschutz zu versehen.|
|[Microsoft. VisualStudio. Modeling. Integration](/previous-versions/ee904412(v=vs.140))|Die Modelbus-API, wodurch Sie integrieren Sie verschiedene Modelle.|
|[Microsoft. VisualStudio. Modeling. Integration. Picker](/previous-versions/ee904394(v=vs.140))|Das Dialogfeld, in dem Benutzer für Modelle und Elemente zur Erstellung von Modelbus-Verweise navigieren kann.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|Der Auswahl-Dienst.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell](/previous-versions/ee869435(v=vs.140))|ModelBus-Adapter Framework [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]für.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell. Picker](/previous-versions/ee886769(v=vs.140))|Das Dialogfeld "Auswahl" ermöglicht, die Benutzern, die für Modelle und Elemente zur Erstellung von Modelbus-Verweise zu navigieren.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Die Schnittstelle zwischen DSLs [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]und.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Können Sie Befehle im Kontextmenü (Kontext) zu definieren.|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Können Sie validierungseinschränkungen definieren.|

## <a name="see-also"></a>Siehe auch

- [API-Referenz für UML-Modellierungserweiterbarkeit](../modeling/api-reference-for-uml-modeling-extensibility.md)
- [Anpassen der T4-Texttransformation](../modeling/customizing-t4-text-transformation.md)
