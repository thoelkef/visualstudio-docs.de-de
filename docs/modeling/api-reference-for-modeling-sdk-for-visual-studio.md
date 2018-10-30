---
title: API-Referenz für Modellierungs-SDK für Visual Studio
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 21da4ff34c26d28944af5edcb14e40b2db0d94d7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896965"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>API-Referenz für Modellierungs-SDK für Visual Studio

Die Visual Studio-Visualisierungs und Modellierungs-SDK bietet die Plattform, auf dem die Tools für domänenspezifische Sprachen (DSL) erstellt werden.

Dieser Abschnitt enthält Referenzmaterial für Namespaces, deren Namen mit "Microsoft.VisualStudio.Modeling" beginnen.

|Namespace|Inhalt|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Klassen wie z. B. ModelElement, die die Basisklasse aller Domänenklassen ist, die Sie in einer DSL zu definieren.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Klassen, die Teil einer DSL-Definition an.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Das Modell Store Viewer und die Leistung Messtools.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Klassen wie z. B. von ShapeElement, die die Basisklasse aller Formen ist, die Sie in einer DSL zu definieren.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Gesten und Auswahl von Methoden.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|Die API des DSL-Definition-Designers.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Interne Klassen-Designer die DSL-Definition.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Attribute, mit die Sie die DSL-Designer mit Befehlen, Gesten und Validierung erweitern können.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Erweiterungsmethoden für ModelElement, die DSL-Erweiterbarkeit implementieren.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Erweiterbarkeit Attribute|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Können Sie die Teile eines Modells Schreibschutz zu versehen.|
|<xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName>|Die Modelbus-API, wodurch Sie integrieren Sie verschiedene Modelle.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName>|Das Dialogfeld, in dem Benutzer für Modelle und Elemente zur Erstellung von Modelbus-Verweise navigieren kann.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName>|Der Auswahl-Dienst.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName>|ModelBus-Adapter-Framework für Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName>|Das Dialogfeld "Auswahl" ermöglicht, die Benutzern, die für Modelle und Elemente zur Erstellung von Modelbus-Verweise zu navigieren.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Die Schnittstelle zwischen DSLs und Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Können Sie Befehle im Kontextmenü (Kontext) zu definieren.|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Können Sie validierungseinschränkungen definieren.|

## <a name="see-also"></a>Siehe auch

- [Anpassen der T4-Texttransformation](../modeling/customizing-t4-text-transformation.md)
