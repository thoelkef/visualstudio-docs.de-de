---
title: Migration von XAML-Designer-Erweiterbarkeit
ms.date: 07/09/2019
ms.topic: conceptual
author: lutzroeder
ms.author: lutzr
manager: jillfra
dev_langs:
- csharp
- vb
monikerRange: vs-2019
ms.openlocfilehash: 52bc8a6a0097d255891f4b6111a27bff85091bec
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67784475"
---
# <a name="xaml-designer-extensibility-migration"></a>Migration von XAML-Designer-Erweiterbarkeit

Ab Visual Studio 2019 Version 16.1 als öffentliche Vorschau der XAML-Designer unterstützt zwei verschiedene Architekturen: die Architektur des Designers Isolation und die neuere Oberfläche Isolation-Architektur. Dieser Übergang Architektur ist zur Unterstützung von Ziel-Laufzeiten, die nicht gehostet werden können in einem .NET Framework-Prozess erforderlich. Umstellung auf die Entwurfsoberfläche Isolation Architektur enthält grundlegende Änderungen für das Drittanbieter-Erweiterbarkeitsmodell. In diesem Artikel werden die Änderungen erläutert.

**Designer Isolation** wird von der WPF-Designer für Projekte, die .NET Framework als Ziel verwendet und unterstützt *. design.dll* Erweiterungen. Benutzercode, Steuerelementbibliotheken und Drittanbieter-Erweiterungen werden in einem externen Prozess geladen (*XDesProc.exe*) zusammen mit den tatsächlichen Designer-Code und die Designer-Bereichen.

**Isolation Oberfläche** wird von der UWP-Designer verwendet. Es wird auch von der WPF-Designer für Projekte verwendet, die auf .NET Core abzielen. Oberfläche isoliert werden nur der Benutzer Code und Bibliotheken in einem separaten Prozess geladen, während der Designer und ihre Bereiche in der Visual Studio-Prozess geladen werden (*DevEnv.exe*). Die Laufzeit zum Ausführen von Code und benutzerbibliotheken unterscheidet sich von, die von .NET Framework für den tatsächlichen Designer und die von Drittanbieter-Erweiterbarkeitscode verwendet.

![extensibility-migration-architecture](media/xaml-designer-extensibility-migration-architecture.png)

Aufgrund dieser Neuerung Architektur werden die Erweiterungen von Drittanbietern in demselben Prozess wie die Bibliotheken der Drittanbieter-Steuerelement nicht mehr geladen. Die Erweiterungen können nicht mehr haben direkte Abhängigkeiten von Steuerelementbibliotheken oder direkt zugreifen auf Laufzeitobjekte. Erweiterungen, die für den Designer Isolation-Architektur mit geschrieben wurden die *Microsoft.Windows.Extensibility.dll* API muss migriert werden, um einen neuen Ansatz für die Arbeit mit der Oberfläche Isolation-Architektur. In der Praxis müssen eine vorhandene Erweiterung für neue Erweiterbarkeit-API-Assemblys kompiliert werden. Zugriff auf Steuerelement der Common Language Runtime-Typen über [Typeof](/dotnet/csharp/language-reference/keywords/typeof) oder Laufzeitinstanzen müssen ersetzt oder entfernt werden, da Steuerelementbibliotheken jetzt in einem anderen Prozess geladen werden.

## <a name="new-extensibility-api-assemblies"></a>Neue Erweiterbarkeits-API-Assemblys

Die neue erweiterbarkeitsassemblys-API die vorhandene API erweiterbarkeitsassemblys ähneln, aber führen Sie ein anderes Schema für die Benennungsstandards um unterscheiden. Auf ähnliche Weise Sprachschnittstellenpakete die Namespacenamen entsprechend die neuen Assemblynamen.

| Designer-Isolation-API-assembly            | API-Oberfläche Isolation-assembly                       |
|:------------------------------------------ |:---------------------------------------------------- |
| Microsoft.Windows.Design.Extensibility.dll | Microsoft.VisualStudio.DesignTools.Extensibility.dll |
| Microsoft.Windows.Design.Interaction.dll   | Microsoft.VisualStudio.DesignTools.Interaction.dll   |

## <a name="new-file-extension-and-discovery"></a>Neue Dateierweiterung und Ermittlung

Anstatt die *. design.dll* Dateierweiterung, neue Oberfläche, die Erweiterungen werden mithilfe von ermittelt die *. designtools.dll* Dateierweiterung. *. design.dll* und *. designtools.dll* Erweiterungen können vorhanden sein, in der gleichen *Entwurf* Unterordner.

Während die Bibliotheken der Drittanbieter-Steuerelement für die tatsächliche Ziellaufzeit (.NET Core oder UWP) kompiliert sind die *. designtools.dll* Erweiterung immer als .NET Framework-Assembly kompiliert werden soll.

## <a name="decouple-attribute-tables-from-runtime-types"></a>Entkoppeln von Attributtabellen aus der Runtime-Typen

Das Erweiterbarkeitsmodell Oberfläche Isolation Erweiterungen hängt von tatsächlichen Steuerelementbibliotheken kann nicht aus, und aus diesem Grund können keine Erweiterungen Typen verweisen, aus der Steuerelementbibliothek. Z. B. *MyLibrary.designtools.dll* sollte keine Abhängigkeit auf *MyLibrary.dll*.

Solche Abhängigkeiten wurden am häufigsten verwendeten, beim Registrieren von Metadaten für Typen über die Attributtabellen. Erweiterungscode, der Steuerelementbibliothek verweist auf Typen direkt per [Typeof](/dotnet/csharp/language-reference/keywords/typeof) ([GetType](/dotnet/visual-basic/language-reference/operators/gettype-operator) in Visual Basic), die in die neuen APIs mit zeichenfolgenbasierten Typnamen ersetzt wird:

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
      AttributeTableBuilder builder = new AttributeTableBuilder();
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

## <a name="feature-providers-and-model-api"></a>Funktionsanbieter und Objektmodell-API

Featureanbieter werden in Assemblys implementiert und in den Visual Studio-Prozess geladen. `FeatureAttribute` Anbieter Funktionstypen, die direkt mit verweisen weiterhin auf [Typeof](/dotnet/csharp/language-reference/keywords/typeof).

Da Featureanbieter jetzt in einem Prozess, der sich von den tatsächlichen Code und Laufzeitbibliotheken geladen werden, sind sie nicht mehr auf Laufzeitobjekte direkt zugreifen können. Stattdessen müssen alle Interaktionen zwischen konvertiert werden, um die entsprechenden modellbasierten-APIs zu verwenden. Der Modell-API wurde aktualisiert, und Zugriff auf <xref:System.Type> oder <xref:System.Object> ist entweder nicht mehr verfügbar oder wurde ersetzt mit `TypeIdentifier` und `TypeDefinition`.

`TypeIdentifier` Stellt eine Zeichenfolge ohne den Namen einer Assembly Identifizieren eines Typs dar. Ein `TypeIdenfifier` zu aufgelöst werden kann eine `TypeDefinition` zur Abfrage von zusätzlichen Informationen über den Typ. `TypeDefinition` Instanzen können nicht im Erweiterungscode zwischengespeichert werden.

```csharp
TypeDefinition type = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("MyLibrary.MyControl"));
TypeDefinition buttonType = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("System.Windows.Controls.Button"));
if (type != null && buttonType != type.IsSubclassOf(buttonType))
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

APIs, die aus der Entwurfsoberfläche Isolation-Erweiterbarkeits-API-Gruppe entfernt werden:

* `ModelFactory.CreateItem(EditingContext context, object item)`
* `ViewItem.PlatformObject`
* `ModelProperty.DefaultValue`

APIs, mit denen `TypeIdentifier` anstelle von <xref:System.Type>:

* `ModelFactory.CreateItem(EditingContext context, Type itemType, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, Type itemType, CreateOptions options, params object[] arguments)`
* `ModelFactory.CreateStaticMemberItem(EditingContext context, Type type, string memberName)`
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

APIs, mit denen `TypeIdentifier` anstelle von <xref:System.Type> und unterstützen Sie nicht mehr Konstruktorargumente:

* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, CreateOptions options, params object[] arguments)`

APIs, mit denen `TypeDefinition` anstelle von <xref:System.Type>:

* `ModelFactory.ResolveType(EditingContext context, TypeIdentifier typeIdentifier)`
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

APIs, mit denen `ModelItem` anstelle von <xref:System.Object>:

* `ModelItemCollection.Insert(int index, object value)`
* `ModelItemCollection.Remove(object value)`
* `ModelItemDictionary.Add(object key, object value)`
* `ModelItemDictionary.ContainsKey(object key)`
* `ModelItemDictionary.Remove(object key)`
* `ModelItemDictionary.TryGetValue(object key, out ModelItem value)`

Bezeichnet die primitive Typen wie `Int32`, `String`, oder `Thickness` der Modell-API als .NET Framework-Instanzen übergeben werden kann und wird mit dem entsprechenden Objekt im Zielprozess Laufzeit konvertiert werden. Beispiel:

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

## <a name="limited-support-for-designdll-extensions"></a>Eingeschränkte Unterstützung für. design.dll-Erweiterungen

Wenn alle *. designtools.dll* Erweiterung für eine Steuerelementbibliothek entdeckt wird, ist es geladen wird, erste und die Ermittlung für *. design.dll* Erweiterungen wird übersprungen.

Wenn kein *. designtools.dll* Erweiterungen vorhanden sind, aber eine *. design.dll* Erweiterung gefunden wird, wird der XAML-Sprachdienst versucht wird, zum Laden dieser Assembly zum Extrahieren der Attribut-Tabelle-Informationen zur Unterstützung Basic-Editors und Eigenschaft Inspector-Szenarien. Dieser Mechanismus wird im Bereich beschränkt. Es kann nicht beim Laden des Designers Isolation-Erweiterungen für die Ausführung von Featureanbieter jedoch gewährleistet grundlegenden Unterstützung für vorhandene WPF-Steuerelement-Bibliotheken.
