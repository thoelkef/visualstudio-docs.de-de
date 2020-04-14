---
title: Erstellen benutzerdefinierter Ansichten von C++-Objekten
description: Verwenden des Natvis-Frameworks zum Anpassen der Anzeige systemeigener Typen in Visual Studio im Debugger
ms.date: 03/02/2020
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8bdd8d26ba450b1aedd790d644c183607c44af
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224510"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Erstellen benutzerdefinierter Ansichten von C++-Objekten im Debugger mithilfe des Natvis-Frameworks

Das Visual Studio *Natvis-Framework* passt an, wie systemeigene Typen in Debuggervariablenfenstern angezeigt werden, z. B. in den **Fenstern "Locals"** und **"Watch",** und in **DataTips**. Natvis-Visualisierungen können dazu beitragen, dass die Typen, die Sie während des Debuggens erstellen, sichtbarer werden.

Natvis ersetzt die *Autoexp.dat-Datei* in früheren Versionen von Visual Studio durch XML-Syntax, bessere Diagnose, Versionsüberwachung und Unterstützung mehrerer Dateien.

> [!NOTE]
> Natvis-Anpassungen funktionieren mit Klassen und Strukturen, jedoch nicht mit typedefs.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Natvis-Visualisierungen

Sie verwenden das Natvis-Framework, um Visualisierungsregeln für die von Ihnen erstellten Typen zu erstellen, damit Entwickler sie während des Debuggens leichter sehen können.

Die folgende Abbildung zeigt beispielsweise eine Variable vom Typ [Windows::UI::Xaml::Controls::TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) in einem Debuggerfenster ohne benutzerdefinierte Visualisierungen.

![TextBox-Standardvisualisierung](../debugger/media/dbg_natvis_textbox_default.png "TextBox-Standardvisualisierung")

Die hervorgehobene Zeile zeigt die `Text` -Eigenschaft der `TextBox` -Klasse. Die komplexe Klassenhierarchie macht es schwierig, diese Eigenschaft zu finden. Der Debugger weiß nicht, wie der benutzerdefinierte Zeichenfolgentyp interpretiert werden soll, sodass die Zeichenfolge im Textfeld nicht angezeigt wird.

Dasselbe `TextBox` sieht im Variablenfenster viel einfacher aus, wenn benutzerdefinierte Visualisierungsregeln von Natvis angewendet werden. Die wichtigen Member der Klasse werden zusammen angezeigt, und der Debugger zeigt den zugrunde liegenden Zeichenfolgenwert des benutzerdefinierten Zeichenfolgentyps an.

![TextBox-Daten mit Schnellansicht](../debugger/media/dbg_natvis_textbox_visualizer.png "TextBox-Daten mit Schnellansicht")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>Verwenden von .natvis-Dateien in C++-Projekten

Natvis verwendet *.natvis-Dateien,* um Visualisierungsregeln anzugeben. Eine *.natvis-Datei* ist eine XML-Datei mit der *Erweiterung .natvis.* Das Natvis-Schema ist in *%VSINSTALLDIR%-Xml-Schemas definiert.*

Die Grundstruktur einer *.natvis-Datei* `Type` ist ein oder mehrere Elemente, die Visualisierungseinträge darstellen. Der vollqualifizierte Name `Type` jedes Elements `Name` wird in seinem Attribut angegeben.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
  <Type Name="MyNamespace::CFoo">
    .
    .
  </Type>

  <Type Name="...">
    .
    .
  </Type>
</AutoVisualizer>
```

Visual Studio stellt einige *.natvis-Dateien* im Ordner *%VSINSTALLDIR%-Common7-Pakete, Debugger-Visualizers* bereit. Diese Dateien verfügen über Visualisierungsregeln für viele gängige Typen und können als Beispiele für das Schreiben von Visualisierungen für neue Typen dienen.

### <a name="add-a-natvis-file-to-a-c-project"></a>Hinzufügen einer .natvis-Datei zu einem C++-Projekt

Sie können jedem C++-Projekt eine *.natvis-Datei* hinzufügen.

**So fügen Sie eine neue *.natvis-Datei* hinzu:**

1. Wählen Sie den C++-Projektknoten im **Projektmappen-Explorer**aus, und wählen Sie **Projekt** > **Neues Element hinzufügen**aus, oder klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie Neues**Element** **hinzufügen** > aus.

1. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die **Visualisierungsdatei Visual C++** > **Utility** > **Debugger (.natvis)** aus.

1. Benennen Sie die Datei, und wählen Sie **Hinzufügen**aus.

   Die neue Datei wird **dem Projektmappen-Explorer**hinzugefügt und im Visual Studio-Dokumentbereich geöffnet.

Der Visual Studio-Debugger lädt *.natvis-Dateien* automatisch in C++-Projekten und schließt sie standardmäßig auch in die *PDB-Datei* ein, wenn das Projekt erstellt wird. Wenn Sie die erstellte App debuggen, lädt der Debugger die *.natvis-Datei* aus der *PDB-Datei,* auch wenn das Projekt nicht geöffnet ist. Wenn Sie nicht möchten, dass die *.natvis-Datei* in der *.pdb*enthalten ist, können Sie sie aus der erstellten *.pdb-Datei* ausschließen.

**So schließen Sie eine *.natvis-Datei* aus einer *.pdb*aus:**

1. Wählen Sie die *.natvis-Datei* im **Projektmappen-Explorer**aus, und wählen Sie das **Eigenschaftensymbol** aus, oder klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie **Eigenschaften**aus.

1. Setzen Sie den Pfeil neben **Aus dem Build ausgeschlossen** herunter, und wählen Sie **Ja**aus, und wählen Sie dann **OK**aus.

>[!NOTE]
>Verwenden Sie zum Debuggen ausführbarer Projekte die Projektmappenelemente, um *alle .natvis-Dateien* hinzuzufügen, die sich nicht in der *.pdb*befinden, da kein C++-Projekt verfügbar ist.

>[!NOTE]
>Natvis-Regeln, die von einer *.pdb* geladen werden, gelten nur für die Typen in den Modulen, auf die sich die *PDB* bezieht. Wenn *Module1.pdb* beispielsweise über einen Natvis-Eintrag `Test`für einen Typ `Test` mit dem Namen verfügt, gilt er nur für die Klasse in *Module1.dll*. Wenn ein anderes Modul auch `Test`eine Klasse mit dem Namen definiert, gilt der Natvis-Eintrag *Module1.pdb* nicht für ihn.

**So installieren und registrieren Sie eine *.natvis-Datei* über ein VSIX-Paket:**

Ein VSIX-Paket kann *.natvis-Dateien* installieren und registrieren. Unabhängig davon, wo sie installiert werden, werden alle registrierten *.natvis-Dateien* während des Debuggens automatisch abgeholt.

1. Fügen Sie die *.natvis-Datei* in das VSIX-Paket ein. Zum Beispiel für die folgende Projektdatei:
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. Registrieren Sie die *.natvis-Datei* in der Datei *source.extension.vsixmanifest:*
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a>Natvis-Dateispeicherorte

Sie können *.natvis-Dateien* zu Ihrem Benutzerverzeichnis oder zu einem Systemverzeichnis hinzufügen, wenn sie auf mehrere Projekte angewendet werden sollen.

Die *.natvis-Dateien* werden in der folgenden Reihenfolge ausgewertet:

1. Alle *.natvis-Dateien,* die in eine *.pdb* eingebettet sind, die Sie debuggen, es sei denn, im geladenen Projekt ist eine Datei mit demselben Namen vorhanden.

2. Alle *.natvis-Dateien,* die sich in einem geladenen C++-Projekt oder einer Lösung der obersten Ebene befinden. Diese Gruppe umfasst alle geladenen C++-Projekte, einschließlich Klassenbibliotheken, jedoch keine Projekte in anderen Sprachen.

3. Alle *.natvis-Dateien,* die über ein VSIX-Paket installiert und registriert wurden.

::: moniker range="vs-2017"

4. Das benutzerspezifische Natvis-Verzeichnis (z. B. *%USERPROFILE%-Dokumente, Visual Studio 2017, Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

4. Das benutzerspezifische Natvis-Verzeichnis (z. B. *%USERPROFILE%-Dokumente, Visual Studio 2019, Visualizers*).

::: moniker-end

5. Das systemweite Natvis-Verzeichnis (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Dieses Verzeichnis enthält die *.natvis-Dateien,* die mit Visual Studio installiert sind. Wenn Sie über Administratorberechtigungen verfügen, können Sie diesem Verzeichnis Dateien hinzufügen.

## <a name="modify-natvis-files-while-debugging"></a>Ändern von .natvis-Dateien während des Debuggens

Sie können eine *.natvis-Datei* in der IDE ändern, während Sie ihr Projekt debuggen. Öffnen Sie die Datei in derselben Instanz von Visual Studio, mit der Sie debuggen, ändern Sie sie und speichern Sie sie. Sobald die Datei gespeichert ist, werden die Fenster **"Uhr"** und **"Lokale"** aktualisiert, um die Änderung widerzuspiegeln.

Sie können auch *.natvis-Dateien* in einer Projektmappe hinzufügen oder löschen, die Sie debuggen, und Visual Studio fügt die entsprechenden Visualisierungen hinzu oder entfernt sie.

Sie können *.natvis-Dateien,* die in *PDB-Dateien* eingebettet sind, während des Debuggens nicht aktualisieren.

Wenn Sie die *.natvis-Datei* außerhalb von Visual Studio ändern, werden die Änderungen nicht automatisch wirksam. Um die Debuggerfenster zu aktualisieren, können Sie den **Befehl .natvisreload** im **Direktfenster** erneut auswerten. Anschließend werden die Änderungen wirksam, ohne die Debugsitzung neu zu starten.

Verwenden Sie auch den Befehl **.natvisreload,** um die *.natvis-Datei* auf eine neuere Version zu aktualisieren. Beispielsweise kann die *.natvis-Datei* in die Quellcodeverwaltung eingecheckt werden, und Sie möchten die letzten Änderungen, die von jemand anderem vorgenommen wurden, aufgreifen.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> Ausdrücke und Formatierung
Natvis-Visualisierungen verwenden C++-Ausdrücke, um anzuzeigende Datenelementen anzugeben. Beachten Sie zusätzlich zu den Verbesserungen und Einschränkungen von C++-Ausdrücken im Debugger, die im [Context-Operator (C++)](../debugger/context-operator-cpp.md)beschrieben werden, Folgendes:

- Natvis-Ausdrücke werden im Kontext des Objekts ausgewertet, das in der Schnellansicht und nicht im aktuellen Stapelrahmen angezeigt wird. In einem `x` Natvis-Ausdruck wird beispielsweise auf das Feld mit dem Namen **x** im zu visualisierten Objekt und nicht auf eine lokale Variable mit dem Namen **x** in der aktuellen Funktion verweist. Sie können nicht auf lokale Variablen in Natvis-Ausdrücken zugreifen, obwohl Sie auf globale Variablen zugreifen können.

- Natvis-Ausdrücke erlauben keine Funktionsauswertung oder Nebenwirkungen. Funktionsaufrufe und Zuweisungsoperatoren werden ignoriert. Da [systeminterne Debuggerfunktionen](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) keine Nebeneffekte haben, können sie beliebig von jedem Natvis-Ausdruck aufgerufen werden, obwohl andere Funktionsaufrufe nicht zulässig sind.

- Um zu steuern, wie ein Ausdruck angezeigt wird, können Sie einen der formationsteller verwenden, die unter [Formatbezeichner in C++](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers)beschrieben sind. Formatbezeichner werden ignoriert, wenn der Eintrag intern von `Size` Natvis verwendet wird, z. B. der Ausdruck in einer [ArrayItems-Erweiterung](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

## <a name="natvis-views"></a>Natvis-Ansichten

Sie können verschiedene Natvis-Ansichten definieren, um Typen auf unterschiedliche Weise anzuzeigen. Hier ist z. B. eine Visualisierung, `std::vector` `simple`die eine vereinfachte Ansicht mit dem Namen definiert. Die `DisplayString` und `ArrayItems` die Elemente werden in `simple` der Standardansicht `[capacity]` und der Ansicht `simple` angezeigt, während die `[size]` und Elemente in der Ansicht nicht angezeigt werden.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

Verwenden Sie im **Überwachungsfenster** den Formatbezeichner **,view,** um eine alternative Ansicht anzugeben. Die einfache Ansicht erscheint als **vec,view(simple)**:

![Überwachungsfenster mit einfacher Ansicht](../debugger/media/watch-simpleview.png "Überwachungsfenster mit einfacher Ansicht")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a>Natvis-Fehler

Wenn der Debugger auf Fehler in einem Visualisierungseintrag stößt, werden diese ignoriert. Der Typ wird entweder in seiner Rohform angezeigt, oder er wählt eine andere geeignete Visualisierung aus. Sie können die Natvis-Diagnose verwenden, um zu verstehen, warum der Debugger einen Visualisierungseintrag ignoriert hat, und um die zugrunde liegende Syntax und Analysefehler anzuzeigen.

**So aktivieren Sie die Natvis-Diagnose:**

- Legen Sie unter > **Tools-Optionen** (oder **Tools** **Debugoptionen** > **Options**) > **Debugging-Ausgabefenster** > **Output Window** **Natvis-Diagnosemeldungen (nur C++)** auf **Fehler**, **Warnung**oder **Ausführlich**fest, und wählen Sie dann **OK**aus.

Die Fehler werden im **Ausgabefenster** angezeigt.

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a> Natvis-Syntaxverweis

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a>AutoVisualizer-Element
Bei dem `AutoVisualizer`-Element handelt es sich um den Stammknoten der *NATVIS*-Datei, der das `xmlns:`-Attribut für den Namespace enthält.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

Das `AutoVisualizer` Element kann über die untergeordneten [Elemente Type](#BKMK_Type), [HResult](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer)und [CustomVisualizer](#BKMK_CustomVisualizer) verfügen.

### <a name="type-element"></a><a name="BKMK_Type"></a>Typelement

Ein `Type` Basic sieht wie in diesem Beispiel aus:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 Das `Type` Element gibt Folgendes an:

1. Für welchen Typ die Visualisierung `Name` verwendet werden soll (das Attribut).

2. Wie der Wert eines Objekts dieses Typs aussehen soll (das `DisplayString` -Element).

3. Wie die Member des Typs aussehen sollen, wenn der Benutzer `Expand` den Typ in einem Variablenfenster (dem Knoten) erweitert.

#### <a name="templated-classes"></a>Vorlagenklassen
Das `Name` Attribut `Type` des Elements akzeptiert `*` ein Sternchen als Platzhalterzeichen, das für Vorlagenklassennamen verwendet werden kann.

Im folgenden Beispiel wird dieselbe Visualisierung verwendet, `CAtlArray<int>` unabhängig `CAtlArray<float>`davon, ob es sich bei dem Objekt um ein oder eine handelt. Wenn es einen bestimmten Visualisierungseintrag für eine `CAtlArray<float>`gibt, hat er Vorrang vor dem generischen.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

Sie können Vorlagenparameter im Visualisierungseintrag mithilfe von Makros $T1, $T2 usw. referenzieren. Beispiele zu diesen Makros finden Sie in den *NATVIS*-Dateien, die in Visual Studio bereitgestellt werden.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> Typenabgleich in der Schnellansicht
Wenn ein Visualisierungseintrag nicht überprüft werden kann, wird die nächste verfügbare Visualisierung verwendet.

#### <a name="inheritable-attribute"></a>Inheritable-Attribut
Das `Inheritable` optionale Attribut gibt an, ob eine Visualisierung nur für einen Basistyp oder für einen Basistyp und alle abgeleiteten Typen gilt. Der Standardwert von `Inheritable` lautet `true`.

Im folgenden Beispiel gilt die Visualisierung `BaseClass` nur für den Typ:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Priority-Attribut

Das `Priority` optionale Attribut gibt die Reihenfolge an, in der alternative Definitionen verwendet werden sollen, wenn eine Definition nicht analysiert werden kann. Die möglichen `Priority` Werte `Low`von `MediumLow``Medium`sind: , , , `MediumHigh`, und `High`. Der Standardwert ist `Medium`. Das `Priority` Attribut unterscheidet nur zwischen Prioritäten innerhalb derselben *.natvis-Datei.*

Im folgenden Beispiel wird zunächst der Eintrag analysiert, der mit der STL 2015 übereinstimmt. Wenn dies nicht analysiert werden kann, wird der alternative Eintrag für die Version 2013 der STL verwendet:

```xml
<!-- VC 2013 -->
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">
     <DisplayString>{_Callee}</DisplayString>
    <Expand>
        <ExpandedItem>_Callee</ExpandedItem>
    </Expand>
</Type>

<!-- VC 2015 -->
<Type Name="std::reference_wrapper&lt;*&gt;">
    <DisplayString>{*_Ptr}</DisplayString>
    <Expand>
        <Item Name="[ptr]">_Ptr</Item>
    </Expand>
</Type>
```

### <a name="optional-attribute"></a>Optional-Attribut
Sie können `Optional` ein Attribut auf jedem Knoten setzen. Wenn ein Unterausdruck innerhalb eines optionalen Knotens nicht analysiert werden kann, ignoriert `Type` der Debugger diesen Knoten, wendet jedoch die restlichen Regeln an. Im folgenden Typ ist `[State]` nicht optional, während `[Exception]` jedoch optional ist.  Wenn `MyNamespace::MyClass` ein Feld`M_exceptionHolder`mit dem `[State]` Namen `[Exception]` _ angezeigt wird, werden `_M_exceptionHolder` sowohl der `[State]` Knoten als auch der Knoten angezeigt, aber wenn kein Feld vorhanden ist, wird nur der Knoten angezeigt.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a>Bedingungsattribut

Das `Condition` optionale Attribut ist für viele Visualisierungselemente verfügbar und gibt an, wann eine Visualisierungsregel verwendet werden soll. Wenn der Ausdruck innerhalb des `false`Bedingungsattributs in aufgelöst wird, wird die Visualisierungsregel nicht angewendet. Wenn es zu `true`ausgewertet wird `Condition` oder kein Attribut vorhanden ist, wird die Visualisierung angewendet. Sie können dieses Attribut für if-else-Logik in den Visualisierungseinträgen verwenden.

Die folgende Visualisierung enthält `DisplayString` z. B. zwei Elemente für einen intelligenten Zeigertyp. Wenn `_Myptr` das Element leer ist, `DisplayString` wird die `true`Bedingung des ersten Elements in aufgelöst, sodass das Formular angezeigt wird. Wenn `_Myptr` das Element nicht leer ist, `false`wird die `DisplayString` Bedingung zu ausgewertet, und das zweite Element wird angezeigt.

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

### <a name="includeview-and-excludeview-attributes"></a>IncludeView- und ExcludeView-Attribute

Die `IncludeView` `ExcludeView` und Attribute geben Elemente an, die in bestimmten Ansichten angezeigt oder nicht angezeigt werden sollen. In der folgenden Natvis-Spezifikation `std::vector`von `simple` wird z. `[size]` B. die Ansicht `[capacity]` nicht angezeigt.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

Sie können `IncludeView` die `ExcludeView` und attribute für Typen und für einzelne Member verwenden.

### <a name="version-element"></a><a name="BKMK_Versioning"></a>Versionselement
Das `Version` Element enthält einen Visualisierungseintrag für ein bestimmtes Modul und eine bestimmte Version. Das `Version` Element hilft, Namenskonflikte zu vermeiden, reduziert unbeabsichtigte Nichtübereinstimmungen und ermöglicht unterschiedliche Visualisierungen für verschiedene Typversionen.

Wenn eine gemeinsame Headerdatei, die von verschiedenen Modulen verwendet wird, einen Typ definiert, wird die versionierte Visualisierung nur angezeigt, wenn sich der Typ in der angegebenen Modulversion befindet.

Im folgenden Beispiel ist die Visualisierung `DirectUI::Border` nur für `Windows.UI.Xaml.dll` den Typ von Version 1.0 bis 1.5 anwendbar.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Sie brauchen nicht `Min` beides und `Max`. Es handelt sich um optionale Attribute. Es werden keine Platzhalterzeichen unterstützt.

Das `Name` Attribut hat das Format *filename.ext*, z. *B. hello.exe* oder *some.dll*. Es sind keine Pfadnamen zulässig.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a>DisplayString-Element
Das `DisplayString` Element gibt eine Zeichenfolge an, die als Wert einer Variablen angezeigt werden soll. Beliebige Zeichenfolgen können mit Ausdrücken gemischt werden. Sämtliche Inhalte innerhalb von geschweiften Klammern werden als ein Ausdruck interpretiert. Zum Beispiel der `DisplayString` folgende Eintrag:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Bedeutet, dass `CPoint` Variablen des Typs wie in dieser Abbildung angezeigt werden:

 ![Verwenden eines DisplayString-Elements](../debugger/media/dbg_natvis_cpoint_displaystring.png "Verwenden eines DisplayString-Elements")

Im `DisplayString` Ausdruck `x` und `y`, die `CPoint`Member von sind, befinden sich in geschweiften Klammern, sodass ihre Werte ausgewertet werden. Das Beispiel zeigt auch, wie Sie eine geschweifte `{{` Geschweifklammer mit doppelten geschweiften Klammern ( oder `}}` ) entkommen können.

> [!NOTE]
> Das `DisplayString` -Element ist das einzige Element, das beliebige Zeichenfolgen und die Syntax mit geschweiften Klammern akzeptiert. Alle anderen Visualisierungselemente akzeptieren nur Ausdrücke, die der Debugger auswerten kann.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a>StringView-Element

Das `StringView` Element definiert einen Wert, den der Debugger an die integrierte Textvisualisierung senden kann. Beispielsweise wird die folgende Visualisierung `ATL::CStringT` für den Typ angezeigt:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

Das `CStringT` Objekt wird in einem Variablenfenster wie in diesem Beispiel angezeigt:

![CStringT-DisplayString-Element](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT-DisplayString-Element")

Durch `StringView` Hinzufügen eines Elements kann der Wert als Textvisualisierung angezeigt werden.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Während des Debuggens können Sie das Lupensymbol neben der Variablen auswählen und dann **Textvisualizer** auswählen, um die Zeichenfolge anzuzeigen, auf **die m_pszData** zeigt.

 ![CStringT-Daten mit StringView-Schnellansicht](../debugger/media/dbg_natvis_stringview_cstringt.png "CStringT-Daten mit StringView-Schnellansicht")

Der `{m_pszData,su}` Ausdruck enthält einen C++-Formatbezeichner **su**, um den Wert als Unicode-Zeichenfolge anzuzeigen. Weitere Informationen finden Sie unter [Formatbezeichner in C++](../debugger/format-specifiers-in-cpp.md).

### <a name="expand-element"></a><a name="BKMK_Expand"></a>Expand-Element

Der `Expand` optionale Knoten passt die untergeordneten Elemente eines visualisierten Typs an, wenn Sie den Typ in einem Variablenfenster erweitern. Der `Expand` Knoten akzeptiert eine Liste der untergeordneten Knoten, die die untergeordneten Elemente definieren.

- Wenn `Expand` ein Knoten nicht in einem Visualisierungseintrag angegeben ist, verwenden die untergeordneten Elemente die Standarderweiterungsregeln.

- Wenn `Expand` ein Knoten ohne untergeordnete Knoten angegeben wird, ist der Typ in den Debuggerfenstern nicht erweiterbar.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> Item-Erweiterung

 Das `Item` Element ist das einfachste und `Expand` gebräuchlichste Element in einem Knoten. Das`Item` -Element definiert ein einzelnes untergeordnetes Element. Eine `CRect` Klasse mit den `top` `left`Feldern `right`, `bottom` , und verfügt beispielsweise über den folgenden Visualisierungseintrag:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

Im Debuggerfenster sieht `CRect` der Typ wie folgt aus:

![CRect mit Item-Element-Erweiterung](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect mit Item-Element-Erweiterung")

Der Debugger wertet die `Width` in `Height` der und-Elemente angegebenen Ausdrücke aus und zeigt die Werte in der Spalte **Wert** des Variablenfensters an.

Der Debugger erstellt automatisch den **Knoten [Raw View]** für jede benutzerdefinierte Erweiterung. Im vorherigen Screenshot wird der erweiterte **Knoten [Rohansicht]** angezeigt, um zu zeigen, wie sich die Standard-Rohansicht des Objekts von der Natvis-Visualisierung unterscheidet. Die Standarderweiterung erstellt eine Unterstruktur für die Basisklasse und listet alle Datenmember der Basisklasse als untergeordnete Elemente auf.

> [!NOTE]
> Wenn der Ausdruck des Elementelements auf einen komplexen Typ verweist, kann der **Elementknoten** selbst erweiterbar sein.

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a> ArrayItems expansion
Verwenden Sie den `ArrayItems` -Knoten, damit der Visual Studio-Debugger den Typ als Array interpretieren und die einzelnen Elemente anzeigen kann. Die Visualisierung für `std::vector` ist ein gutes Beispiel:

```xml
<Type Name="std::vector&lt;*&gt;">
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mylast - _Myfirst</Item>
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>
    <ArrayItems>
      <Size>_Mylast - _Myfirst</Size>
      <ValuePointer>_Myfirst</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

Im `std::vector` -Knoten werden die einzelnen Elemente angezeigt, wenn sie im Variablenfenster erweitert werden:

![std::vector mit ArrayItems-Erweiterung](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vector mit ArrayItems-Erweiterung")

Der `ArrayItems` Knoten muss über Folgendes verfügen:

- Einen `Size`-Ausdruck (der als ganze Zahl ausgewertet werden muss), damit der Debugger die Länge des Arrays kennt.
- Ein `ValuePointer` Ausdruck, der auf das erste Element verweist (der ein `void*`Zeiger eines Elementtyps sein muss, der nicht ).

Der Standardwert mit der Arrayuntergrenze lautet „0“. Um den Wert zu `LowerBound` überschreiben, verwenden Sie ein Element. Die mit Visual Studio ausgelieferten *.natvis-Dateien* haben Beispiele.

>[!NOTE]
>Sie können `[]` den Operator `vector[i]`z. B. mit jeder `ArrayItems`eindimensionalen Arrayvisualisierung verwenden, `CATLArray`die verwendet, auch wenn der Typ selbst (z. B.) diesen Operator nicht zulässt.

Sie können auch mehrdimensionale Arrays angeben. In diesem Fall benötigt der Debugger etwas mehr Informationen, um untergeordnete Elemente korrekt anzuzeigen:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Direction>Forward</Direction>
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

- `Direction`gibt an, ob das Array in Zeilen-Haupt- oder Spalten-Großauftrag ist.
- `Rank` gibt den Rang des Arrays an.
- Das `Size`-Element akzeptiert den impliziten `$i`-Parameter, der durch den Dimensionsindex ersetzt wird, um die Länge des Arrays in dieser Dimension festzustellen. Im vorherigen Beispiel sollte `_M_extent.M_base[0]` der Ausdruck die Länge der `_M_extent._M_base[1]` 0. Dimension, die 1. usw. geben.

So sieht ein zweidimensionales `Concurrency::array` Objekt im Debuggerfenster aus:

![Zweidimensionales Array mit ArrayItems-Erweiterung](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Zweidimensionales Array mit ArrayItems-Erweiterung")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a>IndexListItems-Erweiterung

Sie können `ArrayItems` die Erweiterung nur verwenden, wenn die Arrayelemente zusammenhängend im Speicher angeordnet sind. Der Debugger erhält das nächste Element, indem er einfach seinen Zeiger erhöht. Wenn Sie den Index für den Wertknoten bearbeiten müssen, verwenden Sie `IndexListItems` Knoten. Hier ist eine Visualisierung `IndexListItems` mit einem Knoten:

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_M_vector._M_index</Item>
    <IndexListItems>
      <Size>_M_vector._M_index</Size>
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>
    </IndexListItems>
  </Expand>
</Type>
```

Der einzige `ArrayItems` Unterschied `IndexListItems` zwischen `ValueNode`und ist die , die den vollständigen `$i` Ausdruck für das i<sup>th-Element</sup> mit dem impliziten Parameter erwartet.

>[!NOTE]
>Sie können `[]` den Operator `vector[i]`z. B. mit jeder `IndexListItems`eindimensionalen Arrayvisualisierung verwenden, `CATLArray`die verwendet, auch wenn der Typ selbst (z. B.) diesen Operator nicht zulässt.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> LinkedListItems-Erweiterung

Wenn der Schnellansichtstyp eine verknüpfte Liste darstellt, kann der Debugger die untergeordneten Elemente mithilfe eines `LinkedListItems` -Knotens anzeigen. Die folgende Visualisierung `CAtlList` für `LinkedListItems`den Typ verwendet:

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>
  <Expand>
    <Item Name="Count">m_nElements</Item>
    <LinkedListItems>
      <Size>m_nElements</Size>
      <HeadPointer>m_pHead</HeadPointer>
      <NextPointer>m_pNext</NextPointer>
      <ValueNode>m_element</ValueNode>
    </LinkedListItems>
  </Expand>
</Type>
```

Das `Size` -Element bezieht sich auf die Länge der Liste. `HeadPointer` zeigt auf das erste Element, `NextPointer` bezieht sich auf das nächste Element, und `ValueNode` verweist auf den Wert des Elements.

Der Debugger wertet die `NextPointer` und `ValueNode` Ausdrücke im Kontext des `LinkedListItems` Knotenelements aus, nicht den übergeordneten Listentyp. Im vorherigen Beispiel `CAtlList` verfügt `CNode` über eine `atlcoll.h`Klasse (gefunden in ), die ein Knoten der verknüpften Liste ist. `m_pNext`und `m_element` sind Felder `CNode` dieser Klasse, `CAtlList` nicht der Klasse.

`ValueNode`kann leer gelassen werden, oder `this` `LinkedListItems` verwenden, um auf den Knoten selbst zu verweisen.

#### <a name="customlistitems-expansion"></a>CustomListItems-Erweiterung

Die `CustomListItems` -Erweiterung ermöglicht Ihnen das Schreiben von benutzerdefinierter Logik für das Traversieren einer Datenstruktur, beispielsweise einer Hashtabelle. Verwenden `CustomListItems` Sie diese Funktion zum Visualisieren von Datenstrukturen, die C++-Ausdrücke für `ArrayItems` `IndexListItems`alles `LinkedListItems`verwenden können, was Sie auswerten müssen, aber nicht ganz in die Form für , oder passen.

Sie können `Exec` Code innerhalb einer `CustomListItems` Erweiterung mithilfe der in der Erweiterung definierten Variablen und Objekte ausführen. Sie können logische Operatoren, arithmetische Operatoren und Zuweisungsoperatoren mit `Exec`verwenden. Sie können keine `Exec` Funktionen auswerten, außer für [systeminterne Debuggerfunktionen,](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) die vom C++-Ausdrucksauswertungswert unterstützt werden.

Die folgende Visualisierung `CAtlMap` für ist `CustomListItems` ein ausgezeichnetes Beispiel, wo es angebracht ist.

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>
    <Expand>
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">
        <Variable Name="iBucket" InitialValue="-1" />
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />
        <Variable Name="iBucketIncrement" InitialValue="-1" />

        <Size>m_nElements</Size>
        <Exec>pBucket = nullptr</Exec>
        <Loop>
          <If Condition="pBucket == nullptr">
            <Exec>iBucket++</Exec>
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>
            <Break Condition="iBucketIncrement == -1" />
            <Exec>iBucket += iBucketIncrement</Exec>
            <Exec>pBucket = m_ppBins[iBucket]</Exec>
          </If>
          <Item>pBucket,na</Item>
          <Exec>pBucket = pBucket->m_pNext</Exec>
        </Loop>
      </CustomListItems>
    </Expand>
</Type>
```

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a> TreeItems-Erweiterung
 Wenn der Schnellansichtstyp eine Struktur darstellt, kann der Debugger die Struktur durchlaufen und seine untergeordneten Elemente mithilfe eines `TreeItems` -Knotens anzeigen. Hier ist die Visualisierung `std::map` für `TreeItems` den Typ mit einem Knoten:

```xml
<Type Name="std::map&lt;*&gt;">
  <DisplayString>{{size = {_Mysize}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mysize</Item>
    <Item Name="[comp]">comp</Item>
    <TreeItems>
      <Size>_Mysize</Size>
      <HeadPointer>_Myhead->_Parent</HeadPointer>
      <LeftPointer>_Left</LeftPointer>
      <RightPointer>_Right</RightPointer>
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>
    </TreeItems>
  </Expand>
</Type>
```

Die Syntax ähnelt `LinkedListItems` dem Knoten. `LeftPointer`, `RightPointer`und `ValueNode` werden im Kontext der Strukturknotenklasse ausgewertet. `ValueNode`kann leer gelassen `this` werden oder `TreeItems` verwendet werden, um auf den Knoten selbst zu verweisen.

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a>ExpandedItem-Erweiterung
 Das `ExpandedItem` Element generiert eine aggregierte untergeordnete Ansicht, indem Eigenschaften von Basisklassen oder Datenmembern angezeigt werden, als wären sie untergeordnete Elemente des visualisierten Typs. Der Debugger wertet den angegebenen Ausdruck aus und fügt die untergeordneten Knoten des Ergebnisses an die untergeordnete Liste des visualisierten Typs an.

Der Smart Pointer-Typ `auto_ptr<vector<int>>` wird z. B. in der Regel wie:

 ![auto&#95;ptr&#60;Vector&#60;int&#62;&#62; Standarderweiterung](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Standarderweiterung")

 Um die Werte des Vektors anzuzeigen, müssen Sie zwei Ebenen im `_Myptr` Variablenfenster durch das Element führen. Durch Hinzufügen eines `ExpandedItem`-Elements können Sie die `_Myptr`-Variable aus der Hierarchie ausschließen und die Vektorelemente direkt anzeigen:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![auto&#95;ptr&#60;vector&#60;int&#62;&#62; ExpandedItem-Erweiterung](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "ExpandedItem-Erweiterung")

Das folgende Beispiel zeigt, wie Eigenschaften aus der Basisklasse in einer abgeleiteten Klasse aggregiert werden. Angenommen, die `CPanel` -Klasse wird von `CFrameworkElement`abgeleitet. Anstatt die Eigenschaften zu wiederholen, `CFrameworkElement` die `ExpandedItem` von der Basisklasse stammen, fügt `CPanel` die Knotenvisualisierung diese Eigenschaften an die untergeordnete Liste der Klasse an.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Hier **nd** ist der nd-Formatbezeichner erforderlich, der den Visualisierungsabgleich für die abgeleitete Klasse deaktiviert. Andernfalls würde `*(CFrameworkElement*)this` der Ausdruck `CPanel` dazu führen, dass die Visualisierung erneut angewendet wird, da die standardmäßigen Regeln für die Zuordnung des Visualisierungstyps dies als die am besten geeignete betrachten. Verwenden **nd** Sie den nd-Formatbezeichner, um den Debugger anzuweisen, die Visualisierung der Basisklasse oder die Standarderweiterung zu verwenden, wenn die Basisklasse keine Visualisierung hat.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a> Synthetische Elementerweiterung
 Während das `ExpandedItem`-Element eine flachere Datenansicht durch die Beseitigung von Hierarchien bereitstellt, bewirkt der `Synthetic`-Knoten das Gegenteil. Sie können ein künstliches untergeordnetes Element erstellen, das kein Ergebnis eines Ausdrucks ist. Das künstliche Element kann eigene untergeordnete Elemente haben. Im folgenden Beispiel verwendet die Visualisierung für den `Concurrency::array` -Typ einen `Synthetic` -Knoten, um dem Benutzer eine Diagnosemeldung anzuzeigen:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>
    </Synthetic>
  </Expand>
</Type>
```

 ![Parallelität::Array mit synthetischer Elementerweiterung](../debugger/media/dbg_natvis_expand_synthetic.png "Parallelität::Array mit synthetischer Elementerweiterung")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a>HResult-Element
 Mit `HResult` dem Element können Sie die für ein **HRESULT** angezeigten Informationen in Debuggerfenstern anpassen. Das `HRValue` Element muss den 32-Bit-Wert des zu befolgenden **HRESULT** enthalten. Das `HRDescription` Element enthält die Informationen, die im Debuggerfenster angezeigt werden sollen.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a>UIVisualizer-Element
Ein `UIVisualizer` -Element registriert ein grafisches Schnellansichts-Plug-In mit dem Debugger. Eine grafische Visualisierung erstellt ein Dialogfeld oder eine andere Schnittstelle, die eine Variable oder ein Objekt in einer Weise anzeigt, die mit ihrem Datentyp übereinstimmt. Das Visualizer-Plug-In muss als [VSPackage](../extensibility/internals/vspackages.md)erstellt und einen Dienst verfügbar machen, den der Debugger verwenden kann. Die *.natvis-Datei* enthält Registrierungsinformationen für das Plug-In, z. B. den Namen, die GUID des verfügbar gemachten Dienstes und die Typen, die es visualisieren kann.

Im Folgenden ist ein Beispiel eines UIVisualizer-Elements angegeben:

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="1" MenuName="Vector Visualizer"/>
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="2" MenuName="List Visualizer"/>
.
.
</AutoVisualizer>
```

- `ServiceId`  -  Ein `Id` Attributpaar `UIVisualizer`identifiziert eine . Die `ServiceId` ist die GUID des Dienstes, den das Visualizerpaket verfügbar macht. `Id`ist ein eindeutiger Bezeichner, der Visualisierer unterscheidet, wenn ein Dienst mehr als einen bereitstellt. Im vorherigen Beispiel stellt derselbe Visualisierungsdienst zwei Visualizer bereit.

- Das `MenuName` Attribut definiert einen Visualisierungsnamen, der in der Dropdownliste neben dem Lupensymbol im Debugger angezeigt werden soll. Beispiel:

  ![Kontextmenü des UIVisualizer-Menüs](../debugger/media/dbg_natvis_vectorvisualizer.png "Kontextmenü des UIVisualizer-Menüs")

Jeder in der *.natvis-Datei* definierte Typ muss explizit alle UI-Visualisierungen auflisten, die ihn anzeigen können. Der Debugger gleicht die Visualisierungsreferenzen in den Typeinträgen mit den registrierten Visualisierern ab. Der folgende Typeintrag für `std::vector` Verweise `UIVisualizer` auf die im vorherigen Beispiel.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Sie können ein Beispiel `UIVisualizer` für eine in der [Image Watch-Erweiterung](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) sehen, die zum Anzeigen von In-Memory-Bitmaps verwendet wird.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>CustomVisualizer-Element
 `CustomVisualizer`ist ein Erweiterbarkeitspunkt, der eine VSIX-Erweiterung angibt, die Sie schreiben, um Visualisierungen in Visual Studio-Code zu steuern. Weitere Informationen zum Schreiben von VSIX-Erweiterungen finden Sie im [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Es ist viel mehr Arbeit, eine benutzerdefinierte Visualisierung zu schreiben als eine XML-Natvis-Definition, aber Sie sind frei von Einschränkungen darüber, was Natvis tut oder nicht unterstützt. Benutzerdefinierte Visualisierungen haben Zugriff auf den vollständigen Satz von Debugger-Erweiterbarkeits-APIs, die den Debuggee-Prozess abfragen und ändern oder mit anderen Teilen von Visual Studio kommunizieren können.

 Sie können `Condition`die `IncludeView`, `ExcludeView` und `CustomVisualizer` Attribute für Elemente verwenden.

 ## <a name="limitations"></a>Einschränkungen

Natvis-Anpassungen funktionieren mit Klassen und Strukturen, jedoch nicht mit typedefs.

Natvis unterstützt keine Visualisierungen für primitive Typen `int` `bool`(z. B. , ) oder für Zeiger auf primitive Typen. In diesem Szenario besteht eine Option darin, den [Formatbezeichner](../debugger/format-specifiers-in-cpp.md) zu verwenden, der für Ihren Anwendungsfall geeignet ist. Wenn Sie z. `double* mydoublearray` B. in Ihrem Code verwenden, können Sie einen Arrayformatbezeichner im `mydoublearray, [100]` **Überwachungsfenster** des Debuggers verwenden, z. B. den Ausdruck , der die ersten 100 Elemente anzeigt.
