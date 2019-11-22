---
title: 'UML Class Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.logicalclassdiagram.overrideoperationsdialog
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: 94dbfd55-b300-4b49-9049-0831ed849486
caps.latest.revision: 56
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c170827825d772f4d97cd22f0b5754232e8d2257
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297290"
---
# <a name="uml-class-diagrams-guidelines"></a>UML-Klassendiagramme: Richtlinien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can use a *UML class diagram* to describe data types and their relationships separately from their implementation. Das Diagramm wird verwendet, um die Konzentration auf die logischen Aspekte der Klassen zu leiten, anstatt auf ihre Implementierung.

 To create a UML class diagram, on the **Architecture** menu, choose **New UML Diagram or Layer Diagram**.

 Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> In diesem Thema geht es um UML-Klassendiagramme. Es gibt noch eine andere Art von Klassendiagramm, das erstellt und verwendet wird, um Programmcode visuell darzustellen. See [Designing and Viewing Classes and Types](https://go.microsoft.com/fwlink/?LinkId=142231).

## <a name="Using"></a> Using UML Class Diagrams
 Sie können ein UML-Klassendiagramm für viele verschiedene Zwecke verwenden:

- Zum Bereitstellen einer von der Implementierung unabhängigen Beschreibung der Typen, die in einem System verwendet und zwischen Komponenten übergeben werden.

     Der Typ "Meal Order" kann z. B. in .NET-Code auf Geschäftsebene, in XML auf den Schnittstellen zwischen Komponenten, in SQL in der Datenbank und in HTML auf der Benutzeroberfläche implementiert werden. Obwohl diese Implementierungen sich in ihren Details unterscheiden, ist die Beziehung zwischen "Meal Order" und anderen Typen wie "Menu" und "Payment" immer gleich. Das UML-Klassendiagramm macht es möglich, diese Beziehungen getrennt von den Implementierungen darzustellen.

- Zum Verdeutlichen des Glossars mit den Begriffen, die für die Kommunikation zwischen der Anwendung und ihren Benutzern und in Beschreibungen der Benutzeranforderungen verwendet werden. See [Model user requirements](../modeling/model-user-requirements.md).

     Nehmen wir z. B. die Benutzertextabschnitte, Anwendungsfälle oder anderen Anforderungsbeschreibungen einer Restaurantanwendung. Diese Beschreibungen enthalten zum Beispiel Begriffe wie Menu (Speisekarte), Order (Bestellung), Meal (Gericht), Price (Preis), Payment (Bezahlung) usw. Sie können ein UML-Klassendiagramm zeichnen, das die Beziehungen zwischen diesen Begriffen definiert. Auf diese Weise wird das Risiko von Inkonsistenzen in den Anforderungsbeschreibungen, in der Benutzeroberfläche und in den Hilfedokumenten reduziert.

### <a name="relationship-to-other-diagrams"></a>Beziehung zu anderen Diagrammen
 Ein UML-Klassendiagramm wird normalerweise zusammen mit anderen Modellierungsdiagrammen gezeichnet, um Beschreibungen der verwendeten Typen bereitzustellen. Die physische Darstellung der Typen wird in keinem der Diagramme wiedergegeben.

 Aktivitätsdiagramm

 Typ der Daten, der über einen Objektknoten übergeben wird.

 Typen von Eingabe- und Ausgabepins und Aktivitätsparameterknoten.

 See [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).

 Sequenzdiagramm

 Typen von Parametern und Rückgabewerte von Meldungen.

 Typen der Lebenslinien. Die Klasse einer Lebenslinie sollte Vorgänge für alle Meldungen enthalten, die empfangen werden können.

 See [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

 Komponentendiagramm

 Komponentenschnittstellen, unter denen die Vorgänge aufgeführt sind.

 See [UML Component Diagrams: Guidelines](../modeling/uml-component-diagrams-guidelines.md).

 Anwendungsfalldiagramm

 Typen, die in Beschreibungen der Ziele und Schritte eines Anwendungsfalls erwähnt werden.

 See [UML Use Case Diagrams: Guidelines](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="BasicSteps"></a> Basic Steps for Drawing Class Diagrams
 For reference information about the elements on UML class diagrams, see [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md).

> [!NOTE]
> Detailed steps for creating any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-uml-class-diagram"></a>So erstellen Sie ein UML-Klassendiagramm

1. On the **Architecture** menu, choose **New UML or Layer Diagram**.

2. Under **Templates**, choose **UML Class Diagram**.

3. Benennen Sie das Diagramm.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a New Modeling Project**, and then choose **OK**.

     A new class diagram appears with the **UMLClass Diagram** Toolbox. Die Toolbox enthält die erforderlichen Elemente und Beziehungen.

#### <a name="to-draw-a-uml-class-diagram"></a>So zeichnen Sie ein UML-Klassendiagramm

1. To create a type, choose the **Class**, **Interface** or **Enumeration** tool on the Toolbox, and then click a blank part of the diagram. (Wenn die Toolbox nicht angezeigt wird, drücken Sie STRG+ALT+X.)

2. To add attributes or operations to the types, or literals to an enumeration, choose the **Attributes**, **Operations** or **Literals** heading in the type, and press ENTER.

     Sie können eine Signatur schreiben, z. B. `f(x:Boolean):Integer`. See [Attributes and Operations](#AttributesAndOperations).

     Um schnell mehrere Elemente hinzuzufügen, drücken Sie am Ende jedes Elements zweimal die EINGABETASTE. Sie können in der Liste mit den PFEILTASTEN nach oben und unten navigieren.

3. Um einen Typ zu erweitern oder zu reduzieren, wählen Sie oben links das Chevronsymbol aus. You can also expand and collapse the **Attributes** and **Operations** section of a class or interface.

4. Um zwischen den Typen Zuordnungs-, Vererbungs- oder Abhängigkeitslinks zu zeichnen, klicken Sie auf das entsprechende Tool, auf den Quelltyp und dann auf den Zieltyp.

5. To create types in a package, create a package using the **Package** tool, and then create new types and packages within the package. Sie können auch den Kopierbefehl verwenden, um Typen zu kopieren und in ein Paket einzufügen.

6. Jedes Diagramm ist eine Ansicht eines Modells, das im gleichen Projekt auch von anderen Diagrammen genutzt wird. To see a tree view of the complete model, choose **View**, **Other Windows**, **UML Model Explorer**.

## <a name="UsingTypes"></a> Using Classes, Interfaces, and Enumerations
 In der Toolbox sind drei Standardarten von Klassifizierern verfügbar. These are referred to as *types* throughout this document.

 ![A class, an enumeration, and an interface](../modeling/media/uml-classguidetypes.png "UML_ClassGuideTypes")

- Use **Classes** (1) to represent data or object types for most purposes.

- Use **Interfaces** (2) in a context where you have to differentiate between pure interfaces and concrete classes that have internal implementations. Dieser Unterschied ist nützlich, wenn der Zweck des Diagramms darin besteht, eine Softwareimplementierung zu beschreiben. Er ist weniger nützlich, wenn Sie passive Daten modellieren oder wenn Sie Konzepte definieren, die zum Beschreiben der Benutzeranforderungen verwendet werden.

- Use an **Enumeration** (3) to represent a type that has a limited number of literal values, for example `Stop` and `Go`.

  - Fügen Sie die Literalwerte der Enumeration hinzu. Geben Sie jedem Wert einen anderen Namen.

  - Sie können bei Bedarf auch einen numerischen Wert für jeden Literalwert angeben. Open the shortcut menu for the literal in the enumeration, choose **Properties**, and then type a number in the **Value** field in the **Properties** window.

  Geben Sie jedem Typ einen eindeutigen Namen.

### <a name="getting-types-from-other-diagrams"></a>Abrufen von Typen aus anderen Diagrammen
 Sie können festlegen, dass Typen aus einem anderen Diagramm in Ihrem UML-Klassendiagramm angezeigt werden.

 UML-Klassendiagramm

 Sie können festlegen, dass eine Klasse in mehr als einem UML-Klassendiagramm angezeigt wird. When you have created a class on one diagram, drag the class from **UML Model Explorer** onto the other diagram.

 Dies ist nützlich, wenn Sie erreichen möchten, dass der Schwerpunkt in jedem Diagramm auf einer bestimmten Gruppe von Beziehungen liegt.

 Beispielsweise können Sie die Zuordnungen zwischen einer Essensbestellung (Meal Order) und der Speisekarte (Menu) des Restaurants in einem Diagramm und die Zuordnungen zwischen Essensbestellung und Bezahlung (Payment) in einem anderen Diagramm anzeigen.

 Komponentendiagramm

 If you have defined interfaces on the components in a component diagram, you can drag an interface from **UML Model Explorer** onto the class diagram. Im Klassendiagramm können Sie die Methoden definieren, die in der Schnittstelle enthalten sind.

 See [UML Component Diagrams: Guidelines](../modeling/uml-component-diagrams-guidelines.md).

 UML-Sequenzdiagramm

 You can create classes and interfaces from lifelines in a sequence diagram, and then drag the class from **UML Model Explorer** to a UML class diagram. Jede Lebenslinie in einem Sequenzdiagramm stellt eine Instanz eines Objekts, einer Komponente oder eines Akteurs dar.

 To create a class from a lifeline, open the shortcut menu for the lifeline, and then choose **Create Class** or **Create Interface**. See [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

## <a name="AttributesAndOperations"></a> Attributes and Operations
 Ein Attribut (4) ist ein benannter Wert, über den jede Instanz eines Typs verfügen kann. Das Zugreifen auf ein Attribut führt nicht dazu, dass der Zustand der Instanz geändert wird.

 Ein Vorgang (5) ist eine Methode oder Funktion, die Instanzen des Typs ausführen kann. Dabei kann ein Wert zurückgegeben werden. If its **isQuery** property is true, it cannot change the state of the instance.

 To add an attribute or operation to a type, open the shortcut menu for the type, choose **Add**, and then choose **Attribute** or **Operation**.

 To see its properties, open the shortcut menu for the attribute or operation, and then choose **Properties**. The properties appear in the **Properties** window.

 To see the properties of an operation's parameters, choose <strong>[…]</strong>in the **Parameters** property. Ein neues Eigenschaftendialogfeld wird angezeigt.

 Ausführliche Informationen zu allen Eigenschaften, die Sie festlegen können, finden Sie unter den folgenden Themen:

- [Eigenschaften von Attributen in UML-Klassendiagrammen](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Eigenschaften von Vorgängen in UML-Klassendiagrammen](../modeling/properties-of-operations-on-uml-class-diagrams.md)

### <a name="types-of-attributes-and-operations"></a>Typen von Attributen und Vorgängen
 Each *Type* of an attribute or operation, and each parameter type, can be one of the following:

- **(none)** - You can leave a type unspecified in the signature by omitting the preceding colon (`:`).

- One of the standard primitive types: **Boolean**, **Integer**, **String**.

- Einen Typ, der im Modell definiert ist.

- A parameterized value of a template type, written Template\<Parameter>. See [Template Types](#Templates).

  Sie können auch den Namen eines Typs schreiben, den Sie im Modell noch nicht definiert haben. The name will be listed under **Unspecified Types** in UML Model Explorer.

> [!NOTE]
> Wenn Sie anschließend im Modell eine Klasse oder Schnittstelle mit diesem Namen definieren, verweisen ältere Attribute und Operationen weiterhin auf das Element in "Nicht spezifizierte Typen". Wenn Sie diese älteren Komponenten ändern möchten, damit sie auf die neue Klasse verweisen, müssen Sie für jedes Attribut bzw. jede Operation den Typ zurücksetzen und die neue Klasse im Dropdownmenü auswählen.

#### <a name="multiple-types"></a>Mehrere Typen
 Sie können eine Multiplizität für beliebige Attribute, Vorgänge oder Parametertypen festlegen.

 Die zulässigen Werte lauten wie folgt:

 `[1]`

 Ein Wert des angegebenen Typs. Dies ist die Standardeinstellung.

 `[0..1]`

 **Null** or a value of the given type.

 `[*]`

 Eine Auflistung einer beliebigen Anzahl von Instanzen des angegebenen Typs.

 `[1..*]`

 Eine Auflistung von mindestens einer Instanz des angegebenen Typs.

 `[n..m]`

 Eine Auflistung von zwischen `n` und `m` Instanzen des angegebenen Typs.

 Wenn die Multiplizität mehr als 1 beträgt, können Sie auch diese Eigenschaften festlegen:

- **IsOrdered** - If true, the collection has a defined order.

- **IsUnique** - If true, there are no duplicate values in the collection.

### <a name="visibility"></a>Sichtbarkeit
 *Visibility* indicates whether the attribute or operation can be accessed outside the class definition. Die zulässigen Werte lauten wie folgt:

 **Public**

 **+**

 Zugriff ist von allen anderen Typen möglich.

 **Private**

 **-**

 Zugriff ist nur auf die interne Definition dieses Typs möglich.

 **Pakete**

 **~**

 Der Zugriff ist nur innerhalb des Pakets, das diesen Typ enthält, und in allen Paketen möglich, die diesen explizit importieren. See [Defining Namespaces and Packages](#Packages).

 **Protected**

 **#**

 Der Zugriff ist nur auf diesen Typ und die Typen möglich, die davon erben. See [Inheritance](#Inheritance).

### <a name="setting-the-signature-of-an-attribute-or-an-operation"></a>Festlegen der Signatur eines Attributs oder eines Vorgangs
 Die Signatur eines Attributs oder eines Vorgangs ist eine Auflistung von Eigenschaften, die die Sichtbarkeit, den Namen, die Parameter (für Vorgänge) und den Typ enthält.

 Sie können eine Signatur direkt in das Diagramm schreiben. Klicken Sie zum Auswählen auf das Attribut oder den Vorgang, und klicken Sie dann noch einmal darauf.

 Schreiben Sie die Signatur wie folgt:

```
visibility attribute-name : Type
```

 \- oder -

```
visibility operation-name (parameter1 : Type1, ...) : Type
```

 Beispiel:

```
+ AddItem (item : MenuItem, quantity : Integer) : Boolean
```

 Verwenden Sie die Kurzform der Sichtbarkeit. Der Standardwert ist `+` (öffentlich).

 Bei jedem Typ kann es sich um im Modell definierte Typen, Standardtypen wie "Ganze Zahl" oder "Zeichenfolge" oder den Namen eines neuen Typs handeln, den Sie noch nicht definiert haben.

> [!NOTE]
> Wenn Sie einen Namen ohne einen Typ in eine Parameterliste schreiben, wird anstelle seines Typs der Name des Parameters angegeben. In diesem Beispiel werden "MenuItem" und "Integer" zu den Namen von zwei Parametern mit nicht angegebenen Typen:
>
> `AddItem(MenuItem, Integer) /* parameter names, not types! */`

 Um die Multiplizität eines Typs in einer Signatur festzulegen, schreiben Sie die Multiplizität in eckigen Klammern nach dem Typnamen, z. B.:

```
+ AddItems (items : MenuItem [1..*])
+ MenuContent : MenuItem [*]
```

 Falls das Attribut oder der Vorgang statisch ist, wird sein Name in der Signatur unterstrichen angezeigt. Wenn dieser abstrakt ist, wird der Name kursiv angezeigt.

 However, you can only set the **Is Static** and **Is Abstract** properties in the **Properties** window.

#### <a name="full-signature"></a>Vollständige Signatur
 Wenn Sie die Signatur eines Attributs oder Vorgangs bearbeiten, werden ggf. einige zusätzliche Eigenschaften am Ende der Zeile und nach jedem Parameter angezeigt. Sie stehen in geschweiften Klammern ({…}). Sie können diese Eigenschaften bearbeiten oder hinzufügen. Beispiel:

```
+ AddItems (items: MenuItem [1..*] {unique, ordered})
+ GetItems (filter: String) : MenuItem [*] {ordered, query}
```

 Dort stehen die folgenden Eigenschaften zur Auswahl:

 `unique`

 **Is Unique**

 Die Auflistung enthält keine doppelten Werte. Gilt für Typen mit einer Multiplizität größer als 1.

 `ordered`

 **Is Ordered**

 Die Auflistung ist eine Sequenz. Bei "false" ist kein eindeutiges erstes Element vorhanden. Gilt für Typen mit einer Multiplizität größer als 1.

 `query`

 **Is Query**

 Der Vorgang ändert den Zustand seiner Instanz nicht. Gilt nur für Vorgänge.

 `/`

 **Is Derived**

 Das Attribut wird aus Werten anderer Attribute oder Zuordnungen berechnet.

 "/" steht vor dem Namen eines Attributs. Beispiel:

```
/TotalPrice: Integer
```

 Normalerweise wird die vollständige Signatur nur im Diagramm angezeigt, während Sie es bearbeiten. Wenn Sie die Bearbeitung beenden, werden die zusätzlichen Eigenschaften ausgeblendet. If you want to see the full signature all the time, open the shortcut menu for the type, and then choose **Show Full Signature**.

## <a name="Associations"></a> Drawing and Using Associations
 Verwenden Sie eine Zuordnung, um eine beliebige Art von Verknüpfung zwischen zwei Elementen darzustellen, und zwar unabhängig davon, wie die Verknüpfung in der Software implementiert ist. Sie können eine Zuordnung z. B. verwenden, um einen Zeiger in C#, eine Beziehung in einer Datenbank oder einen Querverweis von einem Teil einer XML-Datei zu einem anderen darzustellen. Sie kann eine Zuordnung zwischen realen Objekten darstellen, z. B. Erde und Sonne. Die Zuordnung besagt nicht, wie der Link dargestellt wird, sondern nur, dass die Informationen vorhanden sind.

### <a name="properties-of-an-association"></a>Eigenschaften einer Zuordnung
 Nachdem Sie eine Zuordnung erstellt haben, legen Sie die Eigenschaften dafür fest. Open the shortcut menu for the association, and then choose **Properties**.

 In addition to the properties of the association as a whole, each *role*, that is, each end of the association, has some properties of its own. To view them, expand the **First Role** and **Second Role** properties.

 Einige Eigenschaften jeder Rolle sind direkt im Diagramm sichtbar. Dies sind:

- Der Rollenname. Er wird am entsprechenden Ende der Zuordnung im Diagramm angezeigt. You can set it either on the diagram or in the **Properties** window.

- **Multiplicity**, which defaults to **1**. Diese Eigenschaft wird auch am entsprechenden Ende der Zuordnung im Diagramm angezeigt.

- **Aggregation**. Wird an einem Ende des Konnektors in Rautenform angezeigt. Damit können Sie angeben, dass die Aggregierungsrolle Instanzen der anderen besitzt oder enthält.

- **Is Navigable**. Wenn nur für eine Rolle "true" gilt, wird ein Pfeil angezeigt, der in die navigierbare Richtung zeigt. Sie können dies nutzen, um die Navigierbarkeit von Links und Datenbankbeziehungen in der Software anzugeben.

  For the full details of these and other properties, see [Properties of associations on UML class diagrams](../modeling/properties-of-associations-on-uml-class-diagrams.md).

### <a name="navigability"></a>Navigierbarkeit
 Eine gezeichnete Zuordnung weist an einem Ende einen Pfeil auf, der angibt, dass die Zuordnung in dieser Richtung navigierbar ist. Dies ist hilfreich, wenn das Klassendiagramm Softwareklassen darstellt und die Zuordnungen Zeiger oder Verweise darstellen. Wenn Sie jedoch ein Klassendiagramm zum Darstellen von Entitäten und Beziehungen oder Geschäftskonzepten verwenden, ist es weniger wichtig, die Navigierbarkeit darzustellen. In diesem Fall kann es ratsam sein, Zuordnungen ohne Pfeile zu zeichnen. You can do so by setting the **Is Navigable** property on both ends of the association to True.

### <a name="attributes-and-associations"></a>Attribute und Zuordnungen
 Eine Zuordnung ist eine grafische Darstellung eines Attributs. Anstatt z. B. eine Klasse "Restaurant" mit einem Attribut vom Typ "Menu" zu erstellen, können Sie eine Zuordnung von "Restaurant" zu "Menu" ziehen.

 Jeder Attributname wird zu einem Rollennamen. Er wird am entgegengesetzten Ende der Zuordnung des besitzenden Typs angezeigt. Ein Beispiel in der Abbildung ist `myMenu`.

 Normalerweise ist es besser, Attribute nur für Typen zu verwenden, die Sie nicht im Diagramm zeichnen würden, z. B. primitive Typen.

 ![Equivalent association and attributes](../modeling/media/uml-classguideattrib.png "UML_ClassGuideAttrib")

## <a name="Inheritance"></a> Vererbung
 Use the **Inheritance** tool to create the following relationships:

- A *generalization* relationship between a specialized type and a general type

   \- oder -

- A *realization* relation between a class and an interface that it implements.

  Sie können in Vererbungsbeziehungen keine Schleifen erstellen.

### <a name="generalization"></a>Generalisierung
 Generalisierung bedeutet, dass der spezialisierende oder abgeleitete Typ Attribute, Vorgänge und Zuordnungen des allgemeinen Typs oder Basistyps erbt.

 Der allgemeine Typ wird am Pfeilspitzenende der Beziehung angezeigt.

 Die geerbten Vorgänge und Attribute werden in den spezialisierenden Typen normalerweise nicht angezeigt. Sie können der Vorgangsliste des spezialisierenden Typs jedoch geerbte Vorgänge hinzufügen. Dies ist nützlich, wenn Sie im spezialisierenden Typ einige der Eigenschaften eines Vorgangs überschreiben möchten oder wenn Sie angeben möchten, dass der implementierende Code dies durchführen soll.

##### <a name="to-override-an-operations-definition-in-a-specializing-type"></a>So überschreiben Sie die Definition eines Vorgangs in einem spezialisierenden Typ

1. Klicken Sie auf die Generalisierungsbeziehung.

    Sie wird markiert, und daneben wird ein Aktionstag angezeigt.

2. Click the Action tag, and then click **Override Operations**.

    The **Override Operations** dialog box appears.

3. Select the operations that you want to appear in the specializing type, and then click **OK**.

   Die ausgewählten Vorgänge werden jetzt im spezialisierenden Typ angezeigt.

### <a name="realization"></a>Realisierung
 Realisierung bedeutet, dass eine Klasse die Attribute und Vorgänge implementiert, die von der Schnittstelle angegeben werden. Die Schnittstelle befindet sich am Pfeilende des Konnektors.

 Wenn Sie einen Realisierungskonnektor erstellen, werden die Vorgänge der Schnittstelle automatisch in der realisierenden Klasse repliziert. Wenn Sie einer Schnittstelle neue Vorgänge hinzufügen, werden diese in den realisierenden Klassen repliziert.

 Nachdem Sie eine Realisierungsbeziehung erstellt haben, können Sie diese in eine Lollipopnotation konvertieren. Right-click the relationship and choose **Show as Lollipop**.

 Auf diese Weise können Sie die von einer Klasse implementierten Schnittstellen anzeigen, ohne dass die Klassendiagramme zu viele Realisierungslinks enthalten. Außerdem können Sie die Schnittstelle und die Klassen, die diese realisieren, in separaten Diagrammen anzeigen.

 ![Realization shown with conector and lollipop](../modeling/media/uml-classguiderealize.png "UML_ClassGuideRealize")

## <a name="Templates"></a> Template Types
 Sie können einen generischen Typ oder Vorlagentyp definieren, der von anderen Typen oder Werten parametrisiert werden kann.

 Sie können z. B. ein generisches Wörterbuch erstellen, das mithilfe von Schlüssel- und Werttypen parametrisiert wird:

 ![Template class with two parameters](../modeling/media/uml-classguidetemplate1.png "UML_ClassGuideTemplate1")

#### <a name="to-create-a-template-type"></a>So erstellen Sie einen Vorlagentyp

1. Erstellen Sie eine Klasse oder eine Schnittstelle. Dies wird zu Ihrem Vorlagentyp. Benennen Sie diesen entsprechend, z. B. `Dictionary`.

2. Open the shortcut menu for the new type, and then choose **Properties**.

3. In the **Properties** window, click **[…]** in the **Template Parameters** field.

    The **Template Parameter Collection Editor** dialog box appears.

4. Wählen Sie **Hinzufügen** aus.

5. Legen Sie die Namenseigenschaft auf einen Parameternamen für den Vorlagentyp fest, z. B. `Key`.

6. Set **Parameter Kind**. The default is **Class**.

7. If you want the parameter to accept only derived classes of a particular base class, set **Constrained Value** to the base class that you want.

8. Add as many parameters as you need, then choose **OK**.

9. Fügen Sie dem Vorlagentyp Attribute und Vorgänge hinzu, wie Sie dies auch bei anderen Klassen tun.

     You can use parameters whose kind is **Class**, **Interface** or **Enumeration** in the definition of attributes and operations. Indem Sie beispielsweise die Parameterklassen `Key` und `Value` verwenden, können Sie den Vorgang in `Dictionary` definieren:

     `Get(k : Key) : Value`

     You can use a parameter whose kind is **Integer** as a bound in a multiplicity. Beispielsweise kann ein Parameter mit einer ganzen Zahl und einem Maximalwert verwendet werden, um die Multiplizität eines Attributs als `[0..max]` zu definieren.

   Wenn Sie Vorlagentypen erstellt haben, können Sie diese zum Definieren von Vorlagenbindungen verwenden:

   ![A  class bound from the Dictionary template](../modeling/media/uml-classguidetemplate2.png "UML_ClassGuideTemplate2")

#### <a name="to-use-a-template-type"></a>So verwenden Sie einen Vorlagentyp

1. Erstellen Sie einen neuen Typ, z. B. `AddressTable`.

2. Open the shortcut menu for the new type, and then choose **Properties**.

3. In the **Template Binding** property, select the template type, for example `Dictionary`, from the drop-down list.

4. Expand the **Template Binding** property.

     Für jeden Parameter des Vorlagentyps wird eine Zeile angezeigt.

5. Legen Sie jeden Parameter auf einen geeigneten Wert fest. Legen Sie den `Key`-Parameter z. B. auf eine Klasse mit dem Namen `Name` fest.

## <a name="Packages"></a> Packages
 Sie können Pakete in einem UML-Klassendiagramm anzeigen. Ein Paket ist ein Container für andere Modellelemente. Sie können in einem Paket beliebige Elemente erstellen. Im Diagramm werden die im Paket enthaltenen Elemente neu angeordnet, wenn Sie das Paket verschieben.

 Sie können das Steuerelement zum Reduzieren/Erweitern verwenden, um den Inhalt des Pakets aus- oder einzublenden.

 See [Define packages and namespaces](../modeling/define-packages-and-namespaces.md).

## <a name="generating"></a> Generating Code from UML Class Diagrams
 Generieren Sie C#-Code oder passen Sie die Vorlagen für Codegenerierung an, um die Implementierung der Klassen in einem UML-Klassendiagramm zu starten. So starten Sie das Generieren von Code mithilfe der bereitgestellten C#-Vorlagen:

- Open the shortcut menu for the diagram or an element, choose **Generate Code**, and then set the necessary properties.

     For more information about how to set these properties and customize the provided templates, see [Generate code from UML class diagrams](../modeling/generate-code-from-uml-class-diagrams.md).

## <a name="see-also"></a>Siehe auch
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [Model user requirements](../modeling/model-user-requirements.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Sequence Diagrams: Reference](../modeling/uml-sequence-diagrams-reference.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md)
