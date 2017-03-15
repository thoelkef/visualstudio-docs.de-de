---
title: "Anpassen des Eigenschaftenfensters | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, Eigenschaftenfenster"
ms.assetid: b6658de5-4e85-4628-93b2-5cc12f63d25b
caps.latest.revision: 20
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 20
---
# Anpassen des Eigenschaftenfensters
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Darstellung und das Verhalten des Eigenschaftenfensters in einer domänenspezifischen Sprache \(DSL\) mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]anpassen.  In der DSL\-Definition definieren Sie Domäneneigenschaften für eine Domänenklasse.  Wenn Sie eine Instanz der Klasse in einem Diagramm oder im Modell Explorer aktivieren, wird jede Domäneneigenschaft im Eigenschaftenfenster aufgelistet.  Auf diese Weise können Sie die Werte von Domäneneigenschaften finden und bearbeiten, auch wenn Sie sie nicht zugeordnet haben, um Felder im Diagramm zu gestalten.  
  
## Titel, Beschreibungen und Kategorien  
 **Name und Anzeigename**.  In der Definition einer Domäneneigenschaft ist der Anzeigename für die Eigenschaft Name, der zur Laufzeit im Eigenschaftenfenster angezeigt wird.  Im Gegensatz dazu wird der Name verwendet, wenn Sie Programmcode schreiben, um die Eigenschaft zu aktualisieren.  Der Name muss ein richtiger alphanumerischer Name der CLR sein, doch der Anzeigename kann Leerzeichen enthalten.  
  
 Wenn Sie den Namen einer Eigenschaft in der DSL\-Definition, unter Angabe ihres Anzeigenamens automatisch an eine Kopie des Namens festgelegt werden.  Wenn Sie einen Pascal umkleideten Namen wie „FuelGauge“ schreiben, enthält der Name Leerzeichen automatisch ein: „Tankanzeige“.  Sie können jedoch den Anzeigenamen zu einem anderen Wert explizit festlegen.  
  
 **Beschreibung**.  Die Beschreibung einer Domäneneigenschaft wird an zwei Stellen:  
  
-   In dem unteren Rand des Eigenschaftenfensters, wenn der Benutzer die Eigenschaft aktiviert.  Sie können ihn verwenden, um den Benutzer zu berücksichtigen, welche Eigenschaft darstellt.  
  
-   Im generierten Programmcode.  Wenn Sie Funktionen verwenden, um die Dokumentation API\-Dokumentation zu extrahieren, wird sie als Beschreibung dieser Eigenschaft im API.  
  
 **Category**.  Eine Kategorie ist eine Überschrift im Eigenschaftenfenster angezeigt.  
  
## Verfügbarmachen Format\-Funktionen  
 Einige der dynamischen Funktionen der grafischen Elemente können als Domäneneigenschaften dargestellt werden und *verfügbar gemacht werden* .  Eine Funktion, die auf diese Weise verfügbar gemacht wurde, kann vom Benutzer aktualisiert werden und kann durch Programmcode problemlos aktualisiert werden.  
  
 Klicken Sie mit der rechten Maustaste auf eine Form Klasse in DSL\-Definition, zeigen Sie auf **Verfügbar gemacht hinzufügen**, und wählen Sie dann eine Funktion aus.  
  
 Auf Forms können Sie die **FillColor**, **OutlineColor**, **TextColor**, **OutlineDashStyle**, **OutlineThickness** und **FillGradientMode**\-Eigenschaften verfügbar machen.  Bei Verbindungen können Sie die Eigenschaften **Farbe**`,`**TextColor**, **DashStyle**und **Stärke** verfügbar machen.  In Diagrammen können Sie die **FillColor** und **TextColor**\-Eigenschaften verfügbar machen.  
  
## Routing: Eigenschaften von verwandten Elemente anzeigen  
 Wenn der Benutzer des DSL ein Element in einem Modell auswählen, werden die Eigenschaften dieses Elements im Eigenschaftenfenster angezeigt.  Sie können jedoch die Eigenschaften der angegebenen zugehörigen Elementen anzeigen.  Dies ist hilfreich, wenn Sie eine Gruppe von Elementen definiert haben, die zusammenarbeitet.  Zum Beispiel definiert haben Sie möglicherweise eine Hauptes Element und ein optionales Element. steckbares  Wenn das wichtigste Element in eine Form zugeordnet ist und das andere nicht der Fall ist, empfiehlt es sich, alle ihre Eigenschaften anzuzeigen, als ob es sich bei einem Element handeln.  
  
 Dieser Effekt ist *die weiterleitende*benannte Eigenschaft, und in einigen Fällen geschieht automatisch.  In anderen Fällen können Sie die Eigenschaft weiterleitend erzielen, indem Sie einen Domänen typdeskriptor definieren.  
  
### Standardeigenschaft, die Fälle weiterleitet  
 Wenn der Benutzer eine Form oder einen Konnektor oder ein Element im Projektmappen\-Explorer auswählt, werden die folgenden Eigenschaften im Eigenschaftenfenster angezeigt:  
  
-   Die Domäneneigenschaften, die auf der Domänenklasse des Modellelements definiert werden, einschließlich denen, die in der Basisklasse definiert sind.  Eine Ausnahme ist Domäneneigenschaften, für die Sie **Ist durchsuchbar** zu `False`festgelegt haben.  
  
-   Die Namen von Elementen, die durch Beziehungen verknüpft sind, die eine Multiplizität von 0..1 haben.  Dies bietet eine bequeme Möglichkeit des Sehens von optional verknüpften Elementen, auch wenn Sie keine Konnektor Zuordnung für die Beziehung definiert haben.  
  
-   Domäneneigenschaften des Einbettungs\-Verhältnisses, der das Element verwendet.  Da Beziehungen einbettend, i. d. R. nicht explizit angezeigt werden, kann dies den Benutzer ihre Eigenschaften angezeigt.  
  
-   Domäneneigenschaften, die auf der ausgewählten Form oder den Konnektor definiert sind.  
  
### Das Hinzufügen Eigenschaft\-Weiterleiten  
 Um eine Eigenschaft weitergeleitet werden, definieren Sie einen Domänen typdeskriptor.  Wenn Sie ein Domänen\-Verhältnis zwischen zwei Domänen Klassen verfügen, können Sie einen Domänen typdeskriptor verwenden, um eine Domäneneigenschaft in der ersten Klasse mit dem Wert einer Domäneneigenschaft in der zweiten Domänenklasse festzulegen.  Wenn Sie beispielsweise eine Beziehung zwischen einem Buch domänen Autoren einer Klasse und domänen Klasse verfügen, können Sie einen Domänen typdeskriptor verwenden, um die Name\-Eigenschaft vom Autor eines Buches im Eigenschaftenfenster angezeigt werden soll, wenn der Benutzer das Buch ausgewählt werden.  
  
> [!NOTE]
>  Das Eigenschaft weiterleiten wirkt sich nur auf das Eigenschaftenfenster, wenn der Benutzer ein Modell bearbeitet.  Sie definiert keine Domäneneigenschaft auf der empfangenden Klasse.  Wenn Sie die weitergeleitete Domäneneigenschaft in anderen Teilen der DSL\-Definition oder im Programmcode zugreifen möchten, müssen Sie das Weiterleitungs Element zugreifen.  
  
 Im folgenden Verfahren wird davon ausgegangen, dass Sie ein DSL erstellt haben.  Die ersten Schritte Word die erforderlichen Komponenten zusammen.  
  
##### So legen Sie eine Eigenschaft von einem anderen Element weiterleiten  
  
1.  Erstellen Sie eine [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Projektmappe, die mindestens zwei Klassen enthält, die in diesem Beispiel Book und Autor aufgerufen werden.  Es sollte eine Beziehung aus einem beliebigen geben, das zwischen Buch und Autor nett ist.  
  
     Die Multiplizität Rolle der Quelle \(die Rolle auf der Seite Buch oder 0..1\) sollte 1..1 sein, dass jedes Buch einen Autor verfügt.  
  
2.  In **DSL\-Explorer**mit der rechten Maustaste auf die Buch domänen Klasse und klicken Sie dann auf **Neuen DomainTypeDescriptor hinzufügen**.  
  
     Ein Knoten mit dem Namen **Pfade der benutzerdefinierten Eigenschaftendeskriptoren** wird unter dem Knoten **Benutzerdefinierter Typdeskriptor** .  
  
3.  **Benutzerdefinierter Typdeskriptor** der rechten Maustaste auf den Knoten, und klicken Sie anschließend auf **Neues PropertyPath hinzufügen**.  
  
     Ein neuer Eigenschaftenpfad wird unter dem Knoten **Pfade der benutzerdefinierten Eigenschaftendeskriptoren** .  
  
4.  Wählen Sie den neuen Eigenschaftenpfad, und legen Sie im Fenster **EigenschaftenPfad zu Eigenschaft** auf den Pfad des entsprechenden Modellelements aus.  
  
     Sie können den Pfad in einer Strukturansicht bearbeiten, indem Sie auf den nach unten zeigenden Pfeil rechts neben der Eigenschaft klicken.  Weitere Informationen über Domänen für finden Sie unter [Domänenpfadsyntax](../modeling/domain-path-syntax.md).  Wenn Sie es bearbeitet haben, sollte der Pfad **BookReferencesAuthor.Author\/\!Autor**ähneln.  
  
5.  Legen Sie **Eigenschaft** zur **Name** Domäneneigenschaft des Autors fest.  
  
6.  Legen Sie fest, dass **Anzeigename** Namen zu erstellen.  
  
7.  Transformieren Sie alle Vorlagen, und übergeben Sie das Build fehl. DSL  
  
8.  In einem Modell Diagramm erstellen Sie ein Buch, einen Autor, und verknüpfen Sie sie mit dem Bezugs\-Verhältnisses.  Wählen Sie im Buch " \- Element aus und legen Sie im Eigenschaftenfenster Autoren\-Namen sollten Sie zusätzlich zu den Eigenschaften des Buchs sehen.  Ändern Sie den Namen des verknüpften Autors, oder verknüpfen Sie das Buch zu einem anderen Entwickler, und beachten Sie, dass der Autoren\-Name eines Buches geändert wird.  
  
## Benutzerdefinierte Eigenschaft\-Editoren  
 Das Eigenschaftenfenster wird eine entsprechende Standardwert für den Typ Darstellung Bearbeiten jeder Domäneneigenschaft bereit.  Zum Beispiel für einen Enumerationstyp, wird der Benutzer eine Dropdownliste, und eine numerische Eigenschaft kann der Benutzer Ziffern eingegeben werden.  Dies gilt nur für die integrierten Datentypen.  Wenn Sie einen externen Typ angeben, kann der Benutzer die Werte der Eigenschaft anzeigen, aber nicht bearbeiten können.  
  
 Sie können jedoch die folgenden Editoren und Typen angeben:  
  
1.  Ein anderer Editor, der mit einem Standardwert verwendet wird.  Sie können beispielsweise einen Dateipfad des Editors für eine Zeichenfolgeneigenschaft angibt.  
  
2.  Ein externer Typ für die Domäneneigenschaft und ein Editor für sie.  
  
3.  Ein .NET\-Editor wie der Dateipfad des Editors erstellen, oder Sie können benutzerdefinierten Eigenschaften\-Editor besitzen.  
  
     Eine Konvertierung zwischen einem externen Typ und einem Typ wie etwa Zeichenfolge, die einen Standardeditor verfügt.  
  
 In einem DSL ist ein *externer Typ* jeder Typ, der keiner der einfachen Typen \(wie Boolean oder Int32\) oder der Zeichenfolge ist.  
  
#### So erstellen Sie eine Domäneneigenschaft definieren, die einen externen Typs  
  
1.  In **Projektmappen\-Explorer**fügen Sie einen Verweis auf die Assembly \(DLL\), die den externen Typ enthält, im **Dsl** Projekt hinzu.  
  
     Die Assembly kann eine .NET\-Assembly oder eine Assembly von Ihnen angegeben wird.  
  
2.  Fügen Sie den Typ der **Domänentypen** Liste hinzu, sofern Sie nicht bereits getan haben.  
  
    1.  Öffnen Sie DslDefinition.dsl, und **DSL\-Explorer**mit der rechten Maustaste auf den Stammknoten, und klicken Sie dann auf **Neuen externen Typ hinzufügen**.  
  
         Ein neuer Eintrag wird unter dem Knoten **Domänentypen** .  
  
        > [!WARNING]
        >  Das Menüelement befindet sich auf dem DSL\-Stammknoten, nicht der **Domänentypen** Knoten.  
  
    2.  Legen Sie den Namen und den Namespace des neuen Typs im Eigenschaftenfenster fest.  
  
3.  Fügen Sie eine Domäneneigenschaft eine Domänenklasse in der üblichen Weise hinzu.  
  
     Wählen Sie im Eigenschaftenfenster den externen Typ aus der Dropdownliste im Feld Typ aus.  
  
 Zu diesem Zeitpunkt können Benutzer die Werte der Eigenschaft anzeigen, aber nicht bearbeiten können.  Folgende Werte werden von der `ToString()`\-Funktion abgerufen.  Sie können Programmcode schreiben, der den Wert der Eigenschaft, z. B. in einem Befehl oder einer Regel festgelegt wird.  
  
### Festlegen eines Eigenschaften\-Editor  
 Fügen Sie ein CLR\-Attribut der Domäneneigenschaft in der folgenden Form:  
  
```  
[System.ComponentModel.Editor (  
   typeof(AnEditor),  
   typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 Sie können das Attribut für eine Eigenschaft festlegen, indem Sie den **Benutzerdefiniertes Attribut** Eintrag im Eigenschaftenfenster verwenden.  
  
 Der Typ der `AnEditor` muss von dem Typ abgeleitet werden, der im zweiten Parameter angegeben wird.  Der zweite Parameter sollte entweder <xref:System.Drawing.Design.UITypeEditor> oder <xref:System.ComponentModel.ComponentEditor>sein.  Weitere Informationen finden Sie unter <xref:System.ComponentModel.EditorAttribute>.  
  
 Sie können angeben, entweder Editor oder einem Editor besitzen, der in [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], wie <xref:System.Windows.Forms.Design.FileNameEditor> oder <xref:System.Drawing.Design.ImageEditor>angegeben wird.  Verwenden Sie beispielsweise die folgende Prozedur, um eine Eigenschaft zu verfügen, in der der Benutzer einen Dateinamen eingeben kann.  
  
##### So definieren Sie einen Dateinamen domäneneigenschaft  
  
1.  Fügen Sie eine Domäneneigenschaft eine Domänenklasse in der DSL\-Definition hinzu.  
  
2.  Wählen Sie die neue Eigenschaft aus.  Wählen Sie im Feld **Benutzerdefiniertes Attribut** Geben Sie im Eigenschaftenfenster das folgende Attribut hinzu.  Um dieses Attribut einzugeben, klicken Sie auf die Auslassungspunkte **\[...\]** und geben Sie dann den Attributnamen und den Parametern einzeln ein:  
  
    ```  
    [System.ComponentModel.Editor (  
       typeof(System.Windows.Forms.Design.FileNameEditor)  
       , typeof(System.Drawing.Design.UITypeEditor))]  
  
    ```  
  
3.  Lassen Sie den Typ der Domäneneigenschaft an der Standardeinstellung **Zeichenfolge**.  
  
4.  Um den Editor zu testen, überprüfen Sie, ob Benutzer den Dateinamen des Editors öffnen können, um die Domäneneigenschaft zu bearbeiten.  
  
    1.  Drücken Sie F5 oder STRG\+F5.  In der Projektmappe Debuggen öffnen Sie eine Testdatei.  Erstellen Sie ein Element der Domänenklasse und wählen Sie es aus.  
  
    2.  Wählen Sie im Eigenschaftenfenster die Domäneneigenschaft aus.  Im Feld Wert zeigt Auslassungspunkte **\[...\]**an.  
  
    3.  Klicken Sie auf die Ellipse.  Ein Dateidialogfeld angezeigt wird.  Wählen Sie eine Datei aus, und schließen Sie das Dialogfeld.  Der Dateipfad kann jetzt der Wert der Domäneneigenschaft.  
  
### Definieren Eigenschaften\-Editor besitzen  
 Sie können definieren, Editor besitzen.  Sie können so vorgehen, um dem Benutzer ein zuzugestehen, um einen Typ zu bearbeiten, die Sie definiert haben, ein standardmäßiger oder Bearbeiten auf eine besondere Weise.  Sie können z. B. dem Benutzer ermöglichen, eine Zeichenfolge einzugeben, die eine Formel enthält.  
  
 Sie definieren einen Editor, indem Sie eine Klasse erstellen, die von <xref:System.Drawing.Design.UITypeEditor>abgeleitet ist.  Die Klasse muss überschrieben werden:  
  
-   <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, mit dem Benutzer interagieren und den Eigenschaftswert aktualisiert werden.  
  
-   <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, die angeben, ob der Editor ein Dialogfeld geöffnet oder ein Dropdownmenü bereitstellt.  
  
 Sie können eine grafische Darstellung des Werts der Eigenschaft bereitstellen, der im Eigenschaftenraster angezeigt wird.  Klicken Sie hierzu `PaintValue`und `GetPaintValueSupported`Überschreibung ausführen.  Weitere Informationen finden Sie unter <xref:System.Drawing.Design.UITypeEditor>.  
  
> [!NOTE]
>  Fügen Sie den Code in einer separaten Codedatei im **Dsl** Projekt hinzu.  
  
 Beispiele:  
  
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
  
 Um den Editor zu verwenden, legen Sie **Benutzerdefiniertes Attribut** einer Domäneneigenschaft fest:  
  
```  
[System.ComponentModel.Editor (  
   typeof(MyNamespace.TextFileNameEditor)  
   , typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 Weitere Informationen finden Sie unter <xref:System.Drawing.Design.UITypeEditor>.  
  
## Bereitstellen einer Dropdownliste von Werten  
 Sie können eine Liste von Werten bereitstellen, damit ein Benutzer auswählt.  
  
> [!NOTE]
>  Diese Technik stellt eine Liste von Werten, die zur Laufzeit ändern können.  Wenn Sie eine Liste bereitstellen möchten, die nicht ändert, sollten Sie einen Enumerationstyp als Typ der Domäneneigenschaft stattdessen zu verwenden.  
  
 Um eine Liste von Standardwerten zu definieren, fügen Sie der Domäneneigenschaft ein CLR\-Attribut hinzu, das das folgende Format aufweist:  
  
```  
[System.ComponentModel.TypeConverter   
(typeof(MyTypeConverter))]  
  
```  
  
 Definieren Sie eine Klasse, die sich von <xref:System.ComponentModel.TypeConverter> ableitet.  Fügen Sie den Code in einer separaten Datei im **Dsl** Projekt hinzu.  Beispiele:  
  
```c#  
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
  
## Siehe auch  
 [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)