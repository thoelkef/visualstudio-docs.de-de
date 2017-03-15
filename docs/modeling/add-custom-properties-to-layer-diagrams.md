---
title: "Hinzufügen benutzerdefinierter Eigenschaften zu Abhängigkeitsdiagramme | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, adding custom properties
ms.assetid: 52b3ac25-d10b-4507-a1fe-209ccb4d2777
caps.latest.revision: 21
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 6c7e43c180ac5210d9c29961ed7330b370a99075
ms.lasthandoff: 02/22/2017

---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Fügen Sie benutzerdefinierter Eigenschaften zu Abhängigkeitsdiagramme hinzu
Wenn Sie Erweiterungscode für Abhängigkeitsdiagramme schreiben, können Sie Werte mit jedem Element in einem Abhängigkeitsdiagramm speichern. Die Werte bleiben erhalten, wenn das Diagramm gespeichert und erneut geöffnet wird. Sie können auch diese Eigenschaften in angezeigt werden sollen die **Eigenschaften** Fenster, damit Benutzer anzeigen und bearbeiten können. Beispielsweise können Sie Benutzer für jede Ebene einen regulären Ausdruck angeben lassen und Überprüfungscode schreiben, um sicherzustellen, dass die Namen der Klassen in jeder Ebene dem Muster entsprechen, das vom Benutzer angegeben wird.  
  
## <a name="properties-not-visible-to-the-user"></a>Für den Benutzer nicht sichtbare Eigenschaften  
 Wenn Sie nur Code, um Werte an ein Element in einem Abhängigkeitsdiagramm angefügt werden sollen, müssen Sie eine MEF-Komponente definieren. Es gibt ein Wörterbuch mit dem Namen `Properties` <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> Fügen Sie einfach Werte zum Wörterbuch jedes Ebenenelements hinzu, die gemarshallt werden können. Sie werden als Teil des Diagramms Abhängigkeit gespeichert werden. Weitere Informationen finden Sie unter [navigieren und Update layer-Modellen im Programmcode](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
## <a name="properties-that-the-user-can-edit"></a>Eigenschaften, die der Benutzer bearbeiten kann  
 **Erste Vorbereitung**  
  
> [!IMPORTANT]
>  Um Eigenschaften anzuzeigen, müssen Sie die folgende Änderung auf jedem Computer vornehmen, in dem Ebeneneigenschaften sichtbar sein sollen.  
>   
>  1.  Führen Sie mithilfe von Editor **als Administrator ausführen**. Öffnen Sie `%ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest`.  
> 2.  Fügen Sie innerhalb des `Content`-Elements Folgendes hinzu:  
>   
>     ```xml  
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>  
>     ```  
> 3.  Klicken Sie unter der **Visual Studio-Tools** Abschnitt der Visual Studio-Anwendung im Startmenü öffnen **Entwicklereingabeaufforderung**.  
>   
>      Geben Sie Folgendes ein:  
>   
>      `devenv /rootSuffix /updateConfiguration`  
>   
>      `devenv /rootSuffix Exp /updateConfiguration`  
> 4.  Starten Sie Visual Studio neu.  
  
 **Stellen Sie sicher, dass Ihr Code in einem VSIX-Projekt**  
  
 Wenn die Eigenschaft Teil eines Befehls-, Gesten- oder Validierungsprojekts ist, müssen Sie nichts hinzufügen. Der Code für die benutzerdefinierte Eigenschaft sollte in einem Visual Studio-Erweiterungsprojekt definiert werden, das als MEF-Komponente definiert wird. Weitere Informationen finden Sie unter [Hinzufügen von Befehlen und Gesten, Abhängigkeitsdiagramme](../modeling/add-commands-and-gestures-to-layer-diagrams.md) oder [Hinzufügen von benutzerdefinierten architekturüberprüfung zu Abhängigkeit Diagrammen](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).  
  
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
  
 Sie können die Eigenschaften definieren, auf <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>oder eine der davon abgeleiteten Klassen, darunter:</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>  
  
-   `ILayerModel` - das Modell  
  
-   `ILayer` - jede Ebene  
  
-   `ILayerDependencyLink` - die Links zwischen Ebenen  
  
-   `ILayerComment`  
  
-   `ILayerCommentLink`  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern Sie Abhängigkeitsdiagramme](../modeling/extend-layer-diagrams.md)

