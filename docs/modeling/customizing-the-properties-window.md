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
ms.openlocfilehash: 7020d3f49d5a693d2b64891c089138be4c073115
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31953991"
---
# <a name="customizing-the-properties-window"></a>Anpassen des Eigenschaftenfensters
Sie können das Aussehen und Verhalten des Eigenschaftenfensters in Ihrer domänenspezifische Sprache (DSL) anpassen, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In der DSL-Definition definieren Sie Domäneneigenschaften für jede Domänenklasse. Wenn Sie eine Instanz der Klasse in einem Diagramm oder im Modell-Explorer auswählen, wird jeder Eigenschaft "Domain" standardmäßig im Eigenschaftenfenster aufgeführt. Dadurch sehen und bearbeiten die Werte der Eigenschaften von Domänen, auch wenn Sie keine Form von Feldern im Diagramm zugeordnet haben.

## <a name="names-descriptions-and-categories"></a>Namen, Beschreibungen und Kategorien
 **Namen und Anzeigenamen**. In der Definition einer Eigenschaft "Domain" ist der Anzeigename der Eigenschaft den Namen, der zur Laufzeit im Eigenschaftenfenster angezeigt wird. Im Gegensatz dazu, wird der Name verwendet, wenn Sie Programmcode so aktualisieren Sie die Eigenschaft schreiben. Der Name muss eine richtige alphanumerische CLR-Name sein, aber der Anzeigename kann Leerzeichen enthalten.

 Wenn Sie den Namen einer Eigenschaft in der DSL-Definition festlegen, wird ihr Anzeigename angegeben automatisch auf eine Kopie des Namens festgelegt. Wenn Sie einen Kleinschreibung Pascal-Namen, z. B. "FuelGauge" schreiben, der Anzeigename automatisch ein Leerzeichen enthalten: "Treibstoff Messgerät". Allerdings können Sie den Anzeigenamen explizit in einen anderen Wert festlegen.

 **Beschreibung**. Die Beschreibung der Eigenschaft "Domain" eine tritt an zwei Stellen:

-   Unten im Eigenschaftenfenster, wenn der Benutzer die Eigenschaft auswählt. Sie können es dem Benutzer erklären, was die Eigenschaft darstellt.

-   In der generierten Programmcode. Wenn Sie die Dokumentation-Funktionen verwenden, um API-Dokumentation zu extrahieren, erscheint es als Beschreibung dieser Eigenschaft in der API.

 **Kategorie**. Eine Kategorie ist eine Überschrift im Fenster Eigenschaften.

## <a name="exposing-style-features"></a>Verfügbarmachen von Stil-Funktionen
 Einige der dynamischen Funktionen von grafischen Elementen dargestellt werden kann oder *verfügbar gemachten* als Domäneneigenschaften. Eine Funktion, die auf diese Weise verfügbar gemacht wurde, kann vom Benutzer aktualisiert werden und kann weitere problemlos aktualisiert werden Programmcode.

 Mit der rechten Maustaste in einer Shape-Klasse in der DSL-Definition, zeigen Sie auf **hinzufügen verfügbar gemachten**, und wählen Sie dann eine Funktion.

 Formen Sie verfügbar machen die **FillColor**, **OutlineColor**, **TextColor**, **OutlineDashStyle**,  **OutlineThickness** und **FillGradientMode** Eigenschaften. Connectors können Sie verfügbar machen die **Farbe**`,`**TextColor**, **DashStyle**, und **Stärke** Eigenschaften. In Diagrammen können Sie verfügbar machen die **FillColor** und **TextColor** Eigenschaften.

## <a name="forwarding-displaying-properties-of-related-elements"></a>Weiterleitung: Anzeigen von Eigenschaften von verknüpften Elementen
 Wenn der Benutzer von der DSL ein Element in einem Modell auswählt, werden die Eigenschaften des Elements im Eigenschaftenfenster angezeigt. Allerdings können Sie auch die Eigenschaften des angegebenen verknüpften Elementen anzeigen. Dies ist hilfreich, wenn Sie eine Gruppe von Elementen definiert haben, die zusammenarbeitet. Beispielsweise können Sie eine main-Element und ein optionales-Plug-in-Element definieren. Wenn das Hauptelement zu einer Form zugeordnet ist, und die andere nicht der Fall ist, ist es hilfreich, alle ihre Eigenschaften anzuzeigen, als wären sie auf ein Element.

 Dieser Effekt ist mit dem Namen *Eigenschaft Weiterleitung*,. er geschieht automatisch im verschiedenen Fällen. In anderen Fällen können Sie die Eigenschaft, die durch die Definition eines Domäne Typdeskriptors Weiterleitung erzielen.

### <a name="default-property-forwarding-cases"></a>Standard-Eigenschaft Weiterleitung Fällen
 Wenn der Benutzer eine Form oder Connector oder von einem Element im Explorer auswählt, werden die folgenden Eigenschaften im Eigenschaftenfenster angezeigt:

-   Definierten Domäneneigenschaften werden in der Domänenklasse des Modellelements, einschließlich derer, die in Basisklassen definiert sind. Eine Ausnahme ist die Domäneneigenschaften für die Sie festgelegt haben **durchsuchbar ist** auf `False`.

-   Die Namen von Elementen, die durch Beziehungen verknüpft sind, die eine Multiplizität von 0.. 1 aufweisen. Dies bietet eine praktische Methode optional sehen Elemente verknüpft, selbst wenn Sie eine Connector-Zuordnung für die Beziehung nicht definiert haben.

-   Domäneneigenschaften das Einbetten von Beziehung, die das Element ausgerichtet ist. Da Einbetten von Beziehungen in der Regel nicht explizit angezeigt werden, können die Benutzer ihre Eigenschaften anzuzeigen.

-   Domäneneigenschaften fest, die auf der ausgewählten Form oder den Verbinder definiert sind.

### <a name="adding-property-forwarding"></a>Eigenschaft Weiterleitung hinzufügen
 Um eine Eigenschaft weiterzuleiten, definieren Sie einen Domäne Typdeskriptor. Wenn Sie eine domänenbeziehung zwischen zwei Domänenklassen verfügen, können Sie einen Typdeskriptor Domäne verwenden, in der ersten Klasse auf den Wert der Eigenschaft "Domain" in der zweiten Domänenklasse eine Eigenschaft "Domain" festgelegt. Angenommen, Sie haben eine Beziehung zwischen einer **Buch** Domänenklasse und ein **Autor** Domänenklasse, können Sie einen Domäne Typdeskriptor stellen die **Namen** Eigenschaft ein Des Buchs **Autor** im Eigenschaftenfenster angezeigt werden, wenn der Benutzer das Buch auswählt.

> [!NOTE]
>  Eigenschaft Weiterleitung wirkt sich auf die nur im Eigenschaftenfenster aus, wenn der Benutzer ein Modell bearbeitet werden. Es werden keine Eigenschaft "Domain" für die empfangende Klasse definiert. Wenn Sie die Eigenschaft "weitergeleitete Domain" in anderen Teilen der DSL-Definition oder im Programmcode zugreifen möchten, müssen Sie die Weiterleitung Element zugreifen.

 Das folgende Verfahren wird davon ausgegangen, dass Sie eine DSL erstellt haben. Die ersten Schritte fassen zusammen, die erforderlichen Komponenten.

##### <a name="to-forward-a-property-from-another-element"></a>Eine Eigenschaft aus einem anderen Element weiterleiten

1.  Erstellen einer [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Lösung, die über mindestens zwei Klassen enthält, die in diesem Beispiel bezeichnet werden **Buch** und **Autor**. Es muss eine Beziehung entweder Art zwischen **Buch** und **Autor**.

     Die Multiplizität der Quellrolle (der Rolle in der **Buch** Seite) muss 0.. 1 oder 1..1, sodass jedes **Buch** verfügt über einen **Autor**.

2.  In **Explorer für DSL**, mit der rechten Maustaste die **Buch** Domänenklasse, und klicken Sie dann auf **Hinzufügen neuer DomainTypeDescriptor**.

     Ein Knoten mit dem Namen **Pfade der benutzerdefinierte Eigenschaftsbeschreibungen** unterhalb der **benutzerdefinierten Typdeskriptors** Knoten.

3.  Mit der rechten Maustaste die **benutzerdefinierten Typdeskriptors** Knoten, und klicken Sie dann auf **Hinzufügen eines neuen "PropertyPath"**.

     Ein neuen Eigenschaftenpfad angezeigt wird, unter dem **Pfade von Eigenschaftendeskriptoren benutzerdefinierte** Knoten.

4.  Wählen Sie den neuen Eigenschaftenpfad, und klicken Sie in der **Eigenschaften** fest **Pfad zur Eigenschaft** auf den Pfad des entsprechenden Modellelements.

     Sie können den Pfad in einer Strukturansicht bearbeiten, indem Sie auf den Pfeil nach unten rechts von dieser Eigenschaft. Weitere Informationen zu Domäne Pfaden finden Sie unter [Domäne Pfadsyntax](../modeling/domain-path-syntax.md). Wenn Sie es bearbeitet haben, sollte der Pfad ähneln **BookReferencesAuthor.Author/! Autor**.

5.  Legen Sie **Eigenschaft** auf die **Namen** Eigenschaft "Domain" des **Autor**.

6.  Legen Sie **Anzeigename** auf **erstellen Namen**.

7.  Transformieren aller Vorlagen erstellen und Ausführen der DSL.

8.  Erstellen Sie in einem Modelldiagramm ein Buch, ein Autor und verknüpfen Sie sie mithilfe der verweisbeziehung. Wählen das Book-Element, und im Eigenschaftenfenster sollte Sie zusätzlich zu den Eigenschaften des Buchs Name des Autors angezeigt. Ändern Sie den Namen des Autors des verknüpften, oder verknüpfen Sie das Buch mit der Autor eines anderen, und beachten Sie, dass der Name des Autors des Buchs ändert.

## <a name="custom-property-editors"></a>Benutzerdefinierte Eigenschaften-Editoren
 Eigenschaftenfenster bietet Ihnen Bearbeitungsfunktionen für den Typ der Eigenschaft "Domain" jede entsprechende Standardeinstellung. Z. B. für ein enumerierter Typ, der Benutzer sieht eine Dropdown-Liste, und der Benutzer kann für eine numerische Eigenschaft Ziffern eingeben. Dies gilt nur für die integrierten Typen. Wenn Sie einen externen Typ angeben, wird der Benutzer sein, finden Sie unter der Eigenschaftswerte, jedoch nicht bearbeiten.

 Allerdings können Sie die folgenden Editoren und Typen angeben:

1.  Einen anderen Editor, der mit einem standard-Typ verwendet wird. Sie können z. B. einen Pfad zum Datei-Editor für eine Zeichenfolgeneigenschaft angeben.

2.  Einen externen Typ für die Eigenschaft "Domain" und einen Editor dafür.

3.  Ein .NET-Editor wie Editor die Datei-Pfad oder Sie können eine eigene benutzerdefinierte Eigenschaft-Editor erstellen.

     Eine Konvertierung zwischen einer externen und einem Typ wie z. B. die Zeichenfolge, die einen Standard-Editor verfügt.

 Eine DSL ein *externen Typ* ist jeder Typ, der nicht der einfachen Typen (z. B. Boolean oder Int32) oder eine Zeichenfolge ist.

#### <a name="to-define-a-domain-property-that-has-an-external-type"></a>Um eine Eigenschaft "Domain" zu definieren, die über einen externen Typ verfügt

1.  In **Projektmappen-Explorer**, fügen Sie einen Verweis auf die Assembly (DLL), die in den externen Typ enthält die **Dsl** Projekt.

     Die Assembly kann eine .NET Framework-Assembly oder einer Assembly, die von Ihnen angegeben werden.

2.  Fügen Sie den Typ der **Domänentypen** aufzulisten, es sei denn, Sie dies getan haben.

    1.  DslDefinition.dsl, öffnen und im **Explorer für DSL**mit der rechten Maustaste auf den Stammknoten, und klicken Sie dann auf **Hinzufügen neuer externer Typ**.

         Ein neuer Eintrag wird unter der **Domänentypen** Knoten.

        > [!WARNING]
        >  Das Menüelement ist nicht für den Stammknoten DSL der **Domänentypen** Knoten.

    2.  Legen Sie den Namen und den Namespace des neuen Typs im Eigenschaftenfenster an.

3.  Fügen Sie eine Eigenschaft "Domain" zu einer Domänenklasse, auf die übliche Weise.

     Wählen Sie im Fenster Eigenschaften den externen Typ aus der Dropdown-Liste in die **Typ** Feld.

 In diesem Stadium Benutzer können die Werte der Eigenschaft anzeigen, aber nicht bearbeiten. Die angezeigten Werte werden abgerufen, von der `ToString()` Funktion. Programmcode geschrieben, die den Wert der Eigenschaft, z. B. in einem Befehl oder die Regel festlegt.

### <a name="setting-a-property-editor"></a>Festlegen eines Eigenschaften-Editors
 Fügen Sie eine CLR-Attributen auf die Eigenschaft "Domain", in der folgenden Form:

```
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]

```

 Sie können das Attribut für eine Eigenschaft festlegen, mit der **benutzerdefiniertes Attribut** Eintrag im Fenster Eigenschaften.

 Der Typ des `AnEditor` muss von dem im zweiten Parameter angegebenen Typ abgeleitet werden. Der zweite Parameter muss entweder <xref:System.Drawing.Design.UITypeEditor> oder <xref:System.ComponentModel.ComponentEditor>. Weitere Informationen finden Sie unter <xref:System.ComponentModel.EditorAttribute>.

 Sie können entweder einen eigenen Editor oder in einem Editor, der im angegebenen angeben der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], wie z. B. <xref:System.Windows.Forms.Design.FileNameEditor> oder <xref:System.Drawing.Design.ImageEditor>. Verwenden Sie z. B. das folgende Verfahren, um eine Eigenschaft aufweisen, in der der Benutzer einen Dateinamen eingeben kann.

##### <a name="to-define-a-file-name-domain-property"></a>Um eine Domäne Dateinameneigenschaft zu definieren.

1.  Fügen Sie eine Eigenschaft "Domain" zu einer Domänenklasse in der DSL-Definition hinzu.

2.  Wählen Sie die neue Eigenschaft ein. In der **benutzerdefiniertes Attribut** Feld im Eigenschaftenfenster, geben Sie das folgende Attribut. Wenn dieses Attribut eingeben möchten, klicken Sie auf die Auslassungspunkte **[...]**  , und geben Sie den Attributnamen und den Parametern getrennt:

    ```
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3.  Behalten Sie die Standardeinstellung für den Typ der Eigenschaft "Domain" die **Zeichenfolge**.

4.  Um den Editor zu testen, stellen Sie sicher, dass Benutzer die Dateinamen-Editor zum Bearbeiten der Eigenschaft "Domain" öffnen können.

    1.  Drücken Sie STRG + F5 oder F5. Öffnen Sie eine Testdatei in der Lösung Debuggen. Erstellen Sie ein Element der Domänenklasse, und wählen Sie sie.

    2.  Wählen Sie im Fenster Eigenschaften die Eigenschaft "Domain". Das Feld "Wert" zeigt ein Auslassungszeichen **[...]** .

    3.  Klicken Sie auf die Auslassungspunkte. Ein Dialogfeld wird angezeigt. Wählen Sie eine Datei, und schließen Sie das Dialogfeld zu. Der Dateipfad ist jetzt den Wert der Eigenschaft "Domain".

### <a name="defining-your-own-property-editor"></a>Definieren Ihre eigenen Eigenschaften-editor
 Sie können Ihren eigenen Editor definieren. Sie würden Sie tun, damit der Benutzer kann entweder einen Typ zu bearbeiten, den Sie definiert haben, oder einen standard-Datentyp auf besondere Weise zu bearbeiten. Sie können z. B. ermöglichen, dass den Benutzer die Eingabe eine Zeichenfolge, die eine Formel darstellt.

 Sie definieren einen Editor, indem schreiben eine Klasse, die abgeleitet ist <xref:System.Drawing.Design.UITypeEditor>. Die Klasse muss außer Kraft setzen:

-   <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, um mit dem Benutzer interagieren und aktualisieren den Wert der Eigenschaft.

-   <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, um anzugeben, ob der Editor wird ein Dialogfeld zu öffnen, oder geben Sie ein Dropdown-Menü.

 Sie können auch eine grafische Darstellung des Werts der Eigenschaft angeben, die im Eigenschaftenraster angezeigt werden. Zu diesem Zweck überschreiben `GetPaintValueSupported`, und `PaintValue`.  Weitere Informationen finden Sie unter <xref:System.Drawing.Design.UITypeEditor>.

> [!NOTE]
>  Fügen Sie den Code in einer separaten Codedatei in der **Dsl** Projekt.

 Zum Beispiel:

```
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

 Um diesen Editor verwenden, legen die **benutzerdefiniertes Attribut** der Eigenschaft "Domain" an:

```
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]

```

 Weitere Informationen finden Sie unter <xref:System.Drawing.Design.UITypeEditor>.

## <a name="providing-a-drop-down-list-of-values"></a>Bereitstellen einer Dropdown-Liste von Werten
 Sie können eine Liste von Werten für einen Benutzer zur Auswahl bereitstellen.

> [!NOTE]
>  Diese Technik stellt eine Liste mit Werten, die zur Laufzeit ändern können. Wenn Sie eine Liste bereitstellen, die nicht ändern möchten, erwägen Sie stattdessen einen enumerierten Typ mit dem Typ der Eigenschaft "Domain" Ihre Verwendung.

 Um eine Liste von Standardwerten zu definieren, fügen Sie auf die Eigenschaft "Domain" ein CLR-Attribut, das die folgende Form aufweist:

```
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