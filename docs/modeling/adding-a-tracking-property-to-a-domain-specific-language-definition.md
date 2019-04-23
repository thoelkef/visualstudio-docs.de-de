---
title: Hinzufügen einer Nachverfolgungseigenschaft zu einer domänenspezifischen Sprachdefinition
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd4bf8b1b6f43e8ed12b133a621e21157fb87118
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59657388"
---
# <a name="add-a-tracking-property-to-a-domain-specific-language-definition"></a>Hinzufügen einer Nachverfolgungseigenschaft zu einer domänenspezifischen Sprachdefinition

Diese exemplarische Vorgehensweise veranschaulicht das Hinzufügen eine Nachverfolgungseigenschaft zu einem Domänenmodell.

Ein *Domäne nachverfolgen* Eigenschaft ist eine Eigenschaft, die vom Benutzer aktualisiert werden können, aber das hat es sich um einen Standardwert, der mit den Werten anderer Eigenschaften von Domänen oder die Elemente berechnet wird.

In der domänenspezifische Sprachtools (DSL-Tools), den Anzeigenamen, die Eigenschaft einer Domänenklasse einen Standardwert, der berechnet wird verfügt, mit dem Namen der Domänenklasse, aber ein Benutzer z. B. ändern Sie den Wert zur Entwurfszeit oder auf den berechneten Wert zurückgesetzt.

In dieser exemplarischen Vorgehensweise erstellen Sie eine domänenspezifische Sprache (DSL), die einen Namespace, die Eigenschaft, die einen Standardwert basierend auf der Standard-Namespace-Eigenschaft des Modells verfügt. Weitere Informationen zu überwachen – Eigenschaften, finden Sie unter [nachverfolgung Eigenschaften](https://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be).

- Die DSL-Tools unterstützen, Nachverfolgen von Eigenschaftendeskriptoren. Allerdings kann nicht der DSL-Designer verwendet werden, zum Hinzufügen einer Nachverfolgungseigenschaft zu einer Sprache. Aus diesem Grund müssen Sie benutzerdefinierten Code zum Definieren und implementieren Sie die änderungsverfolgungseigenschaft hinzufügen.

  Eine Nachverfolgungseigenschaft verfügt über zwei Zustände: nachzuverfolgen und vom Benutzer aktualisiert. Eigenschaften der nachrichtenüberwachung weisen die folgenden Funktionen:

- Klicken Sie in den Status der änderungsnachverfolgung, der Wert der Nachverfolgungseigenschaft wird berechnet, und der Wert wird aktualisiert, wie andere Eigenschaften in das Modell ändern.

- Wenn in der aktualisierten von Benutzerstatus, behält der Wert der Nachverfolgungseigenschaft den Wert, der auf den der Benutzer zuletzt die Eigenschaft festgelegt.

- In der **Eigenschaften** Fenster die **zurücksetzen** Befehl für die änderungsverfolgungseigenschaft nur aktiviert werden, ist wenn die Eigenschaft in der aktualisierten von Benutzerzustand. Die **zurücksetzen** Befehl wird die änderungsverfolgungseigenschaft Status nachverfolgen.

- In der **Eigenschaften** Fenster, wenn die Nachverfolgungseigenschaft in den Zustand "Überwachung" der Wert ist, wird in ein normaler Schrift angezeigt.

- In der **Eigenschaften** Fenster, wenn die Nachverfolgungseigenschaft in der aktualisierten ist ihr Wert durch den Benutzerstatus in fett formatierter Schrift angezeigt wird.

## <a name="prerequisites"></a>Vorraussetzungen

Bevor Sie in dieser exemplarischen Vorgehensweise beginnen können, müssen Sie zunächst diese Komponenten installieren:

| | |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580) |
| [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581) |

## <a name="create-the-project"></a>Erstellen eines Projekts

1.  Erstellen Sie ein Projekt für die domänenspezifischen Sprach-Designers. Nennen Sie es `TrackingPropertyDSL`.

2.  In der **Domain-Specific Language-Designer-Assistenten**, die folgenden Optionen festlegen:

    1.  Wählen Sie die **MinimalLanguage** Vorlage.

    2.  Verwenden Sie den Standardnamen für die domänenspezifische Sprache, `TrackingPropertyDSL`.

    3.  Legen Sie die Erweiterung für den Modelldateien zur `trackingPropertyDsl`.

    4.  Verwenden Sie das Symbol für Standardvorlage für die Modelldateien.

    5.  Legen Sie den Namen des Produkts an `Product Name`.

    6.  Legen Sie den Namen des Unternehmens zu `Company Name`.

    7.  Verwenden Sie den Standardwert für den Stammnamespace für Projekte in der Projektmappe `CompanyName.ProductName.TrackingPropertyDSL`.

    8.  Ermöglichen Sie der Assistent eine Schlüsseldatei mit starkem Namen für die Assemblys zu erstellen.

    9. Überprüfen Sie die Details der Lösung, und klicken Sie dann auf **Fertig stellen** das DSL-Definition-Projekt erstellt.

## <a name="customize-the-default-dsl-definition"></a>Anpassen der Standard-DSL-Definition
 In diesem Abschnitt passen Sie die DSL-Definition, um die folgenden Elemente enthalten:

-   Ein Namespace, die Eigenschaft für jedes Element des Modells.

-   Eine boolesche IsNamespaceTracking-Eigenschaft für jedes Element des Modells. Mit dieser Eigenschaft wird angegeben, ob die Nachverfolgungseigenschaft in den Status der änderungsnachverfolgung oder in der aktualisierten von Benutzerzustand.

-   Eine Standard-Namespace-Eigenschaft für das Modell. Diese Eigenschaft wird zum Berechnen des Standardwert der Eigenschaft Namespace verwendet werden.

-   Eine berechnete CustomElements-Eigenschaft für das Modell. Diese Eigenschaft gibt den Anteil der Elemente, die einen benutzerdefinierten Namespace enthalten.

### <a name="to-add-the-domain-properties"></a>Hinzufügen von Domäneneigenschaften

1.  In der DSL-Designer, mit der Maustaste der **ExampleModel** Domänenklasse, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **DomainProperty**.

    1.  Benennen Sie die neue Eigenschaft `DefaultNamespace`.

    2.  In der **Eigenschaften** Zeitfenster für die neue Eigenschaft **Standardwert** zu `DefaultNamespace`, und legen Sie **Typ** zu **Zeichenfolge**.

2.  Um die **ExampleModel** Domäne-Klasse verwenden, fügen Sie eine Domäneneigenschaft namens `CustomElements`.

     In der **Eigenschaften** Zeitfenster für die neue Eigenschaft **Art** zu **berechnete**.

3.  Um die **ExampleElement** Domäne-Klasse verwenden, fügen Sie eine Domäneneigenschaft namens `Namespace`.

     In der **Eigenschaften** Zeitfenster für die neue Eigenschaft **kann durchsucht werden** zu **"false"**, und legen Sie **Art** zu **"CustomStorage"** .

4.  Um die **ExampleElement** Domäne-Klasse verwenden, fügen Sie eine Domäneneigenschaft namens `IsNamespaceTracking`.

     In der **Eigenschaften** Zeitfenster für die neue Eigenschaft **kann durchsucht werden** zu **"false"** legen **Standardwert** zu `true`, und legen Sie **Typ** zu **booleschen**.

### <a name="to-update-the-diagram-elements-and-dsl-details"></a>So aktualisieren Sie die Diagrammelemente und DSL-details

1.  In der DSL-Designer, mit der Maustaste der **ExampleShape** Geometrie-Form, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Text-Decorator**.

    1.  Benennen Sie den neuen Text-Decorator `NamespaceDecorator`.

    2.  In der **Eigenschaften** Zeitfenster für die Text-Decorator **Position** zu **InnerBottomLeft**.

2.  Wählen Sie im DSL-Designer der Verbindungslinie der **ExampleElement** -Klasse der **ExampleShape** Form.

    1.  In der **DSL-Details** wählen Sie im Fenster der **Decorator-Zuordnungen** Registerkarte.

    2.  In der **Decorator-Elemente** Liste **NamespaceDecorator**, aktivieren Sie das Kontrollkästchen, und klicken Sie dann auf die **Anzeigeeigenschaft** Liste **Namespace**.

3.  In **DSL-Explorer**, erweitern Sie die **Domänenklassen** Ordner mit der rechten Maustaste die **ExampleElement** Knoten, und klicken Sie dann auf **Hinzufügen neuer Domänentypdeskriptor**.

    1.  Erweitern Sie die **ExampleElement** Knoten, und wählen die **benutzerdefinierten Typdeskriptor (Domänentypdeskriptor)** Knoten.

    2.  In der **Eigenschaften** Zeitfenster für die domänentypdeskriptor **benutzerdefinierte codiert** zu **"true"**.

4.  In **DSL-Explorer**, wählen die **XML-Serialisierungsverhalten** Knoten.

    1.  In der **Eigenschaften** legen **benutzerdefinierte nach dem Laden** zu **"true"**.

## <a name="transform-templates"></a>Vorlagen transformieren

Nun, da Sie die Domänenklassen und Eigenschaften für Ihre DSL definiert haben, können Sie überprüfen, ob die DSL-Definition ordnungsgemäß transformiert werden kann, um den Code für das Projekt erneut zu generieren.

1.  Auf der **Projektmappen-Explorer** -Symbolleiste klicken Sie auf **alle Vorlagen transformieren**.

2.  Das System generiert den Code für die Projektmappe, und speichert "DslDefinition.DSL". Weitere Informationen zum XML-Format von Definitionsdateien, finden Sie unter [Datei für die "DslDefinition.DSL"](../modeling/the-dsldefinition-dsl-file.md).

## <a name="create-files-for-custom-code"></a>Dateien für benutzerdefinierten Code erstellen

Wenn Sie alle Vorlagen transformieren, generiert das System den Quellcode, der Ihrer domänenspezifischen Sprache in den Projekten Dsl "und" DslPackage definiert. Damit Sie mit der generierte Text behindert vermeiden können, Schreiben Sie Ihren benutzerdefinierten Code, in Dateien, die sich von den generierten Codedateien befinden.

Sie müssen Code für die Verwaltung der Wert und den Status Ihrer Nachverfolgungseigenschaft angeben. Können Sie Ihren benutzerdefinierten Code aus dem generierten Code zu unterscheiden und Datei Namenskonflikte zu vermeiden, speichern Sie Ihre benutzerdefinierten Code-Dateien in einem separaten Unterordner.

1.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **DSL** Projekt, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **neuer Ordner**. Nennen Sie diesen Ordner `CustomCode`.

2.  Mit der rechten Maustaste den neuen **CustomCode** Ordner, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **neues Element**.

3.  Wählen Sie die **Codedatei** legen Sie die Vorlage der **Name** zu `NamespaceTrackingProperty.cs`, und klicken Sie dann auf **OK**.

     Die NamespaceTrackingProperty.cs-Datei wird erstellt und zur Bearbeitung geöffnet.

4.  In den Ordner, erstellen Sie die folgenden Codedateien: `ExampleModel.cs,``HelperClasses.cs`, `Serialization.cs`, und `TypeDescriptor.cs`.

5.  In der **DslPackage** Projekt, erstellen Sie auch eine `CustomCode` Ordner, und fügen Sie hinzu eine `Package.cs` Codedatei.

## <a name="add-helper-classes-to-support-tracking-properties"></a>Hinzufügen von Hilfsklassen zur Unterstützung von Überwachungseigenschaften

Fügen Sie der Datei HelperClasses.cs hinzu der `TrackingHelper` und `CriticalException` Klassen wie folgt. Sie werden diese Klassen weiter unten in dieser exemplarischen Vorgehensweise verweisen.

1.  Fügen Sie den folgenden Code in die Datei HelperClasses.cs hinzu.

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

## <a name="add-custom-code-for-the-custom-type-descriptor"></a>Hinzufügen von benutzerdefiniertem Code für den benutzerdefinierten Typdeskriptor

Implementieren der `GetCustomProperties` Methode für den Typdeskriptor für den `ExampleModel` Domänenklasse.

> [!NOTE]
> Der Code, der der DSL-Tools für die benutzerdefinierten Typdeskriptor für generieren `ExampleModel` Aufrufe `GetCustomProperties`, aber der DSL-Tools generieren keine Code, der die Methode implementiert.

Definieren diese Methode erstellt die nachverfolgungs-Eigenschaftendeskriptor für den Namespace-Eigenschaft. Bereitstellen der Attribute, die für die Eigenschaft für die Überwachung ermöglicht außerdem die **Eigenschaften** Fenster aus, um die Eigenschaft richtig angezeigt.

### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>So ändern Sie den Typdeskriptor für die Domänenklasse ExampleModel

1.  Fügen Sie den folgenden Code in die Datei TypeDescriptor.cs hinzu.

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

Der generierte Code definiert einen Typbeschreibungsanbieter für die Domänenklasse ExampleElement. Allerdings müssen Sie Code, um anzuweisen, die DSL für die Verwendung dieses typanbieters-Beschreibung hinzufügen.

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

## <a name="add-custom-code-for-the-model"></a>Hinzufügen von benutzerdefiniertem Code für das Modell

Implementieren der `GetCustomElementsValue` -Methode für die `ExampleModel` Domänenklasse.

> [!NOTE]
> Der Code, der für die DSL-Tools generieren `ExampleModel` Aufrufe `GetCustomElementsValue`, aber der DSL-Tools generieren keine Code, der die Methode implementiert.

Definieren der `GetCustomElementsValue` Methode enthält die Logik für die Eigenschaft berechnet CustomElements `ExampleModel`. Diese Methode zählt die Anzahl der `ExampleElement` Domänenklassen, die einen Namespace, die Eigenschaft, die einen Benutzer aktualisierte Wert und gibt eine Zeichenfolge, die diese Zahl als einen Anteil der insgesamt Elemente im Modell darstellt.

Fügen Sie darüber hinaus eine `OnDefaultNamespaceChanged` Methode, um `ExampleModel`, und überschreiben die `OnValueChanged` -Methode der der `DefaultNamespacePropertyHandler` geschachtelte Klasse der `ExampleModel` Aufrufen `OnDefaultNamespaceChanged`.

Da die DefaultNamespace-Eigenschaft verwendet wird, um die Namespace-Eigenschaft, zu berechnen `ExampleModel` muss alle benachrichtigen `ExampleElement` Domänenklassen, die der Wert der DefaultNamespace-Eigenschaft geändert wurde.

### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Den Handler für die nachverfolgte Eigenschaft ändern.

1.  Fügen Sie den folgenden Code in die Datei ExampleModel.cs hinzu.

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

## <a name="add-custom-code-for-the-tracking-property"></a>Hinzufügen von benutzerdefiniertem Code für die Nachverfolgungseigenschaft

Hinzufügen einer `CalculateNamespace` Methode, um die `ExampleElement` Domänenklasse.

Definieren diese Methode enthält die Programmlogik für die Eigenschaft CustomElements berechnet `ExampleModel`. Diese Methode zählt die Anzahl der `ExampleElement` Domänenklassen, die über eine Eigenschaft, die in der aktualisierten Namespace von Benutzerstatus, und gibt eine Zeichenfolge, die diese Zahl als einen Anteil der insgesamt Elemente im Modell darstellt.

Außerdem hinzufügen, Speicher für und Methoden zum Abrufen und festlegen, die Eigenschaft Namespace benutzerdefinierten Speicher, der die `ExampleElement` Domänenklasse.

> [!NOTE]
> Der Code, der für die DSL-Tools generieren `ExampleModel` Ruft die Get und set-Methoden, die DSL-Tools generieren jedoch keine Code, der die Methoden implementiert.

### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Die Methode für den benutzerdefinierten Typdeskriptor hinzufügen

1.  Fügen Sie den folgenden Code in die Datei NamespaceTrackingProperty.cs hinzu.

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

## <a name="add-custom-code-to-support-serialization"></a>Hinzufügen von benutzerdefiniertem Code zur Unterstützung der Serialisierung

Fügen Sie Code, um das benutzerdefinierte Verhalten der nach dem Laden für XML-Serialisierung unterstützen.

> [!NOTE]
> Der Code, der DSL-Tools Aufrufe generieren die `OnPostLoadModel` und `OnPostLoadModelAndDiagram` Methoden der DSL-Tools generieren jedoch keine Code, der diese Methoden implementiert.

### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Hinzufügen von Code zur Unterstützung von benutzerdefinierten Verhaltens nach dem Laden

1.  Fügen Sie den folgenden Code in die Datei Serialization.cs hinzu.

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

## <a name="test-the-language"></a>Testen Sie die Sprache

Der nächste Schritt besteht darin erstellen und führen die DSL-Designer in eine neue Instanz der [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , damit Sie überprüfen können, dass die Eigenschaft für die Überwachung ordnungsgemäß funktioniert.

1. Klicken Sie im Menü **Build** auf **Projektmappe neu erstellen**.

2. Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.

    Das experimentelle Build von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] öffnet die **Debuggen** Lösung, die eine leere Testdatei enthält.

3. In **Projektmappen-Explorer**, doppelklicken Sie auf die Test.trackingPropertyDsl-Datei, um es im Designer zu öffnen, und klicken Sie dann auf die Entwurfsoberfläche.

    Beachten Sie, dass in der **Eigenschaften** Fenster für das Diagramm, das **Default Namespace** -Eigenschaft ist **DefaultNamespace-Eigenschaft**, und die **benutzerdefinierte Elemente** Eigenschaft **0/0**.

4. Ziehen Sie ein **ExampleElement** Element aus der **Toolbox** auf die Diagrammoberfläche.

5. In der **Eigenschaften** Fenster für das Element, wählen die **-Element-Namespace** -Eigenschaft, und ändern Sie den Wert **DefaultNamespace** zu  **OtherNamespace**.

    Beachten Sie, dass der Wert des **-Element-Namespace** ist jetzt in Fettschrift angezeigt.

6. In der **Eigenschaften** Fenster mit der rechten Maustaste **-Element-Namespace**, und klicken Sie dann auf **zurücksetzen**.

    Der Wert der Eigenschaft geändert wird, um **DefaultNamespace**, und der Wert in ein normaler Schrift angezeigt.

    Mit der rechten Maustaste **-Element-Namespace** erneut aus. Die **zurücksetzen** Befehl ist jetzt deaktiviert, da die Eigenschaft derzeit in der Status der änderungsnachverfolgung.

7. Ziehen Sie ein weiteres **ExampleElement** aus der **Toolbox** auf die Diagrammoberfläche, und ändern Sie seine **-Element-Namespace** zu **OtherNamespace**.

8. Klicken Sie auf der Entwurfsoberfläche angezeigt.

    In der **Eigenschaften** Fenster für das Diagramm, das den Wert der **benutzerdefinierte Elemente** ist jetzt **1/2**.

9. Änderung **Default Namespace** für das Diagramm aus **DefaultNamespace** zu **NewNamespace**.

     Die **Namespace** der das erste Element verfolgt die **Default Namespace** -Eigenschaft, während die **Namespace** behält Sie ihren Benutzer aktualisiert-Wert, der deszweitenElements **OtherNamespace**.

10. Speichern Sie die Projektmappe, und schließen Sie das experimentelle Build.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie mehr als eine Nachverfolgungseigenschaft verwenden oder Eigenschaften der nachrichtenüberwachung in mehr als eine DSL implementieren möchten, können Sie eine Textvorlage zum Generieren des allgemeinen Codes für die Unterstützung der einzelnen Nachverfolgungseigenschaft erstellen. Weitere Informationen zu Textvorlagen finden Sie unter [Codegenerierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md).

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>
- <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
- [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)
- [Vorgehensweise: Erstellen einer Projektmappe für eine domänenspezifische Sprache](../modeling/how-to-create-a-domain-specific-language-solution.md)
