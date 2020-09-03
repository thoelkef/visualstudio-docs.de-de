---
title: Hinzufügen benutzerdefinierter Eigenschaften zu ebenendiagrammen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom properties
ms.assetid: 52b3ac25-d10b-4507-a1fe-209ccb4d2777
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ec1c7c94c8a0e6aa233cf21f9b57e093cc430d48
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655285"
---
# <a name="add-custom-properties-to-layer-diagrams"></a>Hinzufügen benutzerdefinierter Eigenschaften zu Ebenendiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Erweiterungscode für Ebenendiagramme schreiben, können Sie Werte mit jedem Element auf einem Ebenendiagramm speichern. Die Werte bleiben erhalten, wenn das Diagramm gespeichert und erneut geöffnet wird. Diese Eigenschaften können auch im **Eigenschaften** Fenster angezeigt werden, damit Sie von Benutzern angezeigt und bearbeitet werden können. Beispielsweise können Sie Benutzer für jede Ebene einen regulären Ausdruck angeben lassen und Validierungscode schreiben, um sicherzustellen, dass die Namen der Klassen in jeder Ebene dem Muster entsprechen, das vom Benutzer angegeben wird.

## <a name="properties-not-visible-to-the-user"></a>Für den Benutzer nicht sichtbare Eigenschaften
 Wenn durch den Code nur Werte an ein Element in einem Ebenendiagramm angefügt werden sollen, müssen Sie keine MEF-Komponente definieren. Es ist ein Wörterbuch `Properties` mit dem Namen in [ilayerelement](/previous-versions/ff644511(v=vs.140))vorhanden. Fügen Sie einfach Werte zum Wörterbuch jedes Ebenenelements hinzu, die gemarshallt werden können. Sie werden als Teil des Ebenendiagramms gespeichert. Weitere Informationen finden Sie unter [Navigieren in und Aktualisieren von ebenenmodellen im Programmcode](../modeling/navigate-and-update-layer-models-in-program-code.md).

## <a name="properties-that-the-user-can-edit"></a>Eigenschaften, die der Benutzer bearbeiten kann
 **Erste Vorbereitung**

> [!IMPORTANT]
> Um Eigenschaften anzuzeigen, müssen Sie die folgende Änderung auf jedem Computer vornehmen, in dem Ebeneneigenschaften sichtbar sein sollen.
>
>  1. Führen Sie Notepad mithilfe von **als Administrator ausführen**aus. Öffnen Sie `%ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest`.
>
>  2. Fügen Sie innerhalb des `Content`-Elements Folgendes hinzu:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
>  3. Öffnen Sie im **Visual Studio-Tools** Abschnitt des Visual Studio-Anwendungs Startmenüs **Developer-Eingabeaufforderung**.
>
>     Eingeben:
>
>     `devenv /rootSuffix /updateConfiguration`
>
>     `devenv /rootSuffix Exp /updateConfiguration`
>
>  4. Starten Sie Visual Studio neu.

 **Stellen Sie sicher, dass sich der Code in einem VSIX-Projekt befindet**

 Wenn die Eigenschaft Teil eines Befehls-, Gesten- oder Validierungsprojekts ist, müssen Sie nichts hinzufügen. Der Code für die benutzerdefinierte Eigenschaft sollte in einem Visual Studio-Erweiterungsprojekt definiert werden, das als MEF-Komponente definiert wird. Weitere Informationen finden Sie unter [Hinzufügen von Befehlen und Gesten zu ebenendiagrammen](../modeling/add-commands-and-gestures-to-layer-diagrams.md) oder [Hinzufügen einer benutzerdefinierten Architektur Validierung zu ebenendiagrammen](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

 **Definieren der benutzerdefinierten Eigenschaft**

 Um eine benutzerdefinierte Eigenschaft zu erstellen, definieren Sie eine Klasse folgendermaßen:

```
[Export(typeof(IPropertyExtension))]
public class MyProperty
      : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

 Sie können Eigenschaften für [ilayerelement](/previous-versions/ff644511(v=vs.140)) oder eine der abgeleiteten Klassen definieren, die Folgendes umfassen:

- `ILayerModel` -das Modell

- `ILayer` -jede Ebene

- `ILayerDependencyLink` - die Links zwischen Ebenen

- `ILayerComment`

- `ILayerCommentLink`

## <a name="example"></a>Beispiel
 Der folgende Code entspricht einem typischen benutzerdefinierten Eigenschaftendeskriptor. Er definiert eine boolesche Eigenschaft für das Ebenenmodell (`ILayerModel`), mit dem der Benutzer Werte für eine benutzerdefinierte Validierungsmethode bereitstellen kann.

```
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

## <a name="see-also"></a>Weitere Informationen
 [Erweitern von Ebenendiagrammen](../modeling/extend-layer-diagrams.md)
