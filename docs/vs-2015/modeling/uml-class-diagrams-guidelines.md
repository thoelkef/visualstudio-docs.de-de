---
title: 'UML-Klassendiagramme: Richtlinien | Microsoft-Dokumentation'
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
ms.openlocfilehash: 4f4fd6eed634da3aea956cddca8d2e1ff6220a94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850187"
---
# <a name="uml-class-diagrams-guidelines"></a>UML-Klassendiagramme: Richtlinien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Sie ein UML- *Klassendiagramm* verwenden, um Datentypen und ihre Beziehungen getrennt von ihrer Implementierung zu beschreiben. Das Diagramm wird verwendet, um die Konzentration auf die logischen Aspekte der Klassen zu leiten, anstatt auf ihre Implementierung.

 Um ein UML-Klassendiagramm zu erstellen, wählen Sie im Menü **Architektur** die Option **neues UML-Diagramm oder ebenendiagramm**aus.

 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> In diesem Thema geht es um UML-Klassendiagramme. Es gibt noch eine andere Art von Klassendiagramm, das erstellt und verwendet wird, um Programmcode visuell darzustellen. Siehe [Entwerfen und Anzeigen von Klassen und Typen](https://msdn.microsoft.com/library/ab7aty24.aspx).

## <a name="using-uml-class-diagrams"></a><a name="Using"></a> Verwenden von UML-Klassendiagrammen
 Sie können ein UML-Klassendiagramm für viele verschiedene Zwecke verwenden:

- Zum Bereitstellen einer von der Implementierung unabhängigen Beschreibung der Typen, die in einem System verwendet und zwischen Komponenten übergeben werden.

     Der Typ "Meal Order" kann z. B. in .NET-Code auf Geschäftsebene, in XML auf den Schnittstellen zwischen Komponenten, in SQL in der Datenbank und in HTML auf der Benutzeroberfläche implementiert werden. Obwohl diese Implementierungen sich in ihren Details unterscheiden, ist die Beziehung zwischen "Meal Order" und anderen Typen wie "Menu" und "Payment" immer gleich. Das UML-Klassendiagramm macht es möglich, diese Beziehungen getrennt von den Implementierungen darzustellen.

- Zum Verdeutlichen des Glossars mit den Begriffen, die für die Kommunikation zwischen der Anwendung und ihren Benutzern und in Beschreibungen der Benutzeranforderungen verwendet werden. Weitere Informationen finden Sie unter [Modellieren von Benutzeranforderungen](../modeling/model-user-requirements.md).

     Nehmen wir z. B. die Benutzertextabschnitte, Anwendungsfälle oder anderen Anforderungsbeschreibungen einer Restaurantanwendung. Diese Beschreibungen enthalten zum Beispiel Begriffe wie Menu (Speisekarte), Order (Bestellung), Meal (Gericht), Price (Preis), Payment (Bezahlung) usw. Sie können ein UML-Klassendiagramm zeichnen, das die Beziehungen zwischen diesen Begriffen definiert. Auf diese Weise wird das Risiko von Inkonsistenzen in den Anforderungsbeschreibungen, in der Benutzeroberfläche und in den Hilfedokumenten reduziert.

### <a name="relationship-to-other-diagrams"></a>Beziehung zu anderen Diagrammen
 Ein UML-Klassendiagramm wird normalerweise zusammen mit anderen Modellierungsdiagrammen gezeichnet, um Beschreibungen der verwendeten Typen bereitzustellen. Die physische Darstellung der Typen wird in keinem der Diagramme wiedergegeben.

 Aktivitätsdiagramm

 Typ der Daten, der über einen Objektknoten übergeben wird.

 Typen von Eingabe- und Ausgabepins und Aktivitätsparameterknoten.

 Siehe [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md).

 Sequenzdiagramm

 Typen von Parametern und Rückgabewerte von Meldungen.

 Typen der Lebenslinien. Die Klasse einer Lebenslinie sollte Vorgänge für alle Meldungen enthalten, die empfangen werden können.

 Siehe [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md).

 Komponentendiagramm

 Komponentenschnittstellen, unter denen die Vorgänge aufgeführt sind.

 Siehe [UML-Komponenten Diagramme: Richtlinien](../modeling/uml-component-diagrams-guidelines.md).

 Anwendungsfalldiagramm

 Typen, die in Beschreibungen der Ziele und Schritte eines Anwendungsfalls erwähnt werden.

 Siehe [UML-Anwendungsfall Diagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="basic-steps-for-drawing-class-diagrams"></a><a name="BasicSteps"></a> Grundlegende Schritte zum Zeichnen von Klassendiagrammen
 Referenzinformationen zu den Elementen in UML-Klassendiagrammen finden Sie unter [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md).

> [!NOTE]
> Ausführliche Schritte zum Erstellen von Modellierungs Diagrammen werden unter [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md)beschrieben.

#### <a name="to-create-a-uml-class-diagram"></a>So erstellen Sie ein UML-Klassendiagramm

1. Wählen Sie im Menü **Architektur** die Option **neues UML-oder ebenendiagramm**aus.

2. Wählen Sie unter **Vorlagen**die Option **UML-Klassendiagramm**aus.

3. Benennen Sie das Diagramm.

4. Wählen Sie unter **zu Modellierungsprojekt hinzufügen**ein vorhandenes Modellierungsprojekt in der Projekt Mappe aus, oder **Erstellen Sie ein neues Modellierungsprojekt**, und wählen Sie dann **OK**aus.

     Ein neues Klassendiagramm wird mit der **Diagramm** Toolbox der Umschlag Sequenz angezeigt. Die Toolbox enthält die erforderlichen Elemente und Beziehungen.

#### <a name="to-draw-a-uml-class-diagram"></a>So zeichnen Sie ein UML-Klassendiagramm

1. Um einen Typ zu erstellen, wählen Sie die **Klasse**, **Schnittstelle** oder das **enumerationstool** in der Toolbox aus, und klicken Sie dann auf einen leeren Teil des Diagramms. (Wenn die Toolbox nicht angezeigt wird, drücken Sie STRG+ALT+X.)

2. Zum Hinzufügen von Attributen oder Vorgängen zu den Typen oder literalen zu einer Enumeration wählen Sie die Überschrift **Attribute**, **Vorgänge** oder **Literale** im Typ aus, und drücken Sie die EINGABETASTE.

     Sie können eine Signatur schreiben, z. B. `f(x:Boolean):Integer`. Siehe [Attribute und Vorgänge](#AttributesAndOperations).

     Um schnell mehrere Elemente hinzuzufügen, drücken Sie am Ende jedes Elements zweimal die EINGABETASTE. Sie können in der Liste mit den PFEILTASTEN nach oben und unten navigieren.

3. Um einen Typ zu erweitern oder zu reduzieren, wählen Sie oben links das Chevronsymbol aus. Sie können auch den Abschnitt **Attribute** und **Vorgänge** einer Klasse oder Schnittstelle erweitern und reduzieren.

4. Um zwischen den Typen Zuordnungs-, Vererbungs- oder Abhängigkeitslinks zu zeichnen, klicken Sie auf das entsprechende Tool, auf den Quelltyp und dann auf den Zieltyp.

5. Um Typen in einem Paket zu erstellen, erstellen Sie ein Paket mit dem **Paket** Tool, und erstellen Sie dann neue Typen und Pakete innerhalb des Pakets. Sie können auch den Kopierbefehl verwenden, um Typen zu kopieren und in ein Paket einzufügen.

6. Jedes Diagramm ist eine Ansicht eines Modells, das im gleichen Projekt auch von anderen Diagrammen genutzt wird. Um eine Strukturansicht des gesamten Modells anzuzeigen, wählen Sie **Ansicht**, **Weitere Fenster**, **UML-Modell-Explorer**aus.

## <a name="using-classes-interfaces-and-enumerations"></a><a name="UsingTypes"></a> Verwenden von Klassen, Schnittstellen und Enumerationen
 In der Toolbox sind drei Standardarten von Klassifizierern verfügbar. Diese werden in diesem Dokument als *Typen* bezeichnet.

 ![Eine Klasse, eine Enumeration und eine Schnittstelle](../modeling/media/uml-classguidetypes.png "UML_ClassGuideTypes")

- Verwenden Sie **Klassen** (1), um Daten oder Objekttypen für die meisten Zwecke darzustellen.

- Verwenden Sie **Schnittstellen** (2) in einem Kontext, in dem Sie zwischen reinen Schnittstellen und konkreten Klassen mit internen Implementierungen unterscheiden müssen. Dieser Unterschied ist nützlich, wenn der Zweck des Diagramms darin besteht, eine Softwareimplementierung zu beschreiben. Er ist weniger nützlich, wenn Sie passive Daten modellieren oder wenn Sie Konzepte definieren, die zum Beschreiben der Benutzeranforderungen verwendet werden.

- Verwenden Sie eine **Enumeration** (3), um einen Typ darzustellen, der über eine begrenzte Anzahl von Literalwerten verfügt, z `Stop` . b `Go` . und.

  - Fügen Sie die Literalwerte der Enumeration hinzu. Geben Sie jedem Wert einen anderen Namen.

  - Sie können bei Bedarf auch einen numerischen Wert für jeden Literalwert angeben. Öffnen Sie das Kontextmenü für das Literale in der-Enumeration, wählen Sie **Eigenschaften**aus, und geben Sie dann im Fenster **Eigenschaften** im Feld **Wert** eine Zahl ein.

  Geben Sie jedem Typ einen eindeutigen Namen.

### <a name="getting-types-from-other-diagrams"></a>Abrufen von Typen aus anderen Diagrammen
 Sie können festlegen, dass Typen aus einem anderen Diagramm in Ihrem UML-Klassendiagramm angezeigt werden.

 UML-Klassendiagramm

 Sie können festlegen, dass eine Klasse in mehr als einem UML-Klassendiagramm angezeigt wird. Wenn Sie eine Klasse in einem Diagramm erstellt haben, ziehen Sie die Klasse aus dem **UML-Modell-Explorer** auf das andere Diagramm.

 Dies ist nützlich, wenn Sie erreichen möchten, dass der Schwerpunkt in jedem Diagramm auf einer bestimmten Gruppe von Beziehungen liegt.

 Beispielsweise können Sie die Zuordnungen zwischen einer Essensbestellung (Meal Order) und der Speisekarte (Menu) des Restaurants in einem Diagramm und die Zuordnungen zwischen Essensbestellung und Bezahlung (Payment) in einem anderen Diagramm anzeigen.

 Komponentendiagramm

 Wenn Sie Schnittstellen für die Komponenten in einem Komponenten Diagramm definiert haben, können Sie eine Schnittstelle aus dem **UML-Modell-Explorer** in das Klassendiagramm ziehen. Im Klassendiagramm können Sie die Methoden definieren, die in der Schnittstelle enthalten sind.

 Siehe [UML-Komponenten Diagramme: Richtlinien](../modeling/uml-component-diagrams-guidelines.md).

 UML-Sequenzdiagramm

 Sie können Klassen und Schnittstellen aus Lebenslinien in einem Sequenzdiagramm erstellen und dann die Klasse aus dem **UML-Modell-Explorer** in ein UML-Klassendiagramm ziehen. Jede Lebenslinie in einem Sequenzdiagramm stellt eine Instanz eines Objekts, einer Komponente oder eines Akteurs dar.

 Um eine Klasse aus einer Lebenslinie zu erstellen, öffnen Sie das Kontextmenü für die Lebenslinie, und wählen Sie dann **Klasse erstellen** oder **Schnittstelle erstellen**aus. Siehe [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md).

## <a name="attributes-and-operations"></a><a name="AttributesAndOperations"></a> Attribute und Vorgänge
 Ein Attribut (4) ist ein benannter Wert, über den jede Instanz eines Typs verfügen kann. Das Zugreifen auf ein Attribut führt nicht dazu, dass der Zustand der Instanz geändert wird.

 Ein Vorgang (5) ist eine Methode oder Funktion, die Instanzen des Typs ausführen kann. Dabei kann ein Wert zurückgegeben werden. Wenn seine **IsQuery** -Eigenschaft den Wert true aufweist, kann der Zustand der Instanz nicht geändert werden.

 Öffnen Sie zum Hinzufügen eines Attributs oder eines Vorgangs zu einem Typ das Kontextmenü für den Typ, wählen Sie **Hinzufügen**aus, und wählen Sie dann **Attribut** oder **Vorgang**aus.

 Um die Eigenschaften anzuzeigen, öffnen Sie das Kontextmenü für das Attribut oder den Vorgang, und wählen Sie dann **Eigenschaften**aus. Die Eigenschaften werden im **Eigenschaften** Fenster angezeigt.

 Wählen Sie <strong>[...]</strong> aus, um die Eigenschaften der Parameter eines Vorgangs anzuzeigen. in der **Parameters** -Eigenschaft. Ein neues Eigenschaftendialogfeld wird angezeigt.

 Ausführliche Informationen zu allen Eigenschaften, die Sie festlegen können, finden Sie unter den folgenden Themen:

- [Eigenschaften von Attributen in UML-Klassendiagrammen](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Eigenschaften von Vorgängen in UML-Klassendiagrammen](../modeling/properties-of-operations-on-uml-class-diagrams.md)

### <a name="types-of-attributes-and-operations"></a>Typen von Attributen und Vorgängen
 Jeder *Typ* eines Attributs oder Vorgangs und jeder Parametertyp kann eines der folgenden sein:

- **(keine)** : Sie können einen Typ in der Signatur nicht angeben, indem Sie den vorangehenden Doppelpunkt () weglassen `:` .

- Einer der primitiven Standardtypen: **Boolean**, **Integer**, **String**.

- Einen Typ, der im Modell definiert ist.

- Ein parametrisierter Wert eines Vorlagen Typs, der als Vorlage geschrieben wurde \<Parameter> . Siehe [Vorlagen Typen](#Templates).

  Sie können auch den Namen eines Typs schreiben, den Sie im Modell noch nicht definiert haben. Der Name wird im UML-Modell-Explorer unter **nicht angegebene Typen** aufgeführt.

> [!NOTE]
> Wenn Sie anschließend im Modell eine Klasse oder Schnittstelle mit diesem Namen definieren, verweisen ältere Attribute und Operationen weiterhin auf das Element in "Nicht spezifizierte Typen". Wenn Sie diese älteren Komponenten ändern möchten, damit sie auf die neue Klasse verweisen, müssen Sie für jedes Attribut bzw. jede Operation den Typ zurücksetzen und die neue Klasse im Dropdownmenü auswählen.

#### <a name="multiple-types"></a>Mehrere Typen
 Sie können eine Multiplizität für beliebige Attribute, Vorgänge oder Parametertypen festlegen.

 Die zulässigen Werte lauten wie folgt:

 `[1]`

 Ein Wert des angegebenen Typs. Dies ist die Standardoption.

 `[0..1]`

 **Null** oder ein Wert des angegebenen Typs.

 `[*]`

 Eine Auflistung einer beliebigen Anzahl von Instanzen des angegebenen Typs.

 `[1..*]`

 Eine Auflistung von mindestens einer Instanz des angegebenen Typs.

 `[n..m]`

 Eine Auflistung von zwischen `n` und `m` Instanzen des angegebenen Typs.

 Wenn die Multiplizität mehr als 1 beträgt, können Sie auch diese Eigenschaften festlegen:

- **Isorder** : Wenn true, hat die Auflistung eine definierte Reihenfolge.

- **IsUnique** : Wenn true, sind in der Auflistung keine doppelten Werte vorhanden.

### <a name="visibility"></a>Sichtbarkeit
 *Sichtbarkeit* gibt an, ob auf das Attribut oder den Vorgang außerhalb der Klassendefinition zugegriffen werden kann. Die zulässigen Werte lauten wie folgt:

 **Öffentlich**

 **+**

 Zugriff ist von allen anderen Typen möglich.

 **Privat**

 **-**

 Zugriff ist nur auf die interne Definition dieses Typs möglich.

 **Pakete**

 **~**

 Der Zugriff ist nur innerhalb des Pakets, das diesen Typ enthält, und in allen Paketen möglich, die diesen explizit importieren. Siehe [Definieren von Namespaces und Paketen](#Packages).

 **Gebieten**

 **#**

 Der Zugriff ist nur auf diesen Typ und die Typen möglich, die davon erben. Siehe [Vererbung](#Inheritance).

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

 Zum Beispiel:

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

 Sie können jedoch nur die Eigenschaft **ist statisch** und **sind abstrakte** Eigenschaften im **Eigenschaften** Fenster festlegen.

#### <a name="full-signature"></a>Vollständige Signatur
 Wenn Sie die Signatur eines Attributs oder Vorgangs bearbeiten, werden ggf. einige zusätzliche Eigenschaften am Ende der Zeile und nach jedem Parameter angezeigt. Sie stehen in geschweiften Klammern ({…}). Sie können diese Eigenschaften bearbeiten oder hinzufügen. Zum Beispiel:

```
+ AddItems (items: MenuItem [1..*] {unique, ordered})
+ GetItems (filter: String) : MenuItem [*] {ordered, query}
```

 Dort stehen die folgenden Eigenschaften zur Auswahl:

 `unique`

 **Ist eindeutig**

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

 "/" steht vor dem Namen eines Attributs. Zum Beispiel:

```
/TotalPrice: Integer
```

 Normalerweise wird die vollständige Signatur nur im Diagramm angezeigt, während Sie es bearbeiten. Wenn Sie die Bearbeitung beenden, werden die zusätzlichen Eigenschaften ausgeblendet. Wenn Sie die vollständige Signatur jederzeit anzeigen möchten, öffnen Sie das Kontextmenü für den Typ, und wählen Sie dann **vollständige Signatur anzeigen**aus.

## <a name="drawing-and-using-associations"></a><a name="Associations"></a> Zeichnen und Verwenden von Zuordnungen
 Verwenden Sie eine Zuordnung, um eine beliebige Art von Verknüpfung zwischen zwei Elementen darzustellen, und zwar unabhängig davon, wie die Verknüpfung in der Software implementiert ist. Sie können eine Zuordnung z. B. verwenden, um einen Zeiger in C#, eine Beziehung in einer Datenbank oder einen Querverweis von einem Teil einer XML-Datei zu einem anderen darzustellen. Sie kann eine Zuordnung zwischen realen Objekten darstellen, z. B. Erde und Sonne. Die Zuordnung besagt nicht, wie der Link dargestellt wird, sondern nur, dass die Informationen vorhanden sind.

### <a name="properties-of-an-association"></a>Eigenschaften einer Zuordnung
 Nachdem Sie eine Zuordnung erstellt haben, legen Sie die Eigenschaften dafür fest. Öffnen Sie das Kontextmenü für die Zuordnung, und wählen Sie dann **Eigenschaften**aus.

 Zusätzlich zu den Eigenschaften der Zuordnung als Ganzes verfügt jede *Rolle*, d. h. jedes Ende der Zuordnung, über eigene Eigenschaften. Um diese anzuzeigen, erweitern Sie die Eigenschaften **erste Rolle** und **zweite Rolle** .

 Einige Eigenschaften jeder Rolle sind direkt im Diagramm sichtbar. Dies sind:

- Der Rollenname. Er wird am entsprechenden Ende der Zuordnung im Diagramm angezeigt. Sie können Sie entweder im Diagramm oder im **Eigenschaften** Fenster festlegen.

- **Multiplizität, der**Standardwert ist **1**. Diese Eigenschaft wird auch am entsprechenden Ende der Zuordnung im Diagramm angezeigt.

- **Aggregation**. Wird an einem Ende des Konnektors in Rautenform angezeigt. Damit können Sie angeben, dass die Aggregierungsrolle Instanzen der anderen besitzt oder enthält.

- **Ist navigiert**. Wenn nur für eine Rolle "true" gilt, wird ein Pfeil angezeigt, der in die navigierbare Richtung zeigt. Sie können dies nutzen, um die Navigierbarkeit von Links und Datenbankbeziehungen in der Software anzugeben.

  Ausführliche Informationen zu diesen und anderen Eigenschaften finden Sie unter [Eigenschaften von Zuordnungen in UML-Klassendiagrammen](../modeling/properties-of-associations-on-uml-class-diagrams.md).

### <a name="navigability"></a>Navigierbarkeit
 Eine gezeichnete Zuordnung weist an einem Ende einen Pfeil auf, der angibt, dass die Zuordnung in dieser Richtung navigierbar ist. Dies ist hilfreich, wenn das Klassendiagramm Softwareklassen darstellt und die Zuordnungen Zeiger oder Verweise darstellen. Wenn Sie jedoch ein Klassendiagramm zum Darstellen von Entitäten und Beziehungen oder Geschäftskonzepten verwenden, ist es weniger wichtig, die Navigierbarkeit darzustellen. In diesem Fall kann es ratsam sein, Zuordnungen ohne Pfeile zu zeichnen. Legen Sie dazu die Eigenschaft **ist Navigier** an beiden Enden der Zuordnung auf true fest.

### <a name="attributes-and-associations"></a>Attribute und Zuordnungen
 Eine Zuordnung ist eine grafische Darstellung eines Attributs. Anstatt z. B. eine Klasse "Restaurant" mit einem Attribut vom Typ "Menu" zu erstellen, können Sie eine Zuordnung von "Restaurant" zu "Menu" ziehen.

 Jeder Attributname wird zu einem Rollennamen. Er wird am entgegengesetzten Ende der Zuordnung des besitzenden Typs angezeigt. Ein Beispiel in der Abbildung ist `myMenu`.

 Normalerweise ist es besser, Attribute nur für Typen zu verwenden, die Sie nicht im Diagramm zeichnen würden, z. B. primitive Typen.

 ![Entsprechende Zuordnung und Attribute](../modeling/media/uml-classguideattrib.png "UML_ClassGuideAttrib")

## <a name="inheritance"></a><a name="Inheritance"></a> Vererbung
 Verwenden Sie das Tool **Vererbung** , um die folgenden Beziehungen zu erstellen:

- Eine *Generalisierungs* Beziehung zwischen einem spezialisierten Typ und einem allgemeinen Typ

   \- oder -

- Eine *Erkenntnis* Beziehung zwischen einer Klasse und einer Schnittstelle, die implementiert wird.

  Sie können in Vererbungsbeziehungen keine Schleifen erstellen.

### <a name="generalization"></a>Generalisierung
 Generalisierung bedeutet, dass der spezialisierende oder abgeleitete Typ Attribute, Vorgänge und Zuordnungen des allgemeinen Typs oder Basistyps erbt.

 Der allgemeine Typ wird am Pfeilspitzenende der Beziehung angezeigt.

 Die geerbten Vorgänge und Attribute werden in den spezialisierenden Typen normalerweise nicht angezeigt. Sie können der Vorgangsliste des spezialisierenden Typs jedoch geerbte Vorgänge hinzufügen. Dies ist nützlich, wenn Sie im spezialisierenden Typ einige der Eigenschaften eines Vorgangs überschreiben möchten oder wenn Sie angeben möchten, dass der implementierende Code dies durchführen soll.

##### <a name="to-override-an-operations-definition-in-a-specializing-type"></a>So überschreiben Sie die Definition eines Vorgangs in einem spezialisierenden Typ

1. Klicken Sie auf die Generalisierungsbeziehung.

    Sie wird markiert, und daneben wird ein Aktionstag angezeigt.

2. Klicken Sie auf das Aktions-Tag und dann auf Außerkraftsetzungs **Vorgänge**.

    Das Dialogfeld **Überschreibungs Vorgänge** wird angezeigt.

3. Wählen Sie die Vorgänge aus, die im spezialisierenden Typ angezeigt werden sollen, und klicken Sie dann auf **OK**.

   Die ausgewählten Vorgänge werden jetzt im spezialisierenden Typ angezeigt.

### <a name="realization"></a>Realisierung
 Realisierung bedeutet, dass eine Klasse die Attribute und Vorgänge implementiert, die von der Schnittstelle angegeben werden. Die Schnittstelle befindet sich am Pfeilende des Konnektors.

 Wenn Sie einen Realisierungskonnektor erstellen, werden die Vorgänge der Schnittstelle automatisch in der realisierenden Klasse repliziert. Wenn Sie einer Schnittstelle neue Vorgänge hinzufügen, werden diese in den realisierenden Klassen repliziert.

 Nachdem Sie eine Realisierungsbeziehung erstellt haben, können Sie diese in eine Lollipopnotation konvertieren. Klicken Sie mit der rechten Maustaste auf die Beziehung, und wählen Sie **als Lollipop anzeigen**.

 Auf diese Weise können Sie die von einer Klasse implementierten Schnittstellen anzeigen, ohne dass die Klassendiagramme zu viele Realisierungslinks enthalten. Außerdem können Sie die Schnittstelle und die Klassen, die diese realisieren, in separaten Diagrammen anzeigen.

 ![Realisierung mit Connector und Lollipop](../modeling/media/uml-classguiderealize.png "UML_ClassGuideRealize")

## <a name="template-types"></a><a name="Templates"></a> Vorlagen Typen
 Sie können einen generischen Typ oder Vorlagentyp definieren, der von anderen Typen oder Werten parametrisiert werden kann.

 Sie können z. B. ein generisches Wörterbuch erstellen, das mithilfe von Schlüssel- und Werttypen parametrisiert wird:

 ![Vorlagenklasse mit zwei Parametern](../modeling/media/uml-classguidetemplate1.png "UML_ClassGuideTemplate1")

#### <a name="to-create-a-template-type"></a>So erstellen Sie einen Vorlagentyp

1. Erstellen Sie eine Klasse oder eine Schnittstelle. Dies wird zu Ihrem Vorlagentyp. Benennen Sie diesen entsprechend, z. B. `Dictionary`.

2. Öffnen Sie das Kontextmenü für den neuen Typ, und wählen Sie dann **Eigenschaften**aus.

3. Klicken Sie im **Eigenschaften** Fenster im Feld **Vorlagen Parameter** auf **[...]** .

    Das Dialogfeld **Vorlagen Parameter** -Auflistungs-Editor wird angezeigt.

4. Wählen Sie **Hinzufügen** aus.

5. Legen Sie die Namenseigenschaft auf einen Parameternamen für den Vorlagentyp fest, z. B. `Key`.

6. **Parameterart**festlegen. Der Standardwert ist **Class**.

7. Wenn Sie möchten, dass der Parameter nur abgeleitete Klassen einer bestimmten Basisklasse akzeptiert, legen Sie den **eingeschränkten Wert** auf die gewünschte Basisklasse fest.

8. Fügen Sie beliebig viele Parameter hinzu, und wählen Sie dann **OK**aus.

9. Fügen Sie dem Vorlagentyp Attribute und Vorgänge hinzu, wie Sie dies auch bei anderen Klassen tun.

     In der Definition von Attributen und Vorgängen können Sie Parameter verwenden, deren Art eine **Klasse**, eine **Schnittstelle** oder eine **Enumeration** ist. Indem Sie beispielsweise die Parameterklassen `Key` und `Value` verwenden, können Sie den Vorgang in `Dictionary` definieren:

     `Get(k : Key) : Value`

     Sie können einen Parameter verwenden, dessen Art " **Integer** " als gebunden in einer Multiplizität ist. Beispielsweise kann ein Parameter mit einer ganzen Zahl und einem Maximalwert verwendet werden, um die Multiplizität eines Attributs als `[0..max]` zu definieren.

   Wenn Sie Vorlagentypen erstellt haben, können Sie diese zum Definieren von Vorlagenbindungen verwenden:

   ![Eine von der Wörterbuch Vorlage gebundene Klasse](../modeling/media/uml-classguidetemplate2.png "UML_ClassGuideTemplate2")

#### <a name="to-use-a-template-type"></a>So verwenden Sie einen Vorlagentyp

1. Erstellen Sie einen neuen Typ, z. B. `AddressTable`.

2. Öffnen Sie das Kontextmenü für den neuen Typ, und wählen Sie dann **Eigenschaften**aus.

3. Wählen Sie in der Eigenschaft **Vorlagen Bindung** den Vorlagentyp aus, z `Dictionary` . b. aus der Dropdown Liste.

4. Erweitern Sie die Eigenschaft **Vorlagen Bindung** .

     Für jeden Parameter des Vorlagentyps wird eine Zeile angezeigt.

5. Legen Sie jeden Parameter auf einen geeigneten Wert fest. Legen Sie den `Key`-Parameter z. B. auf eine Klasse mit dem Namen `Name` fest.

## <a name="packages"></a><a name="Packages"></a> Pakete
 Sie können Pakete in einem UML-Klassendiagramm anzeigen. Ein Paket ist ein Container für andere Modellelemente. Sie können in einem Paket beliebige Elemente erstellen. Im Diagramm werden die im Paket enthaltenen Elemente neu angeordnet, wenn Sie das Paket verschieben.

 Sie können das Steuerelement zum Reduzieren/Erweitern verwenden, um den Inhalt des Pakets aus- oder einzublenden.

 Siehe [Definieren von Paketen und Namespaces](../modeling/define-packages-and-namespaces.md).

## <a name="generating-code-from-uml-class-diagrams"></a><a name="generating"></a> Erstellen von Code aus UML-Klassendiagrammen
 Generieren Sie C#-Code oder passen Sie die Vorlagen für Codegenerierung an, um die Implementierung der Klassen in einem UML-Klassendiagramm zu starten. So starten Sie das Generieren von Code mithilfe der bereitgestellten C#-Vorlagen:

- Öffnen Sie das Kontextmenü für das Diagramm oder ein Element, wählen Sie **Code generieren**aus, und legen Sie dann die erforderlichen Eigenschaften fest.

     Weitere Informationen zum Festlegen dieser Eigenschaften und zum Anpassen der bereitgestellten Vorlagen finden Sie unter [Generieren von Code aus UML-Klassendiagrammen](../modeling/generate-code-from-uml-class-diagrams.md).

## <a name="see-also"></a>Weitere Informationen
 [Bearbeiten von UML-Modellen und-Diagrammen UML-](../modeling/edit-uml-models-and-diagrams.md) [Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md) [Modell Benutzer Anforderungen](../modeling/model-user-requirements.md) [UML-Komponenten Diagramme: Referenz](../modeling/uml-component-diagrams-reference.md) [UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md) [UML-Anwendungsfall Diagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md) für [UML-Komponenten Diagramme: Referenz](../modeling/uml-component-diagrams-reference.md)
