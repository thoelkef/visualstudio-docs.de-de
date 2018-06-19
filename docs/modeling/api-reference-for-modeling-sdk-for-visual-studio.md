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
ms.openlocfilehash: 7db208bf19f0a2433d4c85af7710a0f5ac70562e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947858"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>API-Referenz für Modellierungs-SDK für Visual Studio

Die Visual Studio Visualization and Modeling SDK bietet die Plattform, auf denen Ihre Standardtools für domänenspezifische Sprachen (DSL) erstellt werden.

Dieser Abschnitt enthält Referenzmaterial für Namespaces, deren Namen mit "Microsoft.VisualStudio.Modeling" beginnen.

|Namespace|Inhalt|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Klassen, z. B. Modellelement, die die Basisklasse aller Klassen der Domäne ist, die Sie in eine DSL definieren.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Klassen, die Teil der DSL-Definition zu bilden.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Die Modell-Speicher-Viewer und die Leistung Messung Tools.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Klassen, z. B. ShapeElement, also die Basisklasse für alle Formen, die Sie in eine DSL definieren.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Auswahl und Gestenhandler-Methoden.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|Die API des Designers DSL-Definition.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Interne Klassen des Designers DSL-Definition.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Attribute, die Ihnen das Erweitern der DSL-Designer mit Befehlen, Gesten und Validierung zu ermöglichen.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Erweiterungsmethoden für das Modellelement, die DSL-Erweiterbarkeit implementieren.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Erweiterbarkeit-Attribute|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Sie können Teile eines Modells schreibgeschützt machen.|
|<xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName>|Die Modelbus-API, die Sie die hilft integrieren verschiedene Modelle.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName>|Das Dialogfeld, in dem Benutzer, die Modelle und Elemente zum Erstellen von Modelbus Verweise wechseln kann.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName>|Der Datumsauswahl-Dienst.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName>|ModelBus Adapterframework für Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName>|Der Vererbungsauswahl (Dialogfeld), die Benutzer Navigieren auf Modelle und Elemente Modelbus Verweise erstellen können.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Die Schnittstelle zwischen konzentriert und Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Können Sie Befehle im Kontextmenü (Kontext) zu definieren.|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Sie können validierungseinschränkungen definieren.|

## <a name="see-also"></a>Siehe auch

- [Anpassen der T4-Texttransformation](../modeling/customizing-t4-text-transformation.md)
