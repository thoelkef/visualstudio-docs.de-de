---
title: "Hinzufügen einer Überwachung-Eigenschaft für die Definition einer domänenspezifischen Sprache | Microsoft Docs"
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
caps.latest.revision: "22"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: a126524672b0b827d278d2d76c01d907c9d403a1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="adding-a-tracking-property-to-a-domain-specific-language-definition"></a>Hinzufügen einer Nachverfolgungseigenschaft zu einer domänenspezifischen Sprachdefinition
Diese exemplarische Vorgehensweise zeigt, wie eine Tracking-Eigenschaft zu einem Domänenmodell hinzugefügt.  
  
 Ein *nachverfolgen Domäne* Eigenschaft ist eine Eigenschaft, die vom Benutzer aktualisiert werden können, aber die hat eines Standardwert, der mit den Werten anderer Eigenschaften oder Elemente berechnet wird.  
  
 In der domänenspezifische Sprachtools (DSL Tools), den Anzeigenamen, die Eigenschaft einer Domänenklasse über einen Standardwert, der berechnet wird verfügt, mit dem Namen der Domänenklasse, aber ein Benutzer beispielsweise ändern Sie den Wert zur Entwurfszeit oder auf den berechneten Wert zurückgesetzt.  
  
 In dieser exemplarischen Vorgehensweise erstellen Sie eine domänenspezifische Sprache (DSL), die eine Eigenschaft, die einen Standardwert basierend auf der Standard-Namespace-Eigenschaft des Modells hat für das Nachverfolgen Namespace verfügt. Weitere Informationen zur Überwachung der Eigenschaften finden Sie unter [nachverfolgen Eigenschaften definieren](http://msdn.microsoft.com/en-us/0538b0e4-6221-4e7d-911a-b92cd622f0be).  
  
-   Die Überwachung von Eigenschaftendeskriptoren DSL-Tools-Unterstützung. Allerdings kann nicht der DSL-Designer zum Hinzufügen einer Überwachung-Eigenschaft zu einer anderen Sprache verwendet werden. Aus diesem Grund müssen Sie benutzerdefinierten Code zu definieren und implementieren Sie die Eigenschaft für die Überwachung hinzufügen.  
  
 Eine Überwachung-Eigenschaft verfügt über zwei Zustände: änderungsnachverfolgung und vom Benutzer aktualisiert. Eigenschaften der nachrichtenüberwachung weisen die folgenden Funktionen:  
  
-   Wenn in den Zustand "Überwachung" der Wert der Eigenschaft Überwachung wird berechnet, und der Wert wird als andere Eigenschaften in der Model-Änderung aktualisiert.  
  
-   Wenn in der aktualisierten von Benutzerzustand, behält der Wert der Nachverfolgungseigenschaft den Wert, der auf den der Benutzer zuletzt die Eigenschaft festgelegt.  
  
-   In der **Eigenschaften** Fenster die **zurücksetzen** Befehl für den Tracking-Eigenschaft nur aktiviert ist, wenn die Eigenschaft in der aktualisierten ist von Benutzerzustand. Die **zurücksetzen** Befehl setzt die Eigenschaft für die Überwachung auf Überwachung.  
  
-   In der **Eigenschaften** Fenster, wenn die Überwachung-Eigenschaft in den Zustand "Überwachung" der Wert ist, wird in ein normaler Schrift angezeigt.  
  
-   In der **Eigenschaften** Fenster, wenn die Überwachung-Eigenschaft in der aktualisierten ist von Benutzerzustand, dessen Wert in fett formatierter Schrift angezeigt.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Bevor Sie in dieser exemplarischen Vorgehensweise beginnen können, müssen Sie zunächst diese Komponenten installieren:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
## <a name="creating-the-dsl-project"></a>Erstellen des Projekts DSL  
 Erstellen Sie das Projekt für Ihre einer domänenspezifischen Sprache.  
  
#### <a name="to-create-the-project"></a>So erstellen Sie das Projekt  
  
1.  Erstellen Sie eine domänenspezifische Sprachdesigner-Projekt. Nennen Sie es `TrackingPropertyDSL`.  
  
2.  In der **einer domänenspezifischen Sprache-Designer-Assistenten**, die folgenden Optionen festlegen:  
  
    1.  Wählen Sie die **MinimalLanguage** Vorlage.  
  
    2.  Verwenden Sie den Standardnamen für die domänenspezifischen Sprache `TrackingPropertyDSL`.  
  
    3.  Legen Sie die Erweiterung für Modelldateien zu `trackingPropertyDsl`.  
  
    4.  Verwenden Sie das Symbol für Standardvorlage für den Modelldateien.  
  
    5.  Legen Sie den Namen des Produkts für `Product Name`.  
  
    6.  Legen Sie den Namen des Unternehmens zu `Company Name`.  
  
    7.  Verwenden Sie den Standardwert für den Stammnamespace für Projekte in der Projektmappe `CompanyName.ProductName.TrackingPropertyDSL`.  
  
    8.  Lassen Sie den Assistenten, um eine Schlüsseldatei mit starkem Namen für die Assemblys zu erstellen.  
  
    9. Überprüfen Sie die Details der Projektmappe, und klicken Sie dann auf **Fertig stellen** zum Erstellen des Projekts der DSL-Definition.  
  
## <a name="customizing-the-default-dsl-definition"></a>Anpassen der Default-Definition für DSL  
 In diesem Abschnitt können Sie anpassen, die DSL-Definition, um die folgenden Elemente enthalten:  
  
-   Ein Namespace tracking-Eigenschaft für jedes Element des Modells.  
  
-   Eine boolesche IsNamespaceTracking-Eigenschaft für jedes Element des Modells. Diese Eigenschaft wird angegeben, ob die Überwachung Eigenschaft im Status "Überwachung" oder in der aktualisierten von Benutzerzustand.  
  
-   Eine Standard-Namespace-Eigenschaft für das Modell. Diese Eigenschaft wird zum Berechnen des Standardwert der Eigenschaft für das Nachverfolgen Namespace verwendet werden.  
  
-   Eine für das Modell berechnet CustomElements-Eigenschaft. Diese Eigenschaft wird das Verhältnis von Elementen angegeben, die einen benutzerdefinierten Namespace aufweist.  
  
#### <a name="to-add-the-domain-properties"></a>So fügen Sie den Domäneneigenschaften hinzu  
  
1.  DSL-Designer mit der Maustaste die **ExampleModel** Domänenklasse, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **DomainProperty**.  
  
    1.  Benennen Sie die neue Eigenschaft `DefaultNamespace`.  
  
    2.  In der **Eigenschaften** legen Sie im Fenster für die neue Eigenschaft **Standardwert** auf `DefaultNamespace`, und legen Sie **Typ** auf **Zeichenfolge**.  
  
2.  Um die **ExampleModel** Domäne-Klasse erstellt wird, eine Eigenschaft "Domain" mit dem Namen `CustomElements`.  
  
     In der **Eigenschaften** legen Sie im Fenster für die neue Eigenschaft **Art** auf **berechnete**.  
  
3.  Um die **ExampleElement** Domäne-Klasse erstellt wird, eine Eigenschaft "Domain" mit dem Namen `Namespace`.  
  
     In der **Eigenschaften** legen Sie im Fenster für die neue Eigenschaft **durchsuchbar ist** auf **"false"**, und legen Sie **Art** auf **CustomStorage** .  
  
4.  Um die **ExampleElement** Domäne-Klasse erstellt wird, eine Eigenschaft "Domain" mit dem Namen `IsNamespaceTracking`.  
  
     In der **Eigenschaften** Fenster für die neue Eigenschaft festlegen **durchsuchbar ist** auf **"false"**legen **Standardwert** auf `true`, und legen Sie **Typ** auf **booleschen**.  
  
#### <a name="to-update-the-diagram-elements-and-dsl-details"></a>So aktualisieren Sie die Diagrammelemente und DSL-Detailfenster  
  
1.  DSL-Designer mit der Maustaste die **ExampleShape** Form "Geometry", zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Text Decorator**.  
  
    1.  Benennen Sie den neuen Text Decorator `NamespaceDecorator`.  
  
    2.  In der **Eigenschaften** legen die Decorator Text **Position** auf **InnerBottomLeft**.  
  
2.  Wählen Sie in der DSL-Designer, der Verbindungslinie der **ExampleElement** Klasse, um die **ExampleShape** Form.  
  
    1.  In der **DSL-Detailfenster** wählen die **Decorator-Zuordnungen** Registerkarte.  
  
    2.  In der **Decorators** aufgeführt wird, wählen **NamespaceDecorator**, wählen Sie das Kontrollkästchen und klicken Sie dann auf die **Anzeigeeigenschaft** Liste **Namespace**.  
  
3.  In **Explorer für DSL**, erweitern Sie die **Domänenklassen** Ordner mit der rechten Maustaste die **ExampleElement** Knoten, und klicken Sie dann auf **Hinzufügen neuer Domäne Typdeskriptor**.  
  
    1.  Erweitern Sie die **ExampleElement** Knoten, und wählen die **benutzerdefinierten Typdeskriptors (Domäne Typdeskriptor)** Knoten.  
  
    2.  In der **Eigenschaften** Fenster für den Typdeskriptor Domäne festlegen **benutzerdefinierte codierten** auf **"true"**.  
  
4.  In **Explorer für DSL**, wählen die **XML-Serialisierungsverhalten** Knoten.  
  
    1.  In der **Eigenschaften** legen **benutzerdefinierte Post laden** auf **"true"**.  
  
## <a name="transforming-templates"></a>Transformieren von Vorlagen  
 Nun, dass Sie die Domänenklassen und Eigenschaften für der DSL definiert haben, können Sie überprüfen, dass die DSL-Definition ordnungsgemäß transformiert werden kann, um den Code für das Projekt erneut zu generieren.  
  
#### <a name="to-transform-the-text-templates"></a>Zum Transformieren der Textvorlagen  
  
1.  Auf der **Projektmappen-Explorer** -Symbolleiste klicken Sie auf **alle Vorlagen transformieren**.  
  
2.  Das System generiert den Code für die Projektmappe und DslDefinition.dsl speichert. Informationen über das Format der XML-Definitionsdateien finden Sie unter [der DslDefinition.dsl Datei](../modeling/the-dsldefinition-dsl-file.md).  
  
## <a name="creating-files-for-custom-code"></a>Erstellen von Dateien für benutzerdefinierten Code  
 Wenn Sie alle Vorlagen transformieren, generiert das System den Quellcode, der in den Projekten Dsl und DslPackage einer domänenspezifischen Sprache definiert. Um Sie dem generierten Text stören vermeiden, Schreiben Sie den benutzerdefinierten Code in Dateien, die sich von den generierten Codedateien sind.  
  
 Sie müssen den Code angeben, für die Aufrechterhaltung der Wert und den Status der Überwachung Eigenschaft. Können Sie Ihren benutzerdefinierten Code aus dem generierten Code zu unterscheiden und Datei Namenskonflikte zu vermeiden, legen Sie Ihre benutzerdefinierten Code-Dateien in einem separaten Unterordner.  
  
#### <a name="to-create-the-code-files"></a>So erstellen die Codedateien  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **DSL** Projekt, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **neuer Ordner**. Nennen Sie diesen Ordner `CustomCode`.  
  
2.  Mit der rechten Maustaste das neue **CustomCode** Ordner, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **neues Element**.  
  
3.  Wählen Sie die **Codedatei** Vorlagensatz, der **Name** zu `NamespaceTrackingProperty.cs`, und klicken Sie dann auf **OK**.  
  
     Die NamespaceTrackingProperty.cs-Datei wird erstellt und zur Bearbeitung geöffnet.  
  
4.  Erstellen Sie die folgenden Codedateien im Ordner: `ExampleModel.cs,``HelperClasses.cs`, `Serialization.cs`, und `TypeDescriptor.cs`.  
  
5.  In der **DslPackage** Projekt, erstellen Sie auch eine `CustomCode` Ordner und Hinzufügen einer `Package.cs` Codedatei.  
  
## <a name="adding-helper-classes-to-support-tracking-properties"></a>Hinzufügen von Hilfsklassen zur Unterstützung von Überwachungseigenschaften  
 Fügen Sie der Datei HelperClasses.cs hinzu der `TrackingHelper` und `CriticalException` Klassen wie folgt. Sie können diese Klassen weiter unten in dieser exemplarischen Vorgehensweise verweisen.  
  
#### <a name="to-add-the-helper-classes"></a>So fügen Sie die Hilfsklassen hinzu  
  
1.  Fügen Sie den folgenden Code in die Datei HelperClasses.cs.  
  
    ```csharp  
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
 Implementieren der `GetCustomProperties` Methode für den Typdeskriptor für den `ExampleModel` Domain-Klasse.  
  
> [!NOTE]
>  Der Code, der der DSL-Tools für die benutzerdefinierten Typdeskriptor für generieren `ExampleModel` Aufrufe `GetCustomProperties`, aber der DSL-Tools generieren keine Code, der die Methode implementiert.  
  
 Definieren diese Methode erstellt den Überwachungsprofil-Eigenschaftendeskriptor für die Namespace-Eigenschaft für das nachverfolgen. Darüber hinaus kann Attribute für den Tracking-Eigenschaft liefert die **Eigenschaften** Fenster aus, um die Eigenschaft ordnungsgemäß anzeigen.  
  
#### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>So ändern Sie den Typdeskriptor für die ExampleModel Domäne-Klasse  
  
1.  Fügen Sie den folgenden Code in die Datei TypeDescriptor.cs.  
  
    ```csharp  
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
 Der generierte Code definiert einen Typbeschreibungsanbieter für die ExampleElement Domäne-Klasse. Allerdings müssen Sie Code aus, um die DSL mit diesem Typbeschreibungsanbieter anweisen hinzufügen.  
  
#### <a name="to-update-the-dsl-package-to-use-your-custom-type-descriptor"></a>Beim Aktualisieren der DSL-Paket, um Ihre benutzerdefinierten Typdeskriptors zu verwenden  
  
1.  Fügen Sie den folgenden Code in die Datei Package.cs.  
  
    ```csharp  
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
>  Der Code, der der DSL-Tools für generieren `ExampleModel` Aufrufe `GetCustomElementsValue`, aber der DSL-Tools generieren keine Code, der die Methode implementiert.  
  
 Definieren der `GetCustomElementsValue` Methode stellt die Logik für die Eigenschaft CustomElements berechnet `ExampleModel`. Diese Methode zählt die Anzahl der `ExampleElement` Domänenklassen, die einen Namespace tracking-Eigenschaft, die einen Wert Benutzer aktualisiert wurde, und gibt eine Zeichenfolge, die diese Anzahl als Anteil der insgesamt Elemente im Modell darstellt.  
  
 Darüber hinaus fügen eine `OnDefaultNamespaceChanged` Methode, um `ExampleModel`, und überschreiben die `OnValueChanged` Methode der `DefaultNamespacePropertyHandler` der geschachtelten Klasse von `ExampleModel` Aufrufen `OnDefaultNamespaceChanged`.  
  
 Da die DefaultNamespace-Eigenschaft, zum Berechnen der Namespace verwendet wird-Eigenschaft, für das Nachverfolgen `ExampleModel` müssen alle benachrichtigen `ExampleElement` Domänenklassen, die der Wert der DefaultNamespace geändert hat.  
  
#### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Den Handler für die überwachten Eigenschaft ändern.  
  
1.  Fügen Sie den folgenden Code in die Datei ExampleModel.cs.  
  
    ```csharp  
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
  
## <a name="adding-custom-code-for-the-tracking-property"></a>Hinzufügen von benutzerdefiniertem Code für den Tracking-Eigenschaft  
 Hinzufügen einer `CalculateNamespace` Methode, um die `ExampleElement` Domain-Klasse.  
  
 Definieren diese Methode stellt die Logik für die Eigenschaft CustomElements berechnet `ExampleModel`. Diese Methode zählt die Anzahl der `ExampleElement` Domänenklassen, die einen Namespace, die Eigenschaft, die in der aktualisierten ist für das Nachverfolgen von Benutzerzustand, und gibt eine Zeichenfolge, die diese Anzahl als Anteil der insgesamt Elemente im Modell darstellt.  
  
 Zudem hinzufügen für Speicher- und Methoden zum Abrufen und festlegen, der Namespace "benutzerdefinierte Storage"-Eigenschaft von der `ExampleElement` Domain-Klasse.  
  
> [!NOTE]
>  Der Code, der der DSL-Tools für generieren `ExampleModel` Ruft die Get und set-Methoden; der DSL-Tools generieren jedoch keine Code, der die Methoden implementiert.  
  
#### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Die Methode für die benutzerdefinierten Typdeskriptors hinzu  
  
1.  Fügen Sie den folgenden Code in die Datei NamespaceTrackingProperty.cs.  
  
    ```csharp  
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
  
## <a name="adding-custom-code-to-support-serialization"></a>Hinzufügen von benutzerdefiniertem Code zur Unterstützung von Serialisierung  
 Fügen Sie Code zur Unterstützung von benutzerdefinierten Verhaltens nach der Last für die XML-Serialisierung.  
  
> [!NOTE]
>  Der Code, der DSL-Tools Aufrufe generieren die `OnPostLoadModel` und `OnPostLoadModelAndDiagram` -Methoden der DSL-Tools generieren jedoch keine Code, der diese Methoden implementiert.  
  
#### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Hinzufügen von Code zur Unterstützung von benutzerdefinierten nach der Ladeverhaltens  
  
1.  Fügen Sie den folgenden Code in die Datei Serialization.cs.  
  
    ```csharp  
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
 Der nächste Schritt ist zum Erstellen und Ausführen der DSL-Designer in eine neue Instanz der [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , damit Sie überprüfen können, dass die Eigenschaft für die Überwachung ordnungsgemäß funktioniert.  
  
#### <a name="to-exercise-the-language"></a>Um die zu der Sprache  
  
1.  Auf der **erstellen** Menü klicken Sie auf **Projektmappe neu erstellen**.  
  
2.  Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
     Das experimentelle Build von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] öffnet die **Debuggen** Lösung, die eine leeren Test-Datei enthält.  
  
3.  In **Projektmappen-Explorer**, doppelklicken Sie auf die Test.trackingPropertyDsl-Datei, um es im Designer zu öffnen, und klicken Sie dann auf der Entwurfsoberfläche angezeigt.  
  
     Beachten Sie, dass in der **Eigenschaften** Fenster für das Diagramm die **Default Namespace** Eigenschaft ist **DefaultNamespace**, und die **benutzerdefinierte Elemente** Eigenschaft **0/0**.  
  
4.  Ziehen Sie ein **ExampleElement** Element aus der **Toolbox** auf der Diagrammoberfläche.  
  
5.  In der **Eigenschaften** Fenster für das Element, wählen Sie die **Element-Namespace** -Eigenschaft, und ändern Sie den Wert von **DefaultNamespace** auf  **OtherNamespace**.  
  
     Beachten Sie, dass der Wert der **Element-Namespace** wird jetzt in Fettdruck angezeigt.  
  
6.  In der **Eigenschaften** Fenster mit der rechten Maustaste **Element-Namespace**, und klicken Sie dann auf **zurücksetzen**.  
  
     Der Wert der Eigenschaft wird geändert, um **DefaultNamespace**, und der Wert in ein normaler Schrift angezeigt wird.  
  
     Mit der rechten Maustaste **Element-Namespace** erneut aus. Die **zurücksetzen** Befehl ist jetzt deaktiviert, da die Eigenschaft derzeit im Überwachungsprofil Zustand ist.  
  
7.  Ziehen Sie ein weiteres **ExampleElement** aus der **Toolbox** auf die Diagrammoberfläche, und ändern Sie seine **Element-Namespace** auf **OtherNamespace**.  
  
8.  Klicken Sie auf der Entwurfsoberfläche angezeigt.  
  
     In der **Eigenschaften** Fenster für das Diagramm, das den Wert der **benutzerdefinierte Elemente** ist jetzt **1/2**.  
  
9. Änderung **Default Namespace** für das Diagramm aus **DefaultNamespace** auf **NewNamespace**.  
  
     Die **Namespace** der das erste Element verfolgt den **Default Namespace** -Eigenschaft, während die **Namespace** des zweiten Element behält seine Benutzer aktualisierte Wert des  **OtherNamespace**.  
  
10. Speichern Sie die Projektmappe, und schließen Sie dann das experimentelle Build.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Wenn Sie mehr als eine Tracking-Eigenschaft verwenden, oder Überwachungseigenschaften in mehr als eine DSL implementieren möchten, können Sie eine Textvorlage zum Generieren des allgemeinen Codes für die Unterstützung der einzelnen Tracking-Eigenschaft erstellen. Weitere Informationen zu den Textvorlagen finden Sie unter [Codegenerierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>   
 <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>   
 [Gewusst wie: definieren eine domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md)   
 [Gewusst wie: Erstellen einer domänenspezifischen Sprachlösung](../modeling/how-to-create-a-domain-specific-language-solution.md)   
