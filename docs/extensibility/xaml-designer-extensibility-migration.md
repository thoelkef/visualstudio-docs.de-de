---
title: Migration der XAML-Designer Erweiterbarkeit
ms.date: 07/09/2019
ms.topic: conceptual
author: lutzroeder
ms.author: lutzr
manager: jillfra
dev_langs:
- csharp
- vb
monikerRange: vs-2019
ms.openlocfilehash: 9f5085c7a655f186c3c8a4a6eecada8b440650cd
ms.sourcegitcommit: 528178a304e66c0cb7ab98b493fe3c409f87493a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273220"
---
# <a name="xaml-designer-extensibility-migration"></a>Migration des XAML-Designer-Erweiterbarkeit

In Visual Studio 2019 unterstützt der XAML-Designer zwei verschiedene Architekturen: die Designer Isolations Architektur und die aktuellere Architektur der Oberflächen Isolation. Dieser Architektur Übergang ist erforderlich, um Ziel Laufzeiten zu unterstützen, die nicht in einem .NET Framework Prozess gehostet werden können. Durch die Umstellung auf die Architektur der Oberflächen Isolation werden wichtige Änderungen am Erweiterbarkeits Modell von Drittanbietern eingeführt. In diesem Artikel werden diese Änderungen beschrieben, die in Visual Studio 2019 ab Version 16,3 verfügbar sind.

Die **Designer Isolation** wird vom WPF-Designer für Projekte verwendet, die auf .NET Framework abzielen und *. Design. dll* -Erweiterungen unterstützt. Benutzercode, Steuerelement Bibliotheken und Erweiterungen von Drittanbietern werden in einem externen Prozess (*xdesproc. exe*) zusammen mit dem eigentlichen Designer Code und Designer-Panels geladen.

Die **Oberflächen Isolation** wird vom UWP-Designer verwendet. Sie wird auch vom WPF-Designer für Projekte verwendet, die auf .net Core abzielen. Bei der Oberflächen Isolation werden nur Benutzercode und Steuerelement Bibliotheken in einem separaten Prozess geladen, während der Designer und seine Panels in den Visual Studio-Prozess ("*devenv. exe*") geladen werden. Die Laufzeit, die zum Ausführen von Benutzercode und Steuerelement Bibliotheken verwendet wird, unterscheidet sich von der-.NET Framework für den eigentlichen Designer und Erweiterbarkeits Code von Drittanbietern.

![Erweiterbarkeit-Migration-Architektur](media/xaml-designer-extensibility-migration-architecture.png)

Aufgrund dieses Architektur Übergangs werden Erweiterungen von Drittanbietern nicht mehr in denselben Prozess geladen wie die Steuerelement Bibliotheken von Drittanbietern. Die Erweiterungen können nicht mehr direkte Abhängigkeiten von Steuerelement Bibliotheken aufweisen oder direkt auf Lauf Zeit Objekte zugreifen. Erweiterungen, die zuvor für die Designer Isolations Architektur mithilfe der *Microsoft. Windows. Extensibility. dll* -API geschrieben wurden, müssen zu einem neuen Ansatz migriert werden, um mit der Architektur der Oberflächen Isolation arbeiten zu können. In der Praxis muss eine vorhandene Erweiterung für neue Erweiterbarkeits-API-Assemblys kompiliert werden. Der Zugriff auf Lauf Zeit Steuerelement Typen über [typeof](/dotnet/csharp/language-reference/keywords/typeof) -oder Lauf Zeit Instanzen muss ersetzt oder entfernt werden, da Steuerelement Bibliotheken nun in einem anderen Prozess geladen werden.

## <a name="new-extensibility-api-assemblies"></a>Neue Erweiterbarkeits-API-Assemblys

Die neuen Erweiterbarkeits-API-Assemblys ähneln den vorhandenen Erweiterbarkeits-API-Assemblys, befolgen aber ein anderes Benennungs Schema, um Sie zu unterscheiden. Entsprechend wurden die Namen der Namespaces geändert, um die neuen Assemblynamen widerzuspiegeln.

| Designer Isolation-API-Assembly            | API-Assembly der Oberflächen Isolation                       |
|:------------------------------------------ |:---------------------------------------------------- |
| Microsoft.Windows.Design.Extensibility.dll | Microsoft.VisualStudio.DesignTools.Extensibility.dll |
| Microsoft.Windows.Design.Interaction.dll   | Microsoft.VisualStudio.DesignTools.Interaction.dll   |

## <a name="new-file-extension-and-discovery"></a>Neue Dateierweiterung und-Ermittlung

Anstatt die Dateierweiterung *. Design. dll* zu verwenden, werden neue Oberflächen Erweiterungen mithilfe der Dateierweiterung *. Designtools. dll* ermittelt. die Erweiterungen " *. Design. dll* " und " *. Designtools. dll* " können im gleichen *Entwurfs* Unterordner vorhanden sein.

Während Steuerelement Bibliotheken von Drittanbietern für die tatsächliche Ziel Laufzeit (.net Core oder UWP) kompiliert werden, sollte die Erweiterung *. Designtools. dll* immer als .NET Framework Assembly kompiliert werden.

## <a name="decouple-attribute-tables-from-run-time-types"></a>Entkoppeln von Attribut Tabellen von Lauf Zeit Typen

Das Erweiterbarkeits Modell der Oberflächen Isolation lässt nicht zu, dass Erweiterungen von tatsächlichen Steuerelement Bibliotheken abhängen. Daher können Erweiterungen nicht auf Typen aus der Steuerelement Bibliothek verweisen. Beispielsweise sollte *MyLibrary. Designtools. dll* keine Abhängigkeit von *MyLibrary. dll*aufweisen.

Solche Abhängigkeiten waren am häufigsten beim Registrieren von Metadaten für Typen über Attribut Tabellen. Erweiterungs Code, der auf Steuerelement Bibliothekstypen direkt über [typeof](/dotnet/csharp/language-reference/keywords/typeof) oder [GetType](/dotnet/visual-basic/language-reference/operators/gettype-operator) verweist, ersetzt die neuen APIs mithilfe von Zeichen folgen basierten Typnamen:

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Metadata;
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

[assembly: ProvideMetadata(typeof(AttributeTableProvider))]

public class AttributeTableProvider : IProvideAttributeTable
{
  public AttributeTable AttributeTable
  {
    get
    {
      var builder = new AttributeTableBuilder();
      builder.AddCustomAttributes("MyLibrary.MyControl", new DescriptionAttribute(Strings.MyControlDescription);
      builder.AddCustomAttributes("MyLibrary.MyControl", new FeatureAttribute(typeof(MyControlDefaultInitializer));
      return builder.CreateTable();
    }
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Metadata
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

<Assembly: ProvideMetadata(GetType(AttributeTableProvider))>

Public Class AttributeTableProvider
    Implements IProvideAttributeTable

    Public ReadOnly Property AttributeTable As AttributeTable Implements IProvideAttributeTable.AttributeTable
        Get
            Dim builder As New AttributeTableBuilder
            builder.AddCustomAttributes("MyLibrary.MyControl", New DescriptionAttribute(Strings.MyControlDescription))
            builder.AddCustomAttributes("MyLibrary.MyControl", New FeatureAttribute(GetType(MyControlDefaultInitializer)))
            Return builder.CreateTable()
        End Get
    End Property
End Class
```

## <a name="feature-providers-and-model-api"></a>Funktions Anbieter und Modell-API

Funktions Anbieter werden in Erweiterungsassemblys implementiert und in den Visual Studio-Prozess geladen. `FeatureAttribute`wird weiterhin direkt mithilfe [von typeof](/dotnet/csharp/language-reference/keywords/typeof)auf Funktions Anbieter Typen verweisen.

Derzeit werden die folgenden Funktions Anbieter unterstützt:

* `DefaultInitializer`
* `AdornerProvider`
* `ContextMenuProvider`
* `ParentAdapter`
* `PlacementAdapter`
* `DesignModeValueProvider`wird mit der Einschränkung unterstützt `TranslatePropertyValue` , die über `InvalidateProperty` oder bei Änderung im Designer aufgerufen wird. Sie wird nicht aufgerufen, wenn Sie im Lauf Zeit Code geändert wird.

Da Funktions Anbieter nun in einem Prozess geladen werden, der sich von dem tatsächlichen Lauf Zeit Code und den Steuerelement Bibliotheken unterscheidet, können Sie nicht mehr direkt auf Lauf Zeit Objekte zugreifen. Stattdessen müssen alle diese Interaktionen konvertiert werden, um die entsprechenden modellbasierten APIs zu verwenden. Die Modell-API wurde aktualisiert, und der Zugriff <xref:System.Type> auf <xref:System.Object> oder ist entweder nicht mehr verfügbar `TypeIdentifier` oder wurde durch und `TypeDefinition`ersetzt.

`TypeIdentifier`stellt eine Zeichenfolge ohne Assemblynamen dar, der einen Typ identifiziert. Eine `TypeIdenfifier` kann in eine `TypeDefinition` aufgelöst werden, um zusätzliche Informationen über den Typ abzufragen. `TypeDefinition`-Instanzen können nicht im Erweiterungs Code zwischengespeichert werden.

```csharp
TypeDefinition type = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("MyLibrary.MyControl"));
TypeDefinition buttonType = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("System.Windows.Controls.Button"));
if (type?.IsSubclassOf(buttonType) == true)
{
}
```

```vb
Dim type As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("MyLibrary.MyControl"))
Dim buttonType As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("System.Windows.Controls.Button"))
If type?.IsSubclassOf(buttonType) Then

End If
```

Aus dem Erweiterbarkeits-API-Satz der Oberflächen Isolation entfernte APIs:

* `ModelFactory.CreateItem(EditingContext context, object item)`
* `ViewItem.PlatformObject`
* `ModelProperty.DefaultValue`
* `AssemblyReferences.GetTypes(Type baseType)`

APIs, die `TypeIdentifier` anstelle von <xref:System.Type>verwenden:

* `ModelFactory.CreateItem(EditingContext context, Type itemType, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, Type itemType, CreateOptions options, params object[] arguments)`
* `ModelFactory.CreateStaticMemberItem(EditingContext context, Type type, string memberName)`
* `ModelFactory.ResolveType(EditingContext context, Type)` wurde in `MetadataFactory.ResolveType(EditingContext context, TypeIdentifier typeIdentifier)` geändert
* `ModelService.ResolveType(TypeIdentifier typeIdentifier)` wurde in `MetadataService.ResolveType(TypeIdentifier typeIdentifier)` geändert
* `ViewItem.ItemType`
* `ModelEvent.EventType`
* `ModelEvent.IsEventOfType(Type type)`
* `ModeItem.IsItemOfType(Type type)`
* `ModelParent.CanParent(EditingContext context, ModelItem parent, Type childType)`
* `ModelParent.FindParent(EditingContext context, Type childType, ModelItem startingItem)`
* `ModelParent.FindParent(Type childType, GestureData gestureData)`
* `ModelProperty.IsPropertyOfType(Type type)`
* `ParentAdpater.CanParent(ModelItem parent, Type childType)`
* `ParentAdapter.RedirectParent(ModelItem parent, Type childType)`

APIs, die `TypeIdentifier` anstelle von <xref:System.Type> verwenden und keine Konstruktorargumente mehr unterstützen:

* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, CreateOptions options, params object[] arguments)`

APIs, die `TypeDefinition` anstelle von <xref:System.Type>verwenden:

* `ValueTranslationService.GetProperties(Type itemType)`
* `ValueTranslationService.HasValueTranslation(Type itemType, PropertyIdentifier identifier)`
* `ValueTranslationService.TranslatePropertyValue(Type itemType, ModelItem item, PropertyIdentifier identifier, object value)`
* `ModelService.Find(ModelItem startingItem, Type type)`
* `ModelService.Find(ModelItem startingItem, Predicate<Type> match)`
* `ModelItem.ItemType`
* `ModelProperty.AttachedOwnerType`
* `ModelProperty.PropertyType`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type)`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type, Predicate<Type> match)`
* `FeatureManager.InitializeFeatures(Type type)`
* `FeatureManager.GetCustomAttributes(Type type, Type attributeType)`
* `AdapterService.GetAdapter<TAdapterType>(Type itemType)`
* `AdapterService.GetAdapter(Type adapterType, Type itemType)`
* `PropertyEntry.PropertyType`

APIs, die `AssemblyIdentifier` anstelle von `<xref:System.Reflection.AssemblyName?displayProperty=fullName>`verwenden:

* `AssemblyReferences.ReferencedAssemblies`
* `AssemblyReferences.LocalAssemblyName` wurde in `AssemblyReferences.LocalAssemblyIdentifier` geändert

Darüber hinaus unterstützen `SetValue` APIswienurInstanzenprimitiverTypenoderintegrierter.NETFrameworkTypen,diefürdieZielLaufzeitkonvertiertwerdenkönnen.`ModelItem` Derzeit werden diese Typen unterstützt:

* Primitive .NET Framework Typen: `Boolean`, `Byte`, `Char`, `DateTime`, `Double`, ,`Enum` ,`Int16`, ,`Int64`,, `Int32` `Guid` `Nullable` `SByte` , `Single`, `String`, `Type`, `UInt16`, `UInt32`, `UInt64`,`Uri`
* Bekannte WPF-.NET Framework Typen (und abgeleitete Typen `Brush`) `Color`: `CompositeTransform`, `CornerRadius`, `Duration`, `EasingFunctionBase`, `EasingMode`, `EllipseGeometry`, `FontFamily`, `GeneralTransform`, `Geometry` ,, , `GradientStopCollection`, `GradientStop`, `GridLength`, `ImageSource`, `InlineCollection`, `Inline`, `KeySpline`, `Material`, `Matrix`, `PathFigureCollection`, `PathFigure`, `PathSegmentCollection`, `PathSegment`, `Path`, `PointCollection`, `Point`, `PropertyPath`, `Rect`, `RepeatBehavior`, `Setter`, `Size`, `StaticResource`, `TextAlignment`, `TextDecorationCollection`, `ThemeResourceExtension`, `Thickness`, `TimeSpan`, `Transform3D`,`TransformCollection`

Beispiel:

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

public class MyControlDefaultInitializer : DefaultInitializer
{
  public override void InitializeDefaults(ModelItem item)
  {
    item.Properties["Width"].SetValue(800d);
    base.InitializeDefaults(item);
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

Public Class MyControlDefaultInitializer
    Inherits DefaultInitializer

    Public Overrides Sub InitializeDefaults(item As ModelItem)
        item.Properties!Width.SetValue(800.0)
        MyBase.InitializeDefaults(item)
    End Sub
End Class
```

Weitere Codebeispiele sind im Repository " [XAML-Designer-Extensibility-Samples](https://github.com/microsoft/xaml-designer-extensibility-samples) " verfügbar.

## <a name="limited-support-for-designdll-extensions"></a>Eingeschränkte Unterstützung für. Design. dll-Erweiterungen

Wenn eine " *. Designtools. dll* "-Erweiterung für eine Steuerelement Bibliothek erkannt wird, wird Sie zuerst geladen, und die Ermittlung für " *. Design. dll* "-Erweiterungen wird übersprungen.

Wenn keine *. Designtools. dll* -Erweiterungen vorhanden sind, aber die Erweiterung " *. Design. dll* " gefunden wird, versucht der XAML-Sprachdienst, diese Assembly zu laden, um die Attribut Tabellen Informationen zu extrahieren, um grundlegende Editor-und eigenschaftsinspektorszenarios Dieser Mechanismus ist im Gültigkeitsbereich begrenzt. Das Laden von Designer Isolations Erweiterungen zum Ausführen von Featureanbietern ist nicht zulässig, kann jedoch grundlegende Unterstützung für vorhandene WPF-Steuerelement Bibliotheken bieten.
