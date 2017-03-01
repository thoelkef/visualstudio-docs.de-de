---
title: "Hinzufügen einer Nachverfolgungseigenschaft zu einer domänenspezifischen Sprachdefinition | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: 4aa47777-de75-4897-a423-a3c4426b4125
caps.latest.revision: 22
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
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
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: 0d97770109a3c362f99a014829e694fc2e027196
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-tracking-property-to-a-domain-specific-language-definition"></a>Hinzufügen einer Nachverfolgungseigenschaft zu einer domänenspezifischen Sprachdefinition
In dieser exemplarischen Vorgehensweise wird das Hinzufügen einer Nachverfolgungseigenschaft zu einem Domänenmodell veranschaulicht.  
  
 Ein *tracking Domäne* -Eigenschaft ist eine Eigenschaft, die vom Benutzer aktualisiert werden, jedoch die hat eines Standardwert, der mit den Werten anderer Eigenschaften oder Elemente berechnet wird.  
  
 In die domänenspezifische Sprachtools (DSL-Tools), den Anzeigenamen einer Domänenklasse Eigenschaft einen Standardwert, der berechnet wird besitzt, mit dem Namen der Domänenklasse, aber ein Benutzer beispielsweise ändern Sie den Wert zur Entwurfszeit oder auf den berechneten Wert zurückgesetzt.  
  
 In dieser exemplarischen Vorgehensweise erstellen Sie eine domänenspezifische Sprache (DSL), die einen Namespace tracking-Eigenschaft, die einen Standardwert basierend auf der Standard-Namespace-Eigenschaft des Modells hat. Weitere Informationen zur Überwachung der Eigenschaften finden Sie unter [Tracking Eigenschaften](http://msdn.microsoft.com/en-us/0538b0e4-6221-4e7d-911a-b92cd622f0be).  
  
-   Die DSL-Tools-Unterstützung Eigenschaftendeskriptoren nachverfolgen. Allerdings kann nicht der DSL-Designer zum Hinzufügen einer Nachverfolgungseigenschaft zu einer Sprache verwendet werden. Aus diesem Grund müssen Sie benutzerdefinierten Code zum Definieren und implementieren die Tracking-Eigenschaft hinzufügen.  
  
 Eine Tracking-Eigenschaft verfügt über zwei Zustände: Tracking und vom Benutzer aktualisiert. Überwachungseigenschaften weisen die folgenden Features:  
  
-   In der Überwachungsdatenbank Zustand wird der Wert der Eigenschaft Überwachung wird berechnet, und der Wert wird aktualisiert, wie andere Eigenschaften im Modell ändern.  
  
-   Wenn in der aktualisierten von Benutzerstatus, behält der Wert der Tracking-Eigenschaft den Wert, der der Benutzer zuletzt die Eigenschaft festlegen.  
  
-   In der **Eigenschaften** Fenster der **zurücksetzen** Befehl für die Tracking-Eigenschaft wird nur aktiviert, wenn die Eigenschaft in der aktualisierten ist von den Benutzerzustand. Die **zurücksetzen** Befehl setzt die Tracking-Eigenschaft Status auf Überwachung.  
  
-   In der **Eigenschaften** -Fenster, die Tracking-Eigenschaft wird in den Status nachverfolgen, seinen Wert in ein normaler Schrift angezeigt.  
  
-   In der **Eigenschaften** Fenster, wenn die Tracking-Eigenschaft in der aktualisierten ist vom Status des Benutzers, ihr Wert fett formatiert angezeigt wird.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Bevor Sie in dieser exemplarischen Vorgehensweise beginnen können, müssen Sie zunächst diese Komponenten installieren:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
## <a name="creating-the-dsl-project"></a>DSL-Projekt erstellen  
 Erstellen Sie das Projekt für Ihre einer domänenspezifischen Sprache.  
  
#### <a name="to-create-the-project"></a>So erstellen Sie das Projekt  
  
1.  Erstellen einer domänenspezifischen Sprachdesigner-Projekt. Nennen Sie es `TrackingPropertyDSL`.  
  
2.  In der **domänenspezifischen Sprachdesigner-Assistenten**, die folgenden Optionen festlegen:  
  
    1.  Wählen Sie die **MinimalLanguage** Vorlage.  
  
    2.  Verwenden Sie den Standardnamen für die domänenspezifischen Sprache `TrackingPropertyDSL`.  
  
    3.  Legen Sie die Erweiterung für die Modelldateien zu `trackingPropertyDsl`.  
  
    4.  Verwenden Sie das Standardsymbol für die Vorlage für die Model-Dateien.  
  
    5.  Legen Sie den Namen des Produkts für `Product Name`.  
  
    6.  Legen Sie den Namen des Unternehmens zu `Company Name`.  
  
    7.  Verwenden Sie den Standardwert für den Stammnamespace für Projekte in der Projektmappe `CompanyName.ProductName.TrackingPropertyDSL`.  
  
    8.  Lassen Sie den Assistenten zum Erstellen einer Schlüsseldatei mit starkem Namen für Ihre Assemblys.  
  
    9. Überprüfen Sie die Details der Lösung, und klicken Sie dann auf **Fertig stellen** zum Erstellen des Projekts der DSL-Definition.  
  
## <a name="customizing-the-default-dsl-definition"></a>Anpassen der Standard-DSL-Definition  
 In diesem Abschnitt passen Sie die DSL-Definition, um die folgenden Elemente enthalten:  
  
-   Ein Namespace tracking-Eigenschaft für jedes Element des Modells.  
  
-   Eine boolesche IsNamespaceTracking-Eigenschaft für jedes Element des Modells. Diese Eigenschaft wird anzugeben, ob die Tracking-Eigenschaft im Überwachungsprofil oder in der aktualisierten von Benutzerstatus.  
  
-   Eine Standard-Namespace-Eigenschaft für das Modell. Diese Eigenschaft wird zum Berechnen des Standardwert der Eigenschaft Namespace verwendet werden.  
  
-   Eine berechnete CustomElements-Eigenschaft für das Modell. Diese Eigenschaft wird den Anteil der Elemente angeben, die einen benutzerdefinierten Namespace aufweisen.  
  
#### <a name="to-add-the-domain-properties"></a>Hinzufügen von Domäneneigenschaften  
  
1.  Im DSL-Designer mit der rechten Maustaste die **ExampleModel** Domänenklasse, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **DomainProperty**.  
  
    1.  Nennen Sie die neue Eigenschaft `DefaultNamespace`.  
  
    2.  In der **Eigenschaften** Fenster für die neue Eigenschaft, **Standardwert** auf `DefaultNamespace`, und legen Sie **Typ** auf **Zeichenfolge**.  
  
2.  Um die **ExampleModel** Domäne-Klasse verwenden, fügen Sie eine Domäneneigenschaft namens `CustomElements`.  
  
     In der **Eigenschaften** Fenster für die neue Eigenschaft **Art** auf **berechnete**.  
  
3.  Um die **ExampleElement** Domäne-Klasse verwenden, fügen Sie eine Domäneneigenschaft namens `Namespace`.  
  
     In der **Eigenschaften** Fenster für die neue Eigenschaft, **kann durchsucht werden** auf **False**, und legen Sie **Art** auf **"CustomStorage"**.  
  
4.  Um die **ExampleElement** Domäne-Klasse verwenden, fügen Sie eine Domäneneigenschaft namens `IsNamespaceTracking`.  
  
     In der **Eigenschaften** für die neue Eigenschaft, legen **kann durchsucht werden** zu **False**legen **Standardwert** auf `true`, und legen Sie **Typ** auf **booleschen**.  
  
#### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Aktualisieren der Diagrammelemente und DSL-details  
  
1.  Im DSL-Designer mit der rechten Maustaste die **ExampleShape** Geometrie-Form, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Text-Decorator**.  
  
    1.  Nennen Sie den neuen Text-Decorator `NamespaceDecorator`.  
  
    2.  In der **Eigenschaften** legen die Text-Decorator **Position** auf **InnerBottomLeft**.  
  
2.  Wählen Sie im DSL-Designer die Verbindungslinie der **ExampleElement** Klasse, um die **ExampleShape** Form.  
  
    1.  In der **DSL-Details** wählen Sie im Fenster der **Decorator-Zuordnungen** Registerkarte.  
  
    2.  In der **Decorators** wählen **NamespaceDecorator**, aktivieren Sie das Kontrollkästchen, und klicken Sie dann auf die **Anzeigeeigenschaft** wählen **Namespace**.  
  
3.  In **DSL-Explorer**, erweitern Sie die **Domänenklassen** Ordner mit der rechten Maustaste die **ExampleElement** Knoten, und klicken Sie dann auf **neue Domänentypdeskriptor hinzufügen**.  
  
    1.  Erweitern Sie die **ExampleElement** Knoten, und wählen Sie die **benutzerdefinierten Typdeskriptor (Domänentypdeskriptor)** Knoten.  
  
    2.  In der **Eigenschaften** legen den domänentypdeskriptor **benutzerdefinierte codierten** auf **True**.  
  
4.  In **DSL-Explorer**, wählen die **XML-Serialisierungsverhalten** Knoten.  
  
    1.  In der **Eigenschaften** legen **benutzerdefinierte Post Load** auf **True**.  
  
## <a name="transforming-templates"></a>Transformieren von Vorlagen  
 Nun, dass Sie die Domänenklassen und Eigenschaften für Ihre DSL definiert haben, können Sie überprüfen, ob die DSL-Definition ordnungsgemäß transformiert werden kann, um den Code für das Projekt erneut zu generieren.  
  
#### <a name="to-transform-the-text-templates"></a>Transformieren von Textvorlagen  
  
1.  Auf der **Projektmappen-Explorer** -Symbolleiste klicken Sie auf **alle Vorlagen transformieren**.  
  
2.  Das System generiert den Code für die Projektmappe neu, und speichert "DslDefinition.DSL". Informationen über das XML-Format von Berichtsdefinitionsdateien finden Sie unter [der DslDefinition.dsl-Datei](../modeling/the-dsldefinition-dsl-file.md).  
  
## <a name="creating-files-for-custom-code"></a>Erstellen von Dateien für benutzerdefinierten Code  
 Wenn Sie alle Vorlagen transformieren, generiert das System den Quellcode, der in den Projekten Dsl und DslPackage Ihrer domänenspezifischen Sprache definiert. Damit Sie dem generierten Text behindert vermeiden können, Schreiben Sie Ihren benutzerdefinierten Code in Dateien, die von den generierten Codedateien unterscheiden.  
  
 Sie müssen den Code bereitstellen, für die Verwaltung der Wert und der Status der Tracking-Eigenschaft. Können Sie Ihren benutzerdefinierten Code aus dem generierten Code zu unterscheiden, und Datei Namenskonflikte zu vermeiden, stellen Sie Ihre benutzerdefinierten Code-Dateien in einem separaten Unterordner.  
  
#### <a name="to-create-the-code-files"></a>Um die Codedateien zu erstellen  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **DSL** Projekt, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **neuen Ordner**. Nennen Sie den neuen Ordner `CustomCode`.  
  
2.  Mit der rechten Maustaste die neue **CustomCode** Ordner, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **neues Element**.  
  
3.  Wählen Sie die **Codedatei** Vorlagensatz, der **Namen** auf `NamespaceTrackingProperty.cs`, und klicken Sie dann auf **OK**.  
  
     Die NamespaceTrackingProperty.cs-Datei wird erstellt und zur Bearbeitung geöffnet.  
  
4.  Erstellen Sie im Ordner die folgenden Dateien: `ExampleModel.cs,``HelperClasses.cs`, `Serialization.cs`, und `TypeDescriptor.cs`.  
  
5.  In der **DslPackage** Projekt, erstellen Sie auch eine `CustomCode` Ordner und Hinzufügen einer `Package.cs` Codedatei.  
  
## <a name="adding-helper-classes-to-support-tracking-properties"></a>Hinzufügen von Hilfsklassen zur Unterstützung von Überwachungseigenschaften  
 Die Datei HelperClasses.cs Hinzufügen der `TrackingHelper` und `CriticalException` Klassen wie folgt. Sie können diese Klassen weiter unten in dieser exemplarischen Vorgehensweise verweisen.  
  
#### <a name="to-add-the-helper-classes"></a>Hinzufügen von Hilfsklassen  
  
1.  Fügen Sie den folgenden Code in die Datei HelperClasses.cs.  
  
    ```c#  
    using System;  
    using System.Collections;  
    using System.Diagnostics;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        internal static class TrackingHelper  
        {  
            /// <summary>Notify each model element in a collection that a tracked  
            /// property has changed.</summary>  
            /// <param name="store">The store for the model.</param>  
            /// <param name="collection">The collection of model elements that  
            /// contain the tracking property.</param>  
            /// <param name="propertyId">The ID of the tracking property.</param>  
            /// <param name="trackingPropertyId">The ID of the property that  
            /// indicates whether the tracking property is tracking.</param>  
            internal static void UpdateTrackingCollectionProperty(  
                Store store,  
                IEnumerable collection,  
                Guid propertyId,  
                Guid trackingPropertyId)  
            {  
                DomainPropertyInfo propInfo =  
                    store.DomainDataDirectory.GetDomainProperty(propertyId);  
  
                DomainPropertyInfo trackingPropInfo =  
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);  
  
                Debug.Assert(propInfo != null);  
                Debug.Assert(trackingPropInfo != null);  
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),  
                    "Tracking property not specified as a boolean");  
  
                foreach (ModelElement element in collection)  
                {  
                    // If the tracking property is currently tracking, then notify  
                    // it that the tracked property has changed.  
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);  
                    if (isTracking)  
                    {  
                        propInfo.NotifyValueChange(element);  
                    }  
                }  
            }  
        }  
  
        /// <summary>Helper class to flag critical exceptions from ones that are  
        /// safe to ignore.</summary>  
        internal static class CriticalException  
        {  
            /// <summary>Gets whether an exception is critical and can not be  
            /// ignored.</summary>  
            /// <param name="ex">The exception to check.</param>  
            /// <returns>True if the exception is critical.</returns>  
            internal static bool IsCriticalException(Exception ex)  
            {  
                if (ex is NullReferenceException  
                    || ex is StackOverflowException  
                    || ex is OutOfMemoryException  
                    || ex is System.Threading.ThreadAbortException)  
                    return true;  
  
                if (ex.InnerException != null)  
                    return IsCriticalException(ex.InnerException);  
  
                return false;  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-custom-type-descriptor"></a>Hinzufügen von benutzerdefiniertem Code für den benutzerdefinierten Typdeskriptor  
 Implementieren der `GetCustomProperties` Methode für den Typdeskriptor für die `ExampleModel` Domain-Klasse.  
  
> [!NOTE]
>  Der Code, der für den benutzerdefinierten Typdeskriptor für DSL-Tools generieren `ExampleModel` Aufrufe `GetCustomProperties`, aber die DSL-Tools werden nicht generiert Code, der die Methode implementiert.  
  
 Definieren diese Methode erstellt die Verfolgung Eigenschaftendeskriptor für die Eigenschaft Namespace. Darüber hinaus kann Attribute für den Tracking-Eigenschaft liefert die **Eigenschaften** Eigenschaft ordnungsgemäß angezeigt werden soll.  
  
#### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>So ändern Sie den Typdeskriptor für die Domänenklasse ExampleModel  
  
1.  Fügen Sie den folgenden Code in die Datei TypeDescriptor.cs.  
  
    ```c#  
    using System;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.Design;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // To the custom type descriptor for the ExampleElement domain class, add  
        // the GetCustomProperties method.  
        public partial class ExampleElementTypeDescriptor  
        {  
            /// <summary>Returns the property descriptors for the described  
            /// ExampleElement domain class.</summary>  
            /// <remarks>This method adds the tracking property descriptor.  
            /// </remarks>  
            private PropertyDescriptorCollection GetCustomProperties(  
                Attribute[] attributes)  
            {  
                // Get the default property descriptors from the base class  
                PropertyDescriptorCollection propertyDescriptors =  
                    base.GetProperties(attributes);  
  
                // Get a reference to the model element that is being described.  
                ExampleElement source = this.ModelElement as ExampleElement;  
  
                //Add the descriptor for the tracking property.  
                if (source != null)  
                {  
                    DomainPropertyInfo domainProperty =  
                        source.Store.DomainDataDirectory.GetDomainProperty(  
                            ExampleElement.NamespaceDomainPropertyId);  
  
                    DomainPropertyInfo trackingProperty =  
                        source.Store.DomainDataDirectory.GetDomainProperty(  
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);  
  
                    // Define attributes for the tracking property so that the  
                    // Properties window displays the property correctly.  
                    Attribute[] attr = new Attribute[] {  
                        new DisplayNameAttribute("Element Namespace"),  
                        new DescriptionAttribute("The namespace of the element."),  
                        new CategoryAttribute("Tracking Properties"),  
                    };  
  
                    propertyDescriptors.Add(new TrackingPropertyDescriptor(  
                        source, domainProperty, trackingProperty, attr));  
                }  
  
                // Return the property descriptors for this element  
                return propertyDescriptors;  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-package"></a>Hinzufügen von benutzerdefiniertem Code für das Paket  
 Der generierte Code definiert einen Typbeschreibungsanbieter für die Domänenklasse ExampleElement. Allerdings müssen Sie Code, um die DSL mit diesem Typbeschreibungsanbieter anweisen hinzufügen.  
  
#### <a name="to-update-the-dsl-package-to-use-your-custom-type-descriptor"></a>Aktualisieren Sie das DSL-Paket, um Ihre benutzerdefinierten Typdeskriptor verwenden  
  
1.  Fügen Sie den folgenden Code in die Datei Package.cs.  
  
    ```c#  
    using System.ComponentModel;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // Override the default Initialize method.  
        internal sealed partial class TrackingPropertyDSLPackage  
        {  
            protected override void Initialize()  
            {  
                // Add the custom type descriptor for the ExampleElement type.  
                TypeDescriptor.AddProvider(  
                    new ExampleElementTypeDescriptionProvider(),  
                    typeof(ExampleElement));  
  
                base.Initialize();  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-model"></a>Hinzufügen von benutzerdefiniertem Code für das Modell  
 Implementieren der `GetCustomElementsValue` Methode für die `ExampleModel` Domain-Klasse.  
  
> [!NOTE]
>  Der Code, der für die DSL-Tools generieren `ExampleModel` Aufrufe `GetCustomElementsValue`, aber die DSL-Tools werden nicht generiert Code, der die Methode implementiert.  
  
 Definieren der `GetCustomElementsValue` Methode stellt die Logik für die Eigenschaft CustomElements berechnet der `ExampleModel`. Diese Methode zählt die Anzahl der `ExampleElement` Domänenklassen, die über einen Namespace tracking-Eigenschaft, die einen Wert Benutzer aktualisiert und gibt eine Zeichenfolge, die diese Anzahl im Verhältnis zur Gesamtanzahl Elemente im Modell darstellt.  
  
 Fügen Sie außerdem eine `OnDefaultNamespaceChanged` Methode, um `ExampleModel`, und überschreiben die `OnValueChanged` Methode der `DefaultNamespacePropertyHandler` der geschachtelten Klasse des `ExampleModel` Aufrufen `OnDefaultNamespaceChanged`.  
  
 Da die DefaultNamespace-Eigenschaft verwendet wird, berechnet die Namespace-Eigenschaft, `ExampleModel` teilt alle `ExampleElement` Domänenklassen, die den Wert der DefaultNamespace geändert hat.  
  
#### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Den Handler für die überwachten Eigenschaft ändern.  
  
1.  Fügen Sie den folgenden Code in die Datei ExampleModel.cs.  
  
    ```c#  
    using System.Linq;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        public partial class ExampleModel  
        {  
            public string GetCustomElementsValue()  
            {  
                if (this.Elements.Count == 0) return "0/0";  
  
                int number = this.Elements.Count(e => !e.IsNamespaceTracking);  
                return string.Format("{0}/{1}", number, this.Elements.Count);  
            }  
  
            #region Value changed handler for the tracked property  
  
            // When a tracked property changes, it needs to notify all of the properties  
            // that track it.  
  
            /// <summary>Called by the DefaultNamespace property value handler when the  
            /// DefaultNamespace property changes.</summary>  
            /// <param name="oldValue">The previous value of the property.</param>  
            /// <param name="newValue">The new value of the property.</param>  
            protected virtual void OnDefaultNamespaceChanged(  
                string oldValue, string newValue)  
            {  
                // Use the helper class to notify all of the elements in the model  
                // that the default namespace has changed.  
                TrackingHelper.UpdateTrackingCollectionProperty(  
                    this.Store,  
                    this.Elements,  
                    ExampleElement.NamespaceDomainPropertyId,  
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);  
            }  
  
            // Update the change handler for the DefaultNamespace property.  
            internal sealed partial class DefaultNamespacePropertyHandler  
            {  
                /// <summary>Called when the DefaultNamespace property changes.</summary>  
                /// <param name="element">The model element that has the property that  
                /// changed.</param>  
                /// <param name="oldValue">The previous value of the property.</param>  
                /// <param name="newValue">The new value of the property.</param>  
                protected override void OnValueChanged(  
                    ExampleModel element, string oldValue, string newValue)  
                {  
                    base.OnValueChanged(element, oldValue, newValue);  
  
                    if (!element.Store.InUndoRedoOrRollback)  
                    {  
                        element.OnDefaultNamespaceChanged(oldValue, newValue);  
                    }  
                }  
            }  
  
            #endregion  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-tracking-property"></a>Hinzufügen von benutzerdefiniertem Code für die Tracking-Eigenschaft  
 Hinzufügen einer `CalculateNamespace` Methode, um die `ExampleElement` Domain-Klasse.  
  
 Diese Methode definieren, können Sie die Logik für die Eigenschaft CustomElements berechnet `ExampleModel`. Diese Methode zählt die Anzahl der `ExampleElement` Domänenklassen, die über eine Eigenschaft, die in der aktualisierten Namespace von Benutzerstatus aus, und gibt eine Zeichenfolge, die diese Anzahl im Verhältnis zur Gesamtanzahl Elemente im Modell darstellt.  
  
 Außerdem hinzufügen, Speicher und Methoden zum Abrufen und festlegen, die Eigenschaft Namespace benutzerdefinierten Speicher, der die `ExampleElement` Domain-Klasse.  
  
> [!NOTE]
>  Der Code, der für die DSL-Tools generieren `ExampleModel` Ruft die Get und set-Methoden, die DSL-Tools sind generiert jedoch keinen Code, der die Methoden implementiert.  
  
#### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Die Methode für den benutzerdefinierten Typdeskriptor hinzu  
  
1.  Fügen Sie den folgenden Code in die Datei NamespaceTrackingProperty.cs.  
  
    ```c#  
    using System;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // To the domain class that has the tracking property, add the caluclation  
        // for when the property is tracking.  
        public partial class ExampleElement  
        {  
            /// <summary>Calculates the actual value of the property when it is  
            /// tracking.</summary>  
            /// <returns>The value of the tracking property when it is  
            /// tracking.</returns>  
            /// <remarks>Making this method virtual allows child classes to modify  
            /// the calculation. This method does not need to perform validation, as  
            /// its caller handles validation prior to calling this method.  
            /// <para>In this case, the tracking value depends on the default namespace  
            /// property of the parent model.</para></remarks>  
            protected virtual string CalculateNamespace()  
            {  
                return this.ExampleModel.DefaultNamespace;  
            }  
  
            #region Tracking property implementation  
  
            // Implement the Namespace domain property of the ExampleElement domain class,  
            // and update the IsNamespaceTracking domain property value handler.  
  
            /// <summary>Storage for the Namespace property.</summary>  
            private string namespaceStorage;  
  
            /// <summary>Gets the value of the Namespace property.</summary>  
            /// <returns>The value of the Namespace property.</returns>  
            private string GetNamespaceValue()  
            {  
                // Only retrieve the tracked value if the store is not in the  
                // middle of a serialization transaction.  
                bool loading = this.Store.TransactionManager.InTransaction  
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;  
  
                if (!loading && this.IsNamespaceTracking)  
                {  
                    try  
                    {  
                        return this.CalculateNamespace();  
                    }  
                    catch (NullReferenceException)  
                    {  
                        return default(string);  
                    }  
                    catch (Exception e)  
                    {  
                        if (CriticalException.IsCriticalException(e))  
                        {  
                            throw;  
                        }  
                        else  
                        {  
                            return default(string);  
                        }  
                    }  
                }  
  
                return namespaceStorage;  
            }  
  
            /// <summary>Sets the value of the Namespace property.</summary>  
            /// <param name="value">The new value for the property.</param>  
            private void SetNamespaceValue(string value)  
            {  
                namespaceStorage = value;  
  
                // Only update the state of the tracking property if the store is  
                // not in the middle of a serialization transaction.  
                bool loading = this.Store.TransactionManager.InTransaction  
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;  
  
                if (!this.Store.InUndoRedoOrRollback && !loading)  
                {  
                    this.IsNamespaceTracking = false;  
                }  
            }  
  
            // Update the default behavior of the ExampleElement.IsNamespaceTracking  
            // domain property value handler.  
            internal sealed partial class IsNamespaceTrackingPropertyHandler  
            {  
                /// <summary>Called after the IsNamespaceTracking property changes.  
                /// </summary>  
                /// <param name="element">The model element that has the property  
                /// that changed.</param>  
                /// <param name="oldValue">The previous value of the property.  
                /// </param>  
                /// <param name="newValue">The new value of the property.</param>  
                protected override void OnValueChanged(  
                    ExampleElement element, Boolean oldValue, Boolean newValue)  
                {  
                    base.OnValueChanged(element, oldValue, newValue);  
                    if (!element.Store.InUndoRedoOrRollback && newValue)  
                    {  
                        DomainPropertyInfo propInfo =  
                            element.Store.DomainDataDirectory.GetDomainProperty(  
                                ExampleElement.NamespaceDomainPropertyId);  
                        propInfo.NotifyValueChange(element);  
                    }  
                }  
  
                /// <summary>Performs the reset operation for the IsNamespaceTracking  
                /// property for a model element.</summary>  
                /// <param name="element">The model element that has the property  
                /// to reset.</param>  
                internal void ResetValue(ExampleElement element)  
                {  
                    object calculatedValue = null;  
  
                    try  
                    {  
                        calculatedValue = element.CalculateNamespace();  
                    }  
                    catch (NullReferenceException)  
                    {  
                    }  
                    catch (System.Exception e)  
                    {  
                        if (CriticalException.IsCriticalException(e))  
                        {  
                            throw;  
                        }  
                    }  
  
                    if ((calculatedValue != null  
                        && object.Equals(element.Namespace, calculatedValue)))  
                    {  
                        element.isNamespaceTrackingPropertyStorage = true;  
                    }  
                }  
  
                /// <summary>Method to set IsNamespaceTracking to false so that this  
                /// instance of this tracking property is not storage-based.  
                /// </summary>  
                /// <param name="element">The element on which to reset the property  
                /// value.</param>  
                internal void PreResetValue(ExampleElement element)  
                {  
                    // Force the IsNamespaceTracking property to false so that the value  
                    // of the Namespace property is retrieved from storage.  
                    element.isNamespaceTrackingPropertyStorage = false;  
                }  
            }  
  
            #endregion  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-to-support-serialization"></a>Hinzufügen von benutzerdefiniertem Code zur Unterstützung der Serialisierung  
 Fügen Sie Code zur Unterstützung von benutzerdefinierten Verhaltens nach der Last für XML-Serialisierung.  
  
> [!NOTE]
>  Der Code, der DSL-Tools Aufrufe Generieren der `OnPostLoadModel` und `OnPostLoadModelAndDiagram` Methoden; der DSL-Tools sind generiert jedoch keinen Code, der diese Methoden implementiert.  
  
#### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Hinzufügen von Code zur Unterstützung von benutzerdefinierten Verhaltens nach der Auslastung  
  
1.  Fügen Sie den folgenden Code in die Datei Serialization.cs.  
  
    ```c#  
    using System;  
    using System.Diagnostics;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        #region Helper classes for maintaining state while the store is serializing.  
  
        public abstract partial class TrackingPropertyDSLSerializationHelperBase  
        {  
            /// <summary>Reset the tracking state properties to their natural values  
            /// based on comparing storage with calculation.</summary>  
            /// <param name="store">The store that contains this model.</param>  
            internal static void ResetTrackingProperties(Store store)  
            {  
                // Two passes required - one to set all elements to storage-based  
                // then another to set some back to being tracking.  
                foreach (ModelElement element in store.ElementDirectory.AllElements)  
                {  
                    ExampleElement myElementInstance = element as ExampleElement;  
                    if (myElementInstance != null)  
                    {  
                        myElementInstance.PreResetIsTrackingProperties();  
                        continue;  
                    }  
                }  
                foreach (ModelElement element in store.ElementDirectory.AllElements)  
                {  
                    ExampleElement myElementInstance = element as ExampleElement;  
                    if (myElementInstance != null)  
                    {  
                        myElementInstance.ResetIsTrackingProperties();  
                        continue;  
                    }  
                }  
            }  
        }  
  
        // Add the pre-reset and reset methods for the model element.  
        public partial class ExampleElement  
        {  
            /// <summary>Calls the pre-reset method on the associated property value  
            /// handler for each tracking property of this model element.</summary>  
            internal virtual void PreResetIsTrackingProperties()  
            {  
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);  
            }  
  
            /// <summary>Calls the reset method on the associated property value  
            /// handler for each tracking property of this model element.</summary>  
            internal virtual void ResetIsTrackingProperties()  
            {  
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);  
            }  
        }  
  
        #endregion  
  
        #region Custom serialization code  
  
        // To the serialization helper for the TrackingPropertyDSL class, add post  
        // load handlers to bind the tracking property to the serialization process.  
        // These handlers manage the tracking states and property values when the  
        // model is serialized and deserialized.  
        public partial class TrackingPropertyDSLSerializationHelperBase  
        {  
            /// <summary>Customize model loading.</summary>  
            /// <param name="serializationResult">The serialization result from the  
            /// load operation.</param>  
            /// <param name="partition">The partition in which the new  
            /// instance was created.</param>  
            /// <param name="fileName">The name of the file from which the  
            /// instance was deserialized.</param>  
            /// <param name="modelRoot">The root of the file that was loaded.  
            /// </param>  
            private void OnPostLoadModel(  
                SerializationResult serializationResult,  
                Partition partition,  
                string fileName,  
                ExampleModel modelRoot)  
            {  
            }  
  
            /// <summary>Customize model and diagram loading.</summary>  
            /// <param name="serializationResult">Stores serialization result from  
            /// the load operation.</param>  
            /// <param name="modelPartition">Partition in which the new  
            /// instance will be created.</param>  
            /// <param name="modelFileName">Name of the file from which the  
            /// instance will be deserialized.</param>  
            /// <param name="diagramPartition">Partition in which the new  
            /// diagram instance will be created.</param>  
            /// <param name="diagramFileName">Name of the file from which the  
            /// diagram instance will be deserialized.</param>  
            /// <param name="modelRoot">The root of the file that was loaded.</param>  
            /// <param name="diagram">The diagram matching the modelRoot.</param>  
            private void OnPostLoadModelAndDiagram(  
                SerializationResult serializationResult,  
                Partition modelPartition,  
                string modelFileName,  
                Partition diagramPartition,  
                string diagramFileName,  
                ExampleModel modelRoot,  
                TrackingPropertyDSLDiagram diagram)  
            {  
                Debug.Assert(modelPartition != null);  
                Debug.Assert(modelPartition.Store != null);  
  
                // Tracking properties need to be set up according to whether the  
                // serialization matches the calculated values.  
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(  
                    modelPartition.Store);  
            }  
        }  
  
        #endregion  
    }  
    ```  
  
## <a name="testing-the-language"></a>Testen die Sprache  
 Der nächste Schritt ist zum Erstellen und Ausführen des DSL-Designers in eine neue Instanz der [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , damit Sie überprüfen können, dass die Tracking-Eigenschaft ordnungsgemäß arbeitet.  
  
#### <a name="to-exercise-the-language"></a>Die Sprache ausüben.  
  
1.  Auf der **erstellen** Menü klicken Sie auf **Projektmappe neu erstellen**.  
  
2.  Auf der **Debuggen** Menü klicken Sie auf **Debuggen**.  
  
     Der Projektfunktion [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] öffnet die **Debuggen** Lösung, die eine leeren Test-Datei enthält.  
  
3.  In **Projektmappen-Explorer**, doppelklicken Sie auf die Datei Test.trackingPropertyDsl, um sie im Designer zu öffnen, und klicken Sie dann auf die Entwurfsoberfläche.  
  
     Beachten Sie, dass in der **Eigenschaften** Fenster für das Diagramm, das **Standard-Namespace** Eigenschaft ist **DefaultNamespace**, und die **benutzerdefinierte Elemente** Eigenschaft ist **0/0**.  
  
4.  Ziehen Sie ein **ExampleElement** Element aus der **Toolbox** auf die Diagrammoberfläche.  
  
5.  In der **Eigenschaften** Fenster für das Element, wählen Sie die **Element-Namespace** -Eigenschaft, und ändern Sie den Wert von **DefaultNamespace** auf **OtherNamespace**.  
  
     Beachten Sie, dass der Wert der **Element-Namespace** wird nun in Fettschrift angezeigt.  
  
6.  In der **Eigenschaften** -Fenster mit der rechten Maustaste **Element-Namespace**, und klicken Sie dann auf **zurücksetzen**.  
  
     Der Wert der Eigenschaft geändert wird, um **DefaultNamespace**, und der Wert wird in ein normaler Schrift angezeigt.  
  
     Mit der rechten Maustaste **Element-Namespace** erneut. Die **zurücksetzen** Befehl ist jetzt deaktiviert, da die Eigenschaft derzeit im Zustand nachverfolgen.  
  
7.  Ziehen Sie ein weiteres **ExampleElement** aus der **Toolbox** auf die Diagrammoberfläche, und ändern Sie seine **Element-Namespace** auf **OtherNamespace**.  
  
8.  Klicken Sie auf der Entwurfsoberfläche.  
  
     In der **Eigenschaften** Fenster für das Diagramm, das den Wert der **benutzerdefinierte Elemente** ist nun **1/2**.  
  
9. Änderung **Standard-Namespace** für das Diagramm aus **DefaultNamespace** auf **NewNamespace**.  
  
     Die **Namespace** der ersten Element Spuren der **Standard-Namespace** -Eigenschaft, während die **Namespace** des zweiten Element behält den Wert Benutzer aktualisiert **OtherNamespace**.  
  
10. Speichern Sie die Projektmappe, und schließen Sie dann die experimentellen Build.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Wenn Sie mehr als eine Tracking-Eigenschaft verwenden, oder Überwachungseigenschaften in mehr als eine DSL implementieren möchten, können Sie eine Textvorlage zum Generieren des gemeinsamen Codes zur Unterstützung der einzelnen Nachverfolgungseigenschaft erstellen. Weitere Informationen zu Textvorlagen finden Sie unter [Codegenerierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor></xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>   
 <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor></xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>   
 [Gewusst wie: definieren eine domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md)   
 [Gewusst wie: Erstellen einer domänenspezifischen Sprachlösung](../modeling/how-to-create-a-domain-specific-language-solution.md)   

