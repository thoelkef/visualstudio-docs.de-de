---
title: Erstellen benutzerdefinierter Ansichten von C++-Objekten
description: Verwenden Sie das natvis-Framework, um die Art und Weise anzupassen, in der Visual Studio systemeigene Typen im Debugger anzeigt.
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
ms.openlocfilehash: 064761d87b9aa851e40cf906e7734a3578dcad1a
ms.sourcegitcommit: 9eff8371b7a79a637ebb6850f775dd3eed343d8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2020
ms.locfileid: "78234968"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Erstellen benutzerdefinierter Ansichten C++ von Objekten im Debugger mit dem natvis-Framework

Das *natvis* -Framework von Visual Studio passt die Art und Weise an **, in der**systemeigene Typen in Variablen **Fenstern des** Debuggers angezeigt werden, z. b. die Fenster "lokal" und "über **Wachen** " Natvis-Visualisierungen können dabei helfen, die von Ihnen erstellten Typen während des Debuggens besser sichtbar zu machen.

Natvis ersetzt die Datei *autoexp. dat* in früheren Versionen von Visual Studio durch XML-Syntax, bessere Diagnosefunktionen, Versionskontrolle und Unterstützung mehrerer Dateien.

> [!NOTE]
> Natvis-Anpassungen arbeiten mit Klassen und Strukturen, jedoch nicht mit Typedefs.

## <a name="BKMK_Why_create_visualizations_"></a>Natvis-Visualisierungen

Sie verwenden das natvis-Framework zum Erstellen von Visualisierungs Regeln für die Typen, die Sie erstellen, damit Entwickler diese während des Debuggens leichter sehen können.

Die folgende Abbildung zeigt beispielsweise eine Variable des Typs [Windows:: UI:: XAML:: Controls:: TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) in einem Debuggerfenster ohne angewendete benutzerdefinierte Visualisierungen.

![Standardmäßige TextBox-Visualisierung](../debugger/media/dbg_natvis_textbox_default.png "TextBox-Standardvisualisierung")

Die hervorgehobene Zeile zeigt die `Text` -Eigenschaft der `TextBox` -Klasse. Die komplexe Klassenhierarchie erschwert das Auffinden dieser Eigenschaft. Der Debugger kennt nicht die Interpretation des benutzerdefinierten Zeichen folgen Typs, sodass die Zeichenfolge nicht im Textfeld angezeigt wird.

Das gleiche `TextBox` sieht im Variablen Fenster viel einfacher aus, wenn die benutzerdefinierten natvis-Visualisierungs Regeln angewendet werden. Die wichtigen Member der-Klasse werden zusammengeh eitet, und der Debugger zeigt den zugrunde liegenden Zeichen folgen Wert des benutzerdefinierten Zeichen folgen Typs an.

![TextBox-Daten mithilfe von Visualisierungen](../debugger/media/dbg_natvis_textbox_visualizer.png "TextBox-Daten mit Schnellansicht")

## <a name="BKMK_Using_Natvis_files"></a>Verwenden von natvis-Dateien C++ in Projekten

Natvis verwendet *natvis* -Dateien zum Angeben von Visualisierungs Regeln. Eine *natvis* -Datei ist eine XML-Datei mit der Erweiterung " *. natvis* ". Das natvis-Schema ist in *%VSInstallDir%\xml\schemas\natvis.xsd*definiert.

Die grundlegende Struktur einer *natvis* -Datei ist ein oder mehrere `Type` Elemente, die Visualisierungs Einträge darstellen. Der voll qualifizierte Name der einzelnen `Type`-Elemente wird in Ihrem `Name`-Attribut angegeben.

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

Visual Studio stellt einige *natvis* -Dateien im Ordner *%VSInstallDir%\common7\packages\debugger\visualizers* bereit. Diese Dateien enthalten Visualisierungs Regeln für viele allgemeine Typen und können als Beispiele für das Schreiben von Visualisierungen für neue Typen dienen.

### <a name="add-a-natvis-file-to-a-c-project"></a>Hinzufügen einer natvis-Datei zu C++ einem Projekt

Sie können einem beliebigen C++ Projekt eine *natvis* -Datei hinzufügen.

**So fügen Sie eine neue *natvis* -Datei hinzu:**

1. Wählen Sie C++ den Projekt Knoten in **Projektmappen-Explorer**aus, und wählen Sie **Projekt** > **Neues Element hinzufügen**aus, oder **Klicken Sie mit** der rechten Maustaste auf das Projekt, und wählen Sie dann > **Neues Element**

1. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option  **C++ Visual** > - **Hilfsprogramm** > **Debugger-Visualisierungs Datei (. natvis)** aus.

1. Benennen Sie die Datei, und wählen Sie **Hinzufügen**aus.

   Die neue Datei wird **Projektmappen-Explorer**hinzugefügt und im Dokumentbereich von Visual Studio geöffnet.

Der Visual Studio-Debugger lädt *natvis* -Dateien C++ automatisch in-Projekten und schließt diese standardmäßig auch in die *PDB* -Datei ein, wenn das Projekt erstellt wird. Wenn Sie die erstellte App Debuggen, lädt der Debugger die *natvis* -Datei aus der *PDB* -Datei, auch wenn Sie das Projekt nicht geöffnet haben. Wenn Sie nicht möchten, dass die *natvis* -Datei in der *PDB*-Datei enthalten ist, können Sie Sie aus der erstellten *PDB* -Datei ausschließen.

**So schließen Sie eine *natvis* -Datei aus einer *PDB*-Datei aus:**

1. Wählen Sie in **Projektmappen-Explorer**die *natvis* -Datei aus, und wählen Sie das Symbol **Eigenschaften** aus, oder klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie **Eigenschaften**

1. Legen Sie den Pfeil neben **aus Build ausgeschlossen** fest, wählen Sie **Ja**aus, und klicken Sie dann auf **OK**.

>[!NOTE]
>Verwenden Sie zum Debuggen von ausführbaren Projekten die Projektmappenelemente, um *natvis* -Dateien hinzuzufügen, die sich nicht in der C++ *PDB*-Datei befinden, da kein Projekt verfügbar ist.

>[!NOTE]
>Aus einer *PDB* -Datei geladene natvis-Regeln gelten nur für die Typen in den Modulen, auf die sich die *PDB* -Datei bezieht. Wenn z. b *. "Module1. pdb* " einen natvis-Eintrag für einen Typ mit dem Namen "`Test`" enthält, gilt dies nur für die `Test` Klasse in " *Module1. dll*". Wenn ein anderes Modul auch eine Klasse mit dem Namen `Test`definiert, gilt der *Module1. pdb* -natvis-Eintrag nicht für den Eintrag.

**So installieren und registrieren Sie eine *natvis* -Datei über ein VSIX-Paket:**

Mit einem VSIX-Paket können *natvis* -Dateien installiert und registriert werden. Unabhängig davon, wo Sie installiert sind, werden alle registrierten *natvis* -Dateien beim Debuggen automatisch abgerufen.

1. Schließen Sie die *natvis* -Datei in das VSIX-Paket ein. Beispielsweise für die folgende Projektdatei:
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. Registrieren Sie die *natvis* -Datei in der Datei " *Source. Extension. vsixmanifest* ":
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="BKMK_natvis_location"></a>Natvis-Dateispeicher Orte

Sie können *natvis* -Dateien zu Ihrem Benutzerverzeichnis oder einem System Verzeichnis hinzufügen, wenn Sie für mehrere Projekte gelten sollen.

Die *natvis* -Dateien werden in der folgenden Reihenfolge ausgewertet:

1. Alle *natvis* -Dateien, die in eine *PDB* -Datei eingebettet sind, die Sie Debuggen, es sei denn, im geladenen Projekt ist eine Datei mit demselben Namen vorhanden.

2. Alle *natvis* -Dateien, die sich in einem C++ geladenen Projekt oder auf der obersten Ebene befinden. Diese Gruppe enthält alle geladenen C++ Projekte, einschließlich Klassenbibliotheken, aber keine Projekte in anderen Sprachen.

3. Alle *natvis* -Dateien, die über ein VSIX-Paket installiert und registriert wurden.

::: moniker range="vs-2017"

4. Das benutzerspezifische natvis-Verzeichnis (z. b. *%USERPROFILE%\Documents\Visual Studio 2017 \ Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

4. Das benutzerspezifische natvis-Verzeichnis (z. b. *%USERPROFILE%\Documents\Visual Studio 2019 \ Visualizers*).

::: moniker-end

5. Das systemweite Natvis-Verzeichnis ( *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Dieses Verzeichnis enthält die *natvis* -Dateien, die mit Visual Studio installiert werden. Wenn Sie über Administrator Berechtigungen verfügen, können Sie diesem Verzeichnis Dateien hinzufügen.

## <a name="modify-natvis-files-while-debugging"></a>Ändern von natvis-Dateien beim Debuggen

Sie können eine *natvis* -Datei in der IDE ändern, während Sie das Projekt Debuggen. Öffnen Sie die Datei in derselben Instanz von Visual Studio, in der Sie Debuggen, ändern Sie Sie, und speichern Sie Sie. Sobald die Datei gespeichert ist, werden die Änderungen überwachen **und lokal** aktualisiert, um die Änderung widerzuspiegeln.

Außerdem können Sie *natvis* -Dateien in einer Projekt Mappe hinzufügen oder löschen, die Sie Debuggen, und Visual Studio fügt die relevanten Visualisierungen hinzu bzw. entfernt Sie.

Sie können keine *natvis* -Dateien aktualisieren, die in *PDB* -Dateien eingebettet sind, während Sie Debuggen.

Wenn Sie die *natvis* -Datei außerhalb von Visual Studio ändern, werden die Änderungen nicht automatisch wirksam. Zum Aktualisieren der Debuggerfenster können Sie den Befehl **. natvisreload** im Fenster über **Wachen** neu auswerten. Dann werden die Änderungen wirksam, ohne dass die Debugsitzung neu gestartet wird.

Verwenden Sie auch den Befehl **. natvisreload** , um die *natvis* -Datei auf eine neuere Version zu aktualisieren. Beispielsweise kann die *natvis* -Datei in die Quell Code Verwaltung eingecheckt werden, und Sie möchten die kürzlich von einem anderen Element vorgenommenen Änderungen übernehmen.

## <a name="BKMK_Expressions_and_formatting"></a> Ausdrücke und Formatierung
Natvis-Visualisierungen verwenden C++-Ausdrücke, um anzuzeigende Datenelementen anzugeben. Zusätzlich zu den Erweiterungen und Einschränkungen von C++ Ausdrücken im Debugger, die im [Kontext Operator (C++)](../debugger/context-operator-cpp.md)beschrieben werden, sollten Sie Folgendes beachten:

- Natvis-Ausdrücke werden im Kontext des Objekts ausgewertet, das in der Schnellansicht und nicht im aktuellen Stapelrahmen angezeigt wird. `x` in einem natvis-Ausdruck bezieht sich z. b. auf das Feld " **x** " in dem Objekt, das visualisiert wird, und nicht auf eine lokale Variable mit dem Namen " **x** " in der aktuellen Funktion. Sie können nicht auf lokale Variablen in natvis-Ausdrücken zugreifen, obwohl Sie auf globale Variablen zugreifen können.

- Natvis-Ausdrücke lassen keine Funktions Auswertung oder Nebeneffekte zu. Funktionsaufrufe und Zuweisungs Operatoren werden ignoriert. Da [systeminterne Debuggerfunktionen](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) keine Nebeneffekte haben, können sie beliebig von jedem Natvis-Ausdruck aufgerufen werden, obwohl andere Funktionsaufrufe nicht zulässig sind.

- Um zu steuern, wie ein Ausdruck angezeigt wird, können Sie einen beliebigen Format Bearbeiter verwenden, der in [Formatspezifizierer in C++ ](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers)beschrieben wird. Format Bezeichner werden ignoriert, wenn der Eintrag intern von natvis verwendet wird, z. b. der `Size` Ausdruck in einer [arrayitems-Erweiterung](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

## <a name="natvis-views"></a>Natvis-Ansichten

Sie können verschiedene natvis-Sichten definieren, um Typen auf unterschiedliche Weise anzuzeigen. Hier ist beispielsweise eine Visualisierung von `std::vector`, die eine vereinfachte Ansicht mit dem Namen `simple`definiert. Die `DisplayString` und die `ArrayItems` Elemente werden in der Standardansicht und in der `simple` Ansicht angezeigt, während die `[size]`-und `[capacity]` Elemente in der `simple` Ansicht nicht angezeigt werden.

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

Verwenden Sie im Fenster über **Wachen** den Format Bezeichner der **Anzeige,** um eine Alternative Ansicht anzugeben. Die einfache Ansicht wird als **VEC, View (Simple)** angezeigt:

![Überwachungsfenster mit einfacher Ansicht](../debugger/media/watch-simpleview.png "Überwachungsfenster mit einfacher Ansicht")

## <a name="BKMK_Diagnosing_Natvis_errors"></a>Natvis-Fehler

Wenn der Debugger Fehler in einem Visualisierungs Eintrag erkennt, werden diese ignoriert. Der Typ wird entweder in der Rohform angezeigt, oder es wird eine andere geeignete Visualisierung ausgewählt. Sie können die natvis-Diagnose verwenden, um zu verstehen, warum der Debugger einen Visualisierungs Eintrag ignoriert hat, und um zugrunde liegende Syntax und Analysefehler anzuzeigen.

**So aktivieren Sie die natvis-Diagnose:**

- Wählen **Sie unter Extras** > **Optionen** (oder **Debuggen** Sie > **Optionen**) > **Debuggen** > **Ausgabefenster**, legen Sie **natvis-Diagnosemeldungen (C++ nur)** auf **Fehler**, **Warnung**oder ausführlich fest, und wählen Sie dann **OK**aus.

Die Fehler werden im Fenster **Ausgabe** angezeigt.

## <a name="BKMK_Syntax_reference"></a> Natvis-Syntaxverweis

### <a name="BKMK_AutoVisualizer"></a> AutoVisualizer-Element
Bei dem `AutoVisualizer`-Element handelt es sich um den Stammknoten der *NATVIS*-Datei, der das `xmlns:`-Attribut für den Namespace enthält.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

Das `AutoVisualizer`-Element kann über die untergeordneten Elemente [Type](#BKMK_Type), [HRESULT](#BKMK_HResult), [uivisualizer](#BKMK_UIVisualizer)und [customvisualizer](#BKMK_CustomVisualizer) verfügen.

### <a name="BKMK_Type"></a> Type-Element

Ein grundlegender `Type` sieht wie im folgenden Beispiel aus:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 Das `Type` Element gibt Folgendes an:

1. Der Typ, für den die Visualisierung verwendet werden soll (das `Name`-Attribut).

2. Wie der Wert eines Objekts dieses Typs aussehen soll (das `DisplayString` -Element).

3. Wie die Member des Typs aussehen sollen, wenn der Benutzer den Typ in einem Variablen Fenster erweitert (der `Expand` Knoten).

#### <a name="templated-classes"></a>Vorlagenbasierte Klassen
Das `Name`-Attribut des `Type`-Elements akzeptiert ein Sternchen `*` als Platzhalter Zeichen, das für vorlagenbasierte Klassennamen verwendet werden kann.

Im folgenden Beispiel wird dieselbe Visualisierung verwendet, unabhängig davon, ob es sich bei dem Objekt um eine `CAtlArray<int>` oder eine `CAtlArray<float>`handelt. Wenn ein bestimmter Visualisierungs Eintrag für einen `CAtlArray<float>`vorhanden ist, hat er Vorrang vor dem generischen Eintrag.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

Sie können auf Vorlagen Parameter im Visualisierungs Eintrag verweisen, indem Sie Makros $T 1, $T 2 usw. verwenden. Beispiele zu diesen Makros finden Sie in den *NATVIS*-Dateien, die in Visual Studio bereitgestellt werden.

#### <a name="BKMK_Visualizer_type_matching"></a> Typenabgleich in der Schnellansicht
Wenn ein Visualisierungs Eintrag nicht überprüft werden kann, wird die nächste verfügbare Visualisierung verwendet.

#### <a name="inheritable-attribute"></a>Inheritable-Attribut
Das optionale `Inheritable`-Attribut gibt an, ob eine Visualisierung nur auf einen Basistyp oder auf einen Basistyp und alle abgeleiteten Typen angewendet wird. Der Standardwert von `Inheritable` lautet `true`.

Im folgenden Beispiel gilt die Visualisierung nur für den `BaseClass`-Typ:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Priority-Attribut

Das optionale `Priority`-Attribut gibt die Reihenfolge an, in der Alternative Definitionen verwendet werden sollen, wenn eine Definition nicht analysiert werden kann. Die möglichen Werte `Priority` lauten: `Low`, `MediumLow`,`Medium`, `MediumHigh`und `High`. Standardwert: `Medium`. Das `Priority`-Attribut unterscheidet nur zwischenprioritäten in derselben *natvis* -Datei.

Im folgenden Beispiel wird zunächst der Eintrag analysiert, der mit 2015 STL übereinstimmt. Wenn dies nicht analysiert werden kann, wird der Alternative Eintrag für die Version 2013 von STL verwendet:

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
Sie können ein `Optional` Attribut auf jedem beliebigen Knoten platzieren. Wenn ein Teil Ausdruck in einem optionalen Knoten nicht analysiert werden kann, ignoriert der Debugger diesen Knoten, wendet aber den Rest der `Type` Regeln an. Im folgenden Typ ist `[State]` nicht optional, während `[Exception]` jedoch optional ist.  Wenn `MyNamespace::MyClass` über ein Feld mit dem Namen _`M_exceptionHolder`verfügt, werden sowohl der Knoten `[State]` als auch der Knoten `[Exception]` angezeigt. Wenn jedoch kein `_M_exceptionHolder` Feld vorhanden ist, wird nur der Knoten `[State]` angezeigt.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="BKMK_Condition_attribute"></a> Condition-Attribut

Das optionale `Condition`-Attribut ist für viele Visualisierungs Elemente verfügbar und gibt an, wann eine Visualisierungs Regel verwendet werden soll. Wenn der Ausdruck innerhalb des Condition-Attributs in `false`aufgelöst wird, wird die Visualisierungs Regel nicht angewendet. Wenn es zu `true`ausgewertet wird oder kein `Condition` Attribut vorhanden ist, wird die Visualisierung angewendet. Sie können dieses Attribut für die if-else-Logik in den Visualisierungs Einträgen verwenden.

Beispielsweise verfügt die folgende Visualisierung über zwei `DisplayString` Elemente für einen intelligenten Zeigertyp. Wenn das `_Myptr`-Element leer ist, wird die Bedingung des ersten `DisplayString` Elements in `true`aufgelöst, sodass das Formular angezeigt wird. Wenn das `_Myptr` Member nicht leer ist, wird die Bedingung als `false`ausgewertet, und das zweite `DisplayString` Element wird angezeigt.

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

Die Attribute `IncludeView` und `ExcludeView` geben Elemente an, die in bestimmten Ansichten angezeigt oder nicht angezeigt werden sollen. In der folgenden natvis-Spezifikation von `std::vector`werden in der `simple` Ansicht die Elemente `[size]` und `[capacity]` nicht angezeigt.

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

Sie können die Attribute "`IncludeView`" und "`ExcludeView`" für Typen und einzelne Member verwenden.

### <a name="BKMK_Versioning"></a> Version-Element
Das `Version` Element Bereiche einen Visualisierungs Eintrag für ein bestimmtes Modul und eine bestimmte Version. Das `Version`-Element hilft bei der Vermeidung von Namenskollisionen, reduziert unbeabsichtigte Konflikte und ermöglicht verschiedene Visualisierungen für unterschiedliche Typversionen.

Wenn eine gängige Header Datei, die von verschiedenen Modulen verwendet wird, einen Typ definiert, wird die Visualisierung mit Versions Angabe nur angezeigt, wenn der Typ in der angegebenen Modulversion vorhanden ist.

Im folgenden Beispiel gilt die Visualisierung nur für den `DirectUI::Border` Typ, der in der `Windows.UI.Xaml.dll` von Version 1,0 bis 1,5 gefunden wurde.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Sie benötigen nicht sowohl `Min` als auch `Max`. Dabei handelt es sich um optionale Attribute. Es werden keine Platzhalter Zeichen unterstützt.

Das `Name`-Attribut hat das Format *Dateiname. ext*, z. b *. "Hello. exe* " oder " *some. dll*". Es sind keine Pfadnamen zulässig.

### <a name="BKMK_DisplayString"></a>Display String-Element
Das `DisplayString`-Element gibt eine Zeichenfolge an, die als Wert einer Variablen angezeigt werden soll. Beliebige Zeichenfolgen können mit Ausdrücken gemischt werden. Sämtliche Inhalte innerhalb von geschweiften Klammern werden als ein Ausdruck interpretiert. Der folgende `DisplayString` Eintrag ist beispielsweise:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Dies bedeutet, dass Variablen des Typs `CPoint` wie in der folgenden Abbildung dargestellt werden:

 ![Verwenden eines DisplayString-Elements](../debugger/media/dbg_natvis_cpoint_displaystring.png "Verwenden eines DisplayString-Elements")

Im `DisplayString` Ausdruck befinden sich `x` und `y`, die Member `CPoint`sind, in geschweiften Klammern, sodass ihre Werte ausgewertet werden. Das Beispiel zeigt auch, wie Sie eine geschweifte Klammer mit doppelten geschweiften Klammern (`{{` oder `}}`) mit Escapezeichen versehen können.

> [!NOTE]
> Das `DisplayString` -Element ist das einzige Element, das beliebige Zeichenfolgen und die Syntax mit geschweiften Klammern akzeptiert. Alle anderen Visualisierungs Elemente akzeptieren nur Ausdrücke, die vom Debugger ausgewertet werden können.

### <a name="BKMK_StringView"></a>Stringview-Element

Das `StringView`-Element definiert einen Wert, den der Debugger an die integrierte Text-Schnellansicht senden kann. Angenommen, Sie haben die folgende Visualisierung für den `ATL::CStringT`-Typ:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

Das `CStringT`-Objekt wird in einem Variablen Fenster wie im folgenden Beispiel angezeigt:

![CStringT DisplayString-Element](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT-DisplayString-Element")

Wenn Sie ein `StringView` Element hinzufügen, wird dem Debugger mitgeteilt, dass der Wert als Text Visualisierung angezeigt werden kann.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Während des Debuggens können Sie das Lupensymbol neben der Variablen auswählen und dann **Text** Schnellansicht auswählen, um die Zeichenfolge anzuzeigen, auf die **m_pszData** zeigt.

 ![CStringT Data with stringview Schnellansicht](../debugger/media/dbg_natvis_stringview_cstringt.png "CStringT-Daten mit StringView-Schnellansicht")

Der Ausdruck `{m_pszData,su}` enthält einen C++ Format Bezeichner **su**, um den Wert als Unicode-Zeichenfolge anzuzeigen. Weitere Informationen finden Sie unter [Formatspezifizierer C++in ](../debugger/format-specifiers-in-cpp.md).

### <a name="BKMK_Expand"></a>Element erweitern

Der optionale `Expand` Knoten passt die untergeordneten Elemente eines visualisierten Typs an, wenn Sie den Typ in einem Variablen Fenster erweitern. Der `Expand` Knoten akzeptiert eine Liste untergeordneter Knoten, die die untergeordneten Elemente definieren.

- Wenn ein `Expand` Knoten in einem Visualisierungs Eintrag nicht angegeben ist, verwenden die untergeordneten Elemente die Standard Erweiterungs Regeln.

- Wenn ein `Expand` Knoten ohne untergeordnete Knoten angegeben wird, ist der Typ in den Debuggerfenstern nicht erweiterbar.

#### <a name="BKMK_Item_expansion"></a> Item-Erweiterung

 Das `Item`-Element ist das grundlegendste und häufigste Element in einem `Expand` Knoten. Das`Item` -Element definiert ein einzelnes untergeordnetes Element. Beispielsweise verfügt eine `CRect`-Klasse mit den Feldern `top`, `left`, `right`und `bottom` über den folgenden Visualisierungs Eintrag:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

Im Debuggerfenster sieht der `CRect` Typ wie im folgenden Beispiel aus:

![CRect mit Element Element Erweiterung](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect mit Item-Element-Erweiterung")

Der Debugger wertet die Ausdrücke aus, die in den Elementen `Width` und `Height` angegeben sind, und zeigt die Werte in der Spalte **Wert** des Variablen Fensters an.

Der Debugger erstellt automatisch den Knoten " **[RAW View]** " für jede benutzerdefinierte Erweiterung. Der obige Screenshot zeigt den erweiterten Knoten **[RAW View]** an, um anzuzeigen, wie sich die standardmäßige Rohdaten Ansicht des Objekts von der natvis-Visualisierung unterscheidet. Mit der Standard Erweiterung wird eine Teilstruktur für die Basisklasse erstellt und alle Datenmember der Basisklasse als untergeordnete Elemente aufgelistet.

> [!NOTE]
> Wenn der Ausdruck des item-Elements auf einen komplexen Typ verweist, ist der **Element** Knoten selbst erweiterbar.

#### <a name="BKMK_ArrayItems_expansion"></a> ArrayItems expansion
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

![Std:: Vector mithilfe von arrayitems-Erweiterungen](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vector mit ArrayItems-Erweiterung")

Der `ArrayItems` Knoten muss Folgendes aufweisen:

- Einen `Size`-Ausdruck (der als ganze Zahl ausgewertet werden muss), damit der Debugger die Länge des Arrays kennt.
- Ein `ValuePointer` Ausdruck, der auf das erste Element zeigt (das ein Zeiger eines Elementtyps sein muss, der nicht `void*`ist).

Der Standardwert mit der Arrayuntergrenze lautet „0“. Verwenden Sie ein `LowerBound`-Element, um den Wert zu überschreiben. Die in Visual Studio enthaltenen *natvis* -Dateien enthalten Beispiele.

>[!NOTE]
>Sie können den `[]` Operator, z. b. `vector[i]`, mit jeder eindimensionalen Array Visualisierung verwenden, die `ArrayItems`verwendet, auch wenn der Typ selbst (z. b. `CATLArray`) diesen Operator nicht zulässt.

Sie können auch mehrdimensionale Arrays angeben. In diesem Fall benötigt der Debugger etwas mehr Informationen, um untergeordnete Elemente ordnungsgemäß anzuzeigen:

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

- `Direction` gibt an, ob das Array in Zeilen-Haupt-oder Spalten Hauptreihen Folge ist.
- `Rank` gibt den Rang des Arrays an.
- Das `Size`-Element akzeptiert den impliziten `$i`-Parameter, der durch den Dimensionsindex ersetzt wird, um die Länge des Arrays in dieser Dimension festzustellen. Im vorherigen Beispiel sollte der Ausdruck `_M_extent.M_base[0]` die Länge der nullten-Dimension, `_M_extent._M_base[1]` 1. usw. geben.

So sieht ein zweidimensionales `Concurrency::array` Objekt im Debuggerfenster aus:

![Zweidimensionales Array mit arrayitems-Erweiterung](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Zweidimensionales Array mit arrayitems-Erweiterung")

#### <a name="BKMK_IndexListItems_expansion"></a> IndexListItems-Erweiterung

Sie können `ArrayItems` Erweiterung nur verwenden, wenn die Array Elemente im Arbeitsspeicher zusammenhängend angeordnet werden. Der Debugger erhält das nächste Element, indem er einfach seinen Zeiger erhöht. Wenn Sie den Index auf den Wert Knoten ändern müssen, verwenden Sie `IndexListItems` Knoten. Im folgenden finden Sie eine Visualisierung mit einem `IndexListItems` Knoten:

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

Der einzige Unterschied zwischen `ArrayItems` und `IndexListItems` ist die `ValueNode`, die den vollständigen Ausdruck für das i<sup>th</sup> -Element mit dem impliziten `$i`-Parameter erwartet.

>[!NOTE]
>Sie können den `[]` Operator, z. b. `vector[i]`, mit jeder eindimensionalen Array Visualisierung verwenden, die `IndexListItems`verwendet, auch wenn der Typ selbst (z. b. `CATLArray`) diesen Operator nicht zulässt.

#### <a name="BKMK_LinkedListItems_expansion"></a> LinkedListItems-Erweiterung

Wenn der Schnellansichtstyp eine verknüpfte Liste darstellt, kann der Debugger die untergeordneten Elemente mithilfe eines `LinkedListItems` -Knotens anzeigen. Die folgende Visualisierung für den `CAtlList`-Typ verwendet `LinkedListItems`:

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

Der Debugger wertet die `NextPointer`-und `ValueNode` Ausdrücke im Kontext des `LinkedListItems` Node-Elements und nicht im übergeordneten Listentyp aus. Im vorherigen Beispiel verfügt `CAtlList` über eine `CNode` Klasse (in `atlcoll.h`), die ein Knoten der verknüpften Liste ist. `m_pNext` und `m_element` sind Felder dieser `CNode` Klasse, nicht der `CAtlList` Klasse.

`ValueNode` können leer gelassen werden, oder verwenden Sie `this`, um auf den `LinkedListItems` Knoten selbst zu verweisen.

#### <a name="customlistitems-expansion"></a>CustomListItems-Erweiterung

Die `CustomListItems` -Erweiterung ermöglicht Ihnen das Schreiben von benutzerdefinierter Logik für das Traversieren einer Datenstruktur, beispielsweise einer Hashtabelle. Verwenden Sie `CustomListItems`, um Datenstrukturen visuell darzustellen C++ , die Ausdrücke für alles verwenden können, was Sie auswerten müssen, aber nicht für die `ArrayItems`, `IndexListItems`oder `LinkedListItems`geeignet sind.

Mithilfe von `Exec` können Sie Code innerhalb einer `CustomListItems` Erweiterung ausführen, indem Sie die Variablen und Objekte verwenden, die in der Erweiterung definiert sind. Sie können logische Operatoren, arithmetische Operatoren und Zuweisungs Operatoren mit `Exec`verwenden. Mit Ausnahme der [intrinsischen Debugger-Funktionen](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) , die von der C++ Ausdrucks Auswertung unterstützt werden, können Sie `Exec` nicht zum Auswerten von Funktionen verwenden.

Die folgende Schnellansicht für `CAtlMap` ist ein hervorragendes Beispiel, bei dem `CustomListItems` geeignet ist.

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

#### <a name="BKMK_TreeItems_expansion"></a> TreeItems-Erweiterung
 Wenn der Schnellansichtstyp eine Struktur darstellt, kann der Debugger die Struktur durchlaufen und seine untergeordneten Elemente mithilfe eines `TreeItems` -Knotens anzeigen. Hier sehen Sie die Visualisierung für den `std::map` Typ mit einem `TreeItems` Knoten:

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

Die Syntax ähnelt dem `LinkedListItems`-Knoten. `LeftPointer`, `RightPointer`und `ValueNode` werden im Kontext der Struktur Knoten Klasse ausgewertet. `ValueNode` können leer gelassen werden, oder verwenden Sie `this`, um auf den `TreeItems` Knoten selbst zu verweisen.

#### <a name="BKMK_ExpandedItem_expansion"></a> ExpandedItem-Erweiterung
 Das `ExpandedItem`-Element generiert eine aggregierte untergeordnete Ansicht, indem die Eigenschaften von Basisklassen oder Datenmembern so angezeigt werden, als wären Sie untergeordnete Elemente des visualisierten Typs. Der Debugger wertet den angegebenen Ausdruck aus und fügt die untergeordneten Knoten des Ergebnisses an die untergeordnete Liste des schnell Ansichts Typs an.

Der Typ des intelligenten Zeigers `auto_ptr<vector<int>>` z. b. in der Regel wie folgt angezeigt:

 ![Automatisches&#95;PTR&#60;-&#60;Vektor&#62; &#62; int Standard Erweiterung](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Standard Erweiterung")

 Um die Werte des Vektors anzuzeigen, müssen Sie im Variablen Fenster einen Drilldown auf zwei Ebenen ausführen und den `_Myptr` Member durchlaufen. Durch Hinzufügen eines `ExpandedItem`-Elements können Sie die `_Myptr`-Variable aus der Hierarchie ausschließen und die Vektorelemente direkt anzeigen:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![automatische&#95;PTR&#60;-&#60;Vektor&#62; &#62; -int-Erweiterung](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "ExpandedItem-Erweiterung")

Im folgenden Beispiel wird gezeigt, wie Eigenschaften von der Basisklasse in einer abgeleiteten Klasse aggregiert werden. Angenommen, die `CPanel` -Klasse wird von `CFrameworkElement`abgeleitet. Anstatt die Eigenschaften zu wiederholen, die von der Basis `CFrameworkElement` Klasse stammen, fügt die Visualisierung `ExpandedItem` Knoten diese Eigenschaften an die untergeordnete Liste der `CPanel`-Klasse an.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Der **nd**-Formatbezeichner, mit dem die Visualisierungsabstimmung für die abgeleitete Klasse deaktiviert wird, ist hier erforderlich. Andernfalls würde der Ausdruck `*(CFrameworkElement*)this` bewirken, dass die `CPanel` Visualisierung erneut angewendet wird, da die standardabgleichsregeln des Visualisierungs Typs dies als am besten geeignete Regeln in Erwägung zieht. Verwenden Sie den **ND** -Format Bezeichner, um den Debugger anzuweisen, die Basisklassen Visualisierung zu verwenden, oder die Standard Erweiterung, wenn die Basisklasse keine Visualisierung hat.

#### <a name="BKMK_Synthetic_Item_expansion"></a> Synthetische Elementerweiterung
 Während das `ExpandedItem`-Element eine flachere Datenansicht durch die Beseitigung von Hierarchien bereitstellt, bewirkt der `Synthetic`-Knoten das Gegenteil. Sie ermöglicht es Ihnen, ein künstliches untergeordnetes Element zu erstellen, das kein Ergebnis eines Ausdrucks ist. Das künstliche Element kann eigene untergeordnete Elemente aufweisen. Im folgenden Beispiel verwendet die Visualisierung für den `Concurrency::array` -Typ einen `Synthetic` -Knoten, um dem Benutzer eine Diagnosemeldung anzuzeigen:

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

 ![Parallelcurrency:: Array mit synthetischem Element Erweiterung](../debugger/media/dbg_natvis_expand_synthetic.png "Parallelcurrency:: Array mit synthetischem Element Erweiterung")

### <a name="BKMK_HResult"></a>HRESULT-Element
 Mit dem `HResult`-Element können Sie die Informationen, die für ein **HRESULT** in Debuggerfenstern angezeigt werden, anpassen. Das `HRValue`-Element muss den 32-Bit-Wert des anzupassenden **HRESULT**-Elements enthalten. Das `HRDescription`-Element enthält die Informationen, die im Debugger-Fenster angezeigt werden sollen.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="BKMK_UIVisualizer"></a>Uivisualizer-Element
Ein `UIVisualizer` -Element registriert ein grafisches Schnellansichts-Plug-In mit dem Debugger. Eine grafische Schnellansicht erstellt ein Dialogfeld oder eine andere Schnittstelle, die eine Variable oder ein Objekt in einer Weise anzeigt, die dem Datentyp entspricht. Das schnell Ansichts-Plug-in muss als [VSPackage](../extensibility/internals/vspackages.md)erstellt werden und einen Dienst verfügbar machen, der vom Debugger verwendet werden kann. Die *natvis* -Datei enthält Registrierungsinformationen für das Plug-in, z. b. den Namen, die GUID des verfügbar gemachten Dienstanbieter und die Typen, die Sie visualisieren kann.

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

- Ein `ServiceId` - `Id` Attribut paar identifiziert eine `UIVisualizer`. Der `ServiceId` ist die GUID des Dienstanbieter, der vom schnell Ansichts Paket verfügbar gemacht wird. `Id` ist ein eindeutiger Bezeichner, der Visualisierungen unterscheidet, wenn ein Dienst mehr als einen Dienst bereitstellt. Im vorherigen Beispiel stellt der gleiche schnell Ansichts Dienst zwei schnell Ansichten bereit.

- Das `MenuName`-Attribut definiert einen schnell Ansichts Namen, der in der Dropdown Liste neben dem Lupensymbol im Debugger angezeigt werden soll. Beispiel:

  ![Kontextmenü für uivisualizer-Menü](../debugger/media/dbg_natvis_vectorvisualizer.png "Kontextmenü des UIVisualizer-Menüs")

Jeder Typ, der in der *natvis* -Datei definiert ist, muss explizit alle Benutzeroberflächen-Visualisierungen auflisten, die Sie anzeigen können. Der Debugger gleicht die Visualisierungs Verweise in den typeinträgen mit den registrierten schnell Ansichten ab. Beispielsweise verweist der folgende typeintrag für `std::vector` auf die `UIVisualizer` im vorherigen Beispiel.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Ein Beispiel für eine `UIVisualizer` in der [Image Watch](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) -Erweiterung, die zum Anzeigen von in-Memory-Bitmaps verwendet wird, wird angezeigt.

### <a name="BKMK_CustomVisualizer"></a>CustomVisualizer-Element
 `CustomVisualizer` ist ein Erweiterbarkeits Punkt, der eine VSIX-Erweiterung angibt, die Sie schreiben, um Visualisierungen in Visual Studio Code zu steuern. Weitere Informationen zum Schreiben von VSIX-Erweiterungen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Es ist viel mehr Arbeit, eine benutzerdefinierte Schnellansicht zu schreiben, als eine XML-natvis-Definition, aber es gibt keine Einschränkungen hinsichtlich der Art und Weise, die natvis nicht unterstützt. Benutzerdefinierte Visualisierungen haben Zugriff auf den vollständigen Satz von Debugger-Erweiterbarkeits-APIs, mit denen der zu debuggende Prozess abgefragt und geändert werden kann oder mit anderen Teilen von Visual Studio kommuniziert werden kann.

 Sie können die Attribute "`Condition`", "`IncludeView`" und "`ExcludeView`" für `CustomVisualizer` Elemente verwenden.

 ## <a name="limitations"></a>Einschränkungen

Natvis-Anpassungen arbeiten mit Klassen und Strukturen, jedoch nicht mit Typedefs.

Natvis unterstützt keine Visualisierungen für primitive Typen (z. b. `int``bool`) oder für Zeiger auf primitive Typen. In diesem Szenario besteht eine Möglichkeit darin, den [Format](../debugger/format-specifiers-in-cpp.md) Bezeichner zu verwenden, der für Ihren Anwendungsfall geeignet ist. Wenn Sie z. b. `double* mydoublearray` in Ihrem Code verwenden, können Sie einen Array Format Bezeichner im **Überwachungs** Fenster des Debuggers verwenden, z. b. den Ausdruck `mydoublearray, [100]`, in dem die ersten 100 Elemente angezeigt werden.
