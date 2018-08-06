---
title: Anpassen des Eigenschaftenfensters
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: b9c1aec06469e5ea0845a8658d9dcb88563e1984
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39567167"
---
# <a name="customizing-the-properties-window"></a>Anpassen des Eigenschaftenfensters
Sie können das Aussehen und Verhalten des Fensters Eigenschaften in Ihrer domänenspezifischen Sprache (DSL) anpassen, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In Ihrer DSL-Definition definieren Sie Domäneneigenschaften fest, für jede Domänenklasse. Wenn Sie eine Instanz der Klasse in einem Diagramm oder im Modell-Explorer auswählen, wird jede Domäneneigenschaft standardmäßig in das Fenster "Eigenschaften" aufgeführt. Dadurch können Sie die anzeigen und bearbeiten die Werte der Eigenschaften von Domänen, auch wenn Sie diese Form von Feldern im Diagramm nicht zugeordnet haben.

## <a name="names-descriptions-and-categories"></a>Namen, Beschreibungen und Kategorien
 **Name und Anzeigename**. In die Definition einer Domäneneigenschaft ist der Anzeigename der Eigenschaft den Namen, der zur Laufzeit in das Fenster "Eigenschaften" angezeigt wird. Im Gegensatz dazu wird der Name verwendet, beim Schreiben von Programmcode, der Eigenschaft zu aktualisieren. Der Name muss eine richtige CLR alphanumerischer Name sein, aber der Anzeigename darf Leerzeichen enthalten.

 Wenn Sie den Namen einer Eigenschaft in der DSL-Definition festlegen, wird sein Anzeigename lautet automatisch auf eine Kopie mit dem Namen festgelegt. Wenn Sie einen Groß-und Kleinschreibung Pascal-Namen, z. B. "FuelGauge" schreiben, wird der Anzeigename automatisch ein Leerzeichen enthalten: "Benzinanzeige". Allerdings können Sie den Anzeigenamen an explizit in einen anderen Wert festlegen.

 **Beschreibung**. Die Beschreibung einer Domäneneigenschaft wird an zwei Orten angezeigt:

-   Unten auf der das Fenster "Eigenschaften", wenn der Benutzer die Eigenschaft auswählt. Sie können es dem Benutzer erklären, was die Eigenschaft darstellt.

-   In der generierten Programmcode. Wenn Sie die Funktionen der Dokumentation zum Extrahieren der API-Dokumentation verwenden, wird es als die Beschreibung dieser Eigenschaft in der API angezeigt.

 **Kategorie**. Eine Kategorie ist eine Überschrift im Fenster Eigenschaften.

## <a name="exposing-style-features"></a>Style-Funktionen verfügbar zu machen
 Einige der dynamischen Funktionen von grafischen Elementen dargestellt werden kann oder *verfügbar gemacht werden* als Domäneneigenschaften. Eine Funktion, die auf diese Weise verfügbar gemacht wurde, kann vom Benutzer aktualisiert werden und kann weitere problemlos aktualisiert werden durch Programmcode.

 Mit der rechten Maustaste einer Shape-Klasse im DSL-Definition, zeigen Sie auf **verfügbare hinzufügen**, und wählen Sie dann auf eine Funktion.

 Formen können Sie verfügbar machen die **FillColor**, **OutlineColor**, **TextColor**, **OutlineDashStyle**,  **OutlineThickness** und **FillGradientMode** Eigenschaften. Sie können Connectors Bereitstellen der **Farbe**`,`**TextColor**, **DashStyle**, und **Stärke** Eigenschaften. In Diagrammen können Sie verfügbar machen die **FillColor** und **TextColor** Eigenschaften.

## <a name="forwarding-displaying-properties-of-related-elements"></a>Weiterleitung: Anzeigen von Eigenschaften verwandter Elemente
 Wenn der Benutzer Ihrer DSL ein Element in einem Modell auswählt, werden Eigenschaften des Elements im Eigenschaftenfenster angezeigt. Allerdings können Sie auch die Eigenschaften des angegebenen verwandte Elemente anzeigen. Dies ist nützlich, wenn Sie eine Gruppe von Elementen definiert haben, die zusammen funktioniert. Sie können z. B. ein Hauptelement und ein optionales-Plug-in-Element definieren. Wenn das Hauptelement mit einer Form zugeordnet ist, und die andere nicht der Fall ist, ist es hilfreich, um alle Eigenschaften anzuzeigen, als wären sie auf ein Element.

 Dieser Effekt heißt *Eigenschaft Weiterleitung*, und dies erfolgt automatisch im verschiedenen Fällen. In anderen Fällen können Sie die Eigenschaft, die Weiterleitung durch Definieren einer domänentypdeskriptor erreichen.

### <a name="default-property-forwarding-cases"></a>Weiterleitung von Standardszenarien-Eigenschaft
 Wenn der Benutzer eine Form oder -Connector oder ein Element im Explorer auswählt, werden die folgenden Eigenschaften im Fenster Eigenschaften angezeigt:

-   Die Domäneneigenschaften, die definiert sind, auf die Domänenklasse des Modellelements, einschließlich derjenigen, die in Basisklassen definiert sind. Eine Ausnahme ist die Domäneneigenschaften für die Sie festgelegt haben **kann durchsucht werden** zu `False`.

-   Die Namen von Elementen, die durch Beziehungen verknüpft sind, die eine Multiplizität von 0.. 1 aufweisen. Sie enthält eine praktische Methode optional sehen Elementen verknüpft, selbst wenn Sie keine connectorzuordnung für die Beziehung definiert haben.

-   Domäneneigenschaften der einbettenden Beziehung, die das Element ausgerichtet ist. Da es sich bei einbettende Beziehungen in der Regel nicht explizit angezeigt werden, können die Benutzer, deren Eigenschaften finden Sie unter.

-   Eigenschaften von Domänen, die für die ausgewählte Form oder den Connector definiert sind.

### <a name="adding-property-forwarding"></a>Hinzufügen von Eigenschaft-Weiterleitung
 Um eine Eigenschaft weiterzuleiten, definieren Sie einen Typdeskriptor für die Domäne an. Wenn Sie eine domänenbeziehung zwischen zwei Domänenklassen haben, können Sie einen Typdeskriptor für die Domäne, in der ersten Klasse auf den Wert einer Domäneneigenschaft in der zweiten Domänenklasse eine Domäneneigenschaft fest. Für, wenn Sie z. B. eine Beziehung zwischen einer **Buch** Domänenklasse und ein **Autor** Domänenklasse, können Sie eine domänentypdeskriptor stellen die **Namen** Eigenschaft eine Des Buchs **Autor** im Eigenschaftenfenster angezeigt werden, wenn der Benutzer das Buch auswählt.

> [!NOTE]
>  Eigenschaft Weiterleitung hat Auswirkungen auf die nur im Eigenschaftenfenster aus, wenn der Benutzer ein Modell bearbeitet werden. Es werden keine Domäneneigenschaft auf der empfangenden Klasse definiert. Wenn Sie die weitergeleiteten Domäneneigenschaft in andere Teile der DSL-Definition oder im Programmcode zugreifen möchten, müssen Sie das Element für die Weiterleitung zugreifen.

 Das folgende Verfahren wird davon ausgegangen, dass Sie eine DSL erstellt haben. Die ersten Schritten werden die Voraussetzungen zusammengefasst.

##### <a name="to-forward-a-property-from-another-element"></a>Eine Eigenschaft aus einem anderen Element weiterleiten

1.  Erstellen Sie eine [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Projektmappe mit mindestens zwei Klassen, die in diesem Beispiel aufgerufen werden, **Buch** und **Autor**. Es muss eine Beziehung entweder Art zwischen **Buch** und **Autor**.

     Die Multiplizität der Rolle "Quelle" (die Rolle auf die **Buch** Seite) muss 0.. 1 "oder" 1..1, sodass die einzelnen **Buch** verfügt über ein **Autor**.

2.  In **DSL-Explorer**, mit der rechten Maustaste die **Buch** Domänenklasse, und klicken Sie dann auf **neue für Hinzufügen neuer DomainTypeDescriptor**.

     Ein Knoten mit dem Namen **Pfade der benutzerdefinierte Eigenschaftsbeschreibungen** wird unter der **benutzerdefinierten Typdeskriptor** Knoten.

3.  Mit der rechten Maustaste die **benutzerdefinierten Typdeskriptor** Knoten, und klicken Sie dann auf **Hinzufügen eines neuen "PropertyPath"**.

     Ein neuen Eigenschaftenpfad angezeigt wird, unter dem **Pfade der benutzerdefinierte Eigenschaftsbeschreibungen** Knoten.

4.  Wählen Sie den neuen Eigenschaftenpfad, und klicken Sie in der **Eigenschaften** legen **Pfad zur Eigenschaft** auf den Pfad der entsprechenden Modellelement.

     Sie können den Pfad in einer Strukturansicht bearbeiten, indem Sie auf den Pfeil nach unten rechts von dieser Eigenschaft. Weitere Informationen zu Domänenpfade, finden Sie unter [Domänenpfadsyntax](../modeling/domain-path-syntax.md). Wenn Sie es bearbeitet haben, sollte der Pfad ähneln **BookReferencesAuthor.Author/! Autor**.

5.  Legen Sie **Eigenschaft** auf die **Namen** Domäneneigenschaft der **Autor**.

6.  Legen Sie **Anzeigename** zu **erstellen Namen**.

7.  Transformieren Sie alle Vorlagen, zu erstellen Sie, und führen Sie die DSL.

8.  In einem Modell ein Buch, Autor, und sie mit der verweisbeziehung zu verknüpfen. Wählen das Book-Element, und im Eigenschaftenfenster sollte Autorenname zusätzlich zu den Eigenschaften des Buchs angezeigt. Ändern Sie den Namen des Autors des verknüpften, oder verknüpfen Sie das Buch zu einem anderen Autor, und beachten Sie, dass der Name des Autors des Buchs ändert.

## <a name="custom-property-editors"></a>Benutzerdefinierte Eigenschaften-Editoren
 Das Eigenschaftenfenster stellt Bearbeitungsfunktionen für den Typ der Eigenschaft "Domain" jede entsprechende Standardeinstellung bereit. Z. B. für ein enumerierter Typ, der Benutzer sieht eine Dropdown-Liste, und der Benutzer kann für eine numerische Eigenschaft Ziffern eingeben. Dies gilt nur für die integrierten Typen. Wenn Sie einen externen Typ angeben, wird der Benutzer sein können, finden Sie unter der Eigenschaftswerte, aber nicht bearbeiten.

 Allerdings können Sie die folgenden Editoren und Typen angeben:

1.  Einem anderen Editor, der mit einem standard-Typ verwendet wird. Beispielsweise können Sie einen Datei-Pfad-Editor für eine Zeichenfolgeneigenschaft angeben.

2.  Einen externen Typ für die Eigenschaft "Domain" und einen Editor für sie.

3.  Ein .NET-Editor wie z. B. den Pfad-Editor, oder Sie können eine eigene benutzerdefinierte Eigenschaft-Editor erstellen.

     Eine Konvertierung zwischen einer externen und einem Typ wie z. B. Zeichenfolge, die über ein Standard-Editor verfügt.

 In einer DSL ein *externen Typ* ist jeder Typ, der nicht das einfache Typen (z. B. Boolean oder Int32) oder die Zeichenfolge.

#### <a name="to-define-a-domain-property-that-has-an-external-type"></a>Um eine Domäneneigenschaft zu definieren, die einen externen Typ aufweist.

1.  In **Projektmappen-Explorer**, fügen Sie einen Verweis auf die Assembly (DLL) mit dem externen Typ, in der **Dsl** Projekt.

     Die Assembly kann es sich um eine .NET-Assembly oder eine von Ihnen bereitgestellten Assembly sein.

2.  Fügen Sie den Typ der **Domänentypen** aufzulisten, es sei denn, Sie geschehen.

    1.  Öffnen Sie "DslDefinition.DSL", und klicken Sie in **DSL-Explorer**mit der rechten Maustaste auf den Stammknoten, und klicken Sie dann auf **neuen externen Typ hinzufügen**.

         Ein neuer Eintrag wird unter der **Domänentypen** Knoten.

        > [!WARNING]
        >  Das Menüelement ist nicht für den Stammknoten des DSL, die **Domänentypen** Knoten.

    2.  Legen Sie den Namen und den Namespace des neuen Typs im Eigenschaftenfenster an.

3.  Fügen Sie eine Domäneneigenschaft an eine Domänenklasse, auf die übliche Weise.

     Wählen Sie im Fenster Eigenschaften den externen Typ aus der Dropdown-Liste in der **Typ** Feld.

 In dieser Phase Benutzer können die Werte der Eigenschaft anzeigen, aber nicht bearbeiten. Die angezeigten Werte erhalten Sie vom der `ToString()` Funktion. Sie können Programmcode schreiben, die den Wert der Eigenschaft, z. B. in einem Befehlsfenster oder die Regel festlegt.

### <a name="setting-a-property-editor"></a>Festlegen eines Eigenschaften-Editors
 Fügen Sie der Domäne-Eigenschaft in der folgenden Form eine CLR-Attribut hinzu:

```csharp
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]

```

 Sie können das Attribut für eine Eigenschaft festlegen, mit der **benutzerdefiniertes Attribut** Eintrag im Fenster Eigenschaften.

 Der Typ des `AnEditor` aus dem im zweiten Parameter angegebenen Typ abgeleitet werden. Der zweite Parameter muss entweder <xref:System.Drawing.Design.UITypeEditor> oder <xref:System.ComponentModel.ComponentEditor>. Weitere Informationen finden Sie unter <xref:System.ComponentModel.EditorAttribute>.

 Sie können entweder einen eigenen Editor oder in einem Editor, die im angegebenen angeben der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], z. B. <xref:System.Windows.Forms.Design.FileNameEditor> oder <xref:System.Drawing.Design.ImageEditor>. Verwenden Sie z. B. das folgende Verfahren, um eine Eigenschaft verfügen, in der der Benutzer einen Dateinamen eingeben kann.

##### <a name="to-define-a-file-name-domain-property"></a>Definieren Sie eine Datei namens Domäneneigenschaft

1.  Fügen Sie eine Domäneneigenschaft an eine Domänenklasse in Ihrer DSL-Definition.

2.  Wählen Sie die neue Eigenschaft ein. In der **benutzerdefiniertes Attribut** Feld in das Fenster "Eigenschaften", geben Sie das folgende Attribut. Dieses Attribut bei der Eingabe, klicken Sie auf die Auslassungspunkte **[...]**  und geben Sie den Attributnamen und den Parametern getrennt:

    ```csharp
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3.  Behalten Sie die Standardeinstellung für den Typ der Domäneneigenschaft **Zeichenfolge**.

4.  Um den Editor zu testen, stellen Sie sicher, dass Benutzer die Dateinamen-Editor zum Bearbeiten Ihrer Eigenschaft "Domain" öffnen können.

    1.  Drücken Sie STRG + F5 oder F5. Öffnen Sie eine Testdatei in der Projektmappe debuggen. Erstellen Sie ein Element der Domänenklasse aus, und wählen Sie sie.

    2.  Wählen Sie im Fenster Eigenschaften die Eigenschaft "Domain". Das Feld "Wert" zeigt ein Auslassungszeichen **[...]** .

    3.  Klicken Sie auf die Auslassungspunkte. Ein Dialogfeld wird angezeigt. Wählen Sie eine Datei, und schließen Sie das Dialogfeld. Der Dateipfad ist jetzt der Wert der Domäneneigenschaft.

### <a name="defining-your-own-property-editor"></a>Definieren Ihre eigenen Eigenschaften-editor
 Sie können Ihren eigenen Editor definieren. Sie möchten diese Option, um dem Benutzer ermöglichen, einen Typ zu bearbeiten, den Sie definiert haben, oder um einen Standardtyp auf besondere Weise zu bearbeiten. Beispielsweise können Sie ermöglichen, den Benutzer zur Eingabe von einer Zeichenfolge, die eine Formel darstellt.

 Sie definieren einen Editor schreiben eine abgeleitete Klasse, von <xref:System.Drawing.Design.UITypeEditor>. Die Klasse muss außer Kraft setzen:

-   <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, mit dem Benutzer interagieren, und aktualisieren den Wert der Eigenschaft.

-   <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, um anzugeben, ob Ihr Editor wird ein Dialogfeld zu öffnen, oder geben Sie ein Dropdown-Menü.

 Sie können auch eine grafische Darstellung des Werts der Eigenschaft angeben, die im Eigenschaftenraster angezeigt werden. Zu diesem Zweck überschreiben `GetPaintValueSupported`, und `PaintValue`.  Weitere Informationen finden Sie unter <xref:System.Drawing.Design.UITypeEditor>.

> [!NOTE]
>  Fügen Sie den Code in einer separaten Codedatei in die **Dsl** Projekt.

 Zum Beispiel:

```csharp
internal class TextFileNameEditor : System.Windows.Forms.Design.FileNameEditor
{
  protected override void InitializeDialog(System.Windows.Forms.OpenFileDialog openFileDialog)
  {
    base.InitializeDialog(openFileDialog);
    openFileDialog.Filter = "Text files(*.txt)|*.txt|All files (*.*)|*.*";
    openFileDialog.Title = "Select a text file";
  }
}

```

 Um diesen Editor zu verwenden, legen die **benutzerdefiniertes Attribut** einer Domäneneigenschaft auf:

```csharp
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]

```

 Weitere Informationen finden Sie unter <xref:System.Drawing.Design.UITypeEditor>.

## <a name="providing-a-drop-down-list-of-values"></a>Bereitstellen einer Dropdownliste von Werten
 Sie können eine Liste von Werten für einen Benutzer zur Auswahl bereitstellen.

> [!NOTE]
>  Diese Technik bietet es sich um eine Liste von Werten, die zur Laufzeit ändern können. Wenn Sie eine Liste angeben, die nicht geändert wird, können Sie stattdessen einen enumerierten Typ mit dem Typ der Eigenschaft "Domain" Ihre mithilfe.

 Um eine Liste von Standardwerten zu definieren, fügen Sie für Ihre Domäneneigenschaft ein CLR-Attribut, das die folgende Form aufweist:

```csharp
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]

```

 Definieren Sie eine Klasse, die sich von <xref:System.ComponentModel.TypeConverter> ableitet. Fügen Sie den Code in einer separaten Datei in die **Dsl** Projekt. Zum Beispiel:

```csharp
/// <summary>
/// Type converter that provides a list of values
/// to be displayed in the property grid.
/// </summary>
/// <remarks>This type converter returns a list
/// of the names of all "ExampleElements" in the
/// current store.</remarks>
public class MyTypeConverter : System.ComponentModel.TypeConverter
{
  /// <summary>
  /// Return true to indicate that we return a list of values to choose from
  /// </summary>
  /// <param name="context"></param>
  public override bool GetStandardValuesSupported
    (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Returns true to indicate that the user has
  /// to select a value from the list
  /// </summary>
  /// <param name="context"></param>
  /// <returns>If we returned false, the user would
  /// be able to either select a value from
  /// the list or type in a value that is not in the list.</returns>
  public override bool GetStandardValuesExclusive
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Return a list of the values to display in the grid
  /// </summary>
  /// <param name="context"></param>
  /// <returns>A list of values the user can choose from</returns>
  public override StandardValuesCollection GetStandardValues
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    // Try to get a store from the current context
    // "context.Instance"  returns the element(s) that
    // are currently selected i.e. whose values are being
    // shown in the property grid.
    // Note that the user could have selected multiple objects,
    // in which case context.Instance will be an array.
    Store store = GetStore(context.Instance);

    List<string> values = new List<string>();

    if (store != null)
    {
      values.AddRange(store.ElementDirectory
        .FindElements<ExampleElement>()
        .Select<ExampleElement, string>(e =>
      {
        return e.Name;
      }));
    }
    return new StandardValuesCollection(values);
  }

  /// <summary>
  /// Attempts to get to a store from the currently selected object(s)
  /// in the property grid.
  /// </summary>
  private Store GetStore(object gridSelection)
  {
    // We assume that "instance" will either be a single model element, or
    // an array of model elements (if multiple items are selected).

    ModelElement currentElement = null;

    object[] objects = gridSelection as object[];
    if (objects != null && objects.Length > 0)
    {
      currentElement = objects[0] as ModelElement;
    }
    else
    {
        currentElement = gridSelection as ModelElement;
    }

    return (currentElement == null) ? null : currentElement.Store;
  }

}

```

## <a name="see-also"></a>Siehe auch

- [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)