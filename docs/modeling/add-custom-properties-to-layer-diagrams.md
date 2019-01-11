---
title: Hinzufügen benutzerdefinierter Eigenschaften zu Abhängigkeitsdiagrammen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 407db46519872d8f1c4e6eba79ddd5ca84610d70
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892237"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Hinzufügen benutzerdefinierter Eigenschaften zu Abhängigkeitsdiagrammen

Wenn Sie Erweiterungscode für Abhängigkeitsdiagramme schreiben, können Sie Werte mit jedem Element in einem Abhängigkeitsdiagramm speichern. Die Werte bleiben erhalten, wenn das Diagramm gespeichert und erneut geöffnet wird. Ferner können Sie diese Eigenschaften werden in der **Eigenschaften** Fenster, damit Benutzer anzeigen und bearbeiten können. Beispielsweise können Sie Benutzer für jede Ebene einen regulären Ausdruck angeben lassen und Validierungscode schreiben, um sicherzustellen, dass die Namen der Klassen in jeder Ebene dem Muster entsprechen, das vom Benutzer angegeben wird.

## <a name="non-visible-properties"></a>Nicht sichtbare Eigenschaften

Wenn Sie lediglich Ihren Code können Sie jedes Element in einem Abhängigkeitsdiagramm Werte zuordnen möchten, müssen Sie keine MEF-Komponente zu definieren. Es gibt ein Wörterbuch namens `Properties` in <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>. Fügen Sie einfach Werte zum Wörterbuch jedes Ebenenelements hinzu, die gemarshallt werden können. Sie werden als Teil des Diagramms Abhängigkeit gespeichert werden. Weitere Informationen finden Sie unter [Navigieren zu und Update layer-Modellen im Programmcode](../modeling/navigate-and-update-layer-models-in-program-code.md).

## <a name="editable-properties"></a>Bearbeitbaren Eigenschaften

**Erste Vorbereitung**

> [!IMPORTANT]
> Um Eigenschaften anzuzeigen, stellen Sie die folgende Änderung auf jedem Computer, in dem Ebeneneigenschaften sichtbar sein soll:
>
> 1. Führen Sie mithilfe von Editor **als Administrator ausführen**. Open *%ProgramFiles%\Microsoft Visual Studio [Version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest*.
> 2. In der **Content** Element hinzufügen:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
> 3. Unter den **Visual Studio-Tools** Abschnitt der Visual Studio-Anwendung im Startmenü öffnen **Developer-Eingabeaufforderung**. Geben Sie Folgendes ein:
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Starten Sie Visual Studio neu.

**Stellen Sie sicher, dass Ihr Code in einem VSIX-Projekt ist.**

Wenn die Eigenschaft Teil eines Befehls, Geste oder überprüfungsprojekt ist, müssen Sie nichts hinzufügen. Der Code für die benutzerdefinierte Eigenschaft sollte in einem Visual Studio-Erweiterungsprojekt definiert werden, das als MEF-Komponente definiert wird. Weitere Informationen finden Sie unter [Hinzufügen von Befehlen und Gesten zu Abhängigkeitsdiagrammen](../modeling/add-commands-and-gestures-to-layer-diagrams.md) oder [Hinzufügen einer benutzerdefinierten architekturvalidierung zu Abhängigkeitsdiagrammen](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

**Definieren der benutzerdefinierten Eigenschaft**

Um eine benutzerdefinierte Eigenschaft zu erstellen, definieren Sie eine Klasse folgendermaßen:

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

Sie können Eigenschaften für <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> oder eine der abgeleiteten Klassen definieren, darunter folgende:

-   `ILayerModel` - das Modell

-   `ILayer` - jede Ebene

-   `ILayerDependencyLink` - die Links zwischen Ebenen

-   `ILayerComment`

-   `ILayerCommentLink`

## <a name="example"></a>Beispiel

Der folgende Code entspricht einem typischen benutzerdefinierten Eigenschaftendeskriptor. Er definiert eine boolesche Eigenschaft für das Ebenenmodell (`ILayerModel`), mit dem der Benutzer Werte für eine benutzerdefinierte Validierungsmethode bereitstellen kann.

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;

namespace MyNamespace
{
  /// <summary>
  /// Custom properties are added to the Layer Designer via a custom
  /// Property Descriptor. We have to export this Property Descriptor
  /// using MEF to make it available in the Layer Designer.
  /// </summary>
  [Export(typeof(IPropertyExtension))]
  public class AllTypesMustBeReferencedProperty
      : PropertyExtension<ILayerModel>
  {
    /// <summary>
    /// Each custom property must have a unique name.
    /// Usually we use the full name of this class.
    /// </summary>
    public static readonly string FullName =
      typeof(AllTypesMustBeReferencedProperty).FullName;

    /// <summary>
    /// Construct the property. Notice the use of FullName.
    /// </summary>
    public AllTypesMustBeReferencedProperty()
            : base(FullName)
    {  }

    /// <summary>
    /// The display name is shown in the Properties window.
    /// We therefore use a localizable resource.
    /// </summary>
    public override string DisplayName
    {
      get { return Strings.AllTypesMustBeReferencedDisplayName; }
    }

    /// <summary>
    /// Description shown at the bottom of the Properties window.
    /// We use a resource string for easier localization.
    /// </summary>
    public override string Description
    {
      get { return Strings.AllTypesMustBeReferencedDescription; }
    }

    /// <summary>
    /// This is called to set a new value for this property. We must
    /// throw an exception if the value is invalid.
    /// </summary>
    /// <param name="component">The target ILayerElement</param>
    /// <param name="value">The new value</param>
    public override void SetValue(object component, object value)
    {
      ValidateValue(value);
      base.SetValue(component, value);
    }
    /// <summary>
    /// Helper to validate the value.
    /// </summary>
    /// <param name="value">The value to validate</param>
    private static void ValidateValue(object value)
    {  }

    public override Type PropertyType
    { get { return typeof(bool); } }

    /// <summary>
    /// The segment label of the properties window.
    /// </summary>
    public override string Category
    {
      get
      {
        return Strings.AllTypesMustBeReferencedCategory;
      }
    }
  }
}
```

## <a name="see-also"></a>Siehe auch

- [Erweitern von Abhängigkeitsdiagrammen](../modeling/extend-layer-diagrams.md)
