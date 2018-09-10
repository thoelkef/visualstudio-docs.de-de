---
title: 'Exemplarische Vorgehensweise: Verwenden von MSBuild | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d7e862322995c7cda4a7080ee387c7a080437748
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178517"
---
# <a name="walkthrough-use-msbuild"></a>Exemplarische Vorgehensweise: Verwenden von MSBuild
MSBuild ist die Buildplattform für Microsoft und Visual Studio. In dieser exemplarischen Vorgehensweise machen Sie sich mit den Bausteinen von MSBuild vertraut, zudem wird erläutert, wie Sie MSBuild-Projekte erstellen, bearbeiten und debuggen. Zu folgenden Aspekten erfahren Sie mehr:

-   Erstellen und Bearbeiten einer Projektdatei.

-   Verwenden von Buildeigenschaften

-   Verwenden von Buildelementen

Sie können MSBuild in Visual Studio oder im **Befehlsfenster** ausführen. In dieser exemplarischen Vorgehensweise erstellen Sie in Visual Studio eine MSBuild-Projektdatei. Sie bearbeiten die Projektdatei in Visual Studio, und im **Befehlsfenster** erstellen Sie das Projekt und untersuchen die Ergebnisse.

## <a name="create-an-msbuild-project"></a>Erstellen eines MSBuild-Projekts
 Das Visual Studio-Projektsystem beruht auf MSBuild. Auf diese Weise können in Visual Studio neue Projektdatei problemlos erstellt werden. In diesem Abschnitt erstellen Sie eine Visual C#-Projektdatei. Stattdessen können Sie auch eine Visual Basic-Projektdatei erstellen. Im Kontext dieser exemplarischen Vorgehensweise ist der Unterschied zwischen den zwei Projektdateien marginal.

#### <a name="to-create-a-project-file"></a>So erstellen Sie eine neue Projektdatei

1.  Öffnen Sie Visual Studio.

2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

3.  Wählen Sie im Dialogfeld **Neues Projekt** den Projekttyp **Visual C#** und anschließend die Vorlage **Windows Forms-Anwendung** aus. Geben Sie im Feld **Name** `BuildApp`ein. Geben Sie einen **Speicherort** für die Projektmappe ein, z.B. *D:\\*. Übernehmen Sie die Standardwerte für **Projektmappenverzeichnis erstellen** (ausgewählt), **Zur Quellcodeverwaltung hinzufügen** (nicht ausgewählt) und **Projektmappenname** (**BuildApp**).

4.    Klicken Sie auf **OK**, um die neue Projektdatei zu erstellen.

## <a name="examine-the-project-file"></a>Überprüfen der Projektdatei
 Im vorherigen Abschnitt haben Sie in Visual Studio eine Visual C#-Projektdatei erstellt. Die Projektdatei wird im **Projektmappen-Explorer** durch den Projektknoten „BuildApp“ dargestellt. Sie können die Projektdatei im Visual Studio Code-Editor untersuchen.

#### <a name="to-examine-the-project-file"></a>So überprüfen Sie die Projektdatei

1.  Klicken Sie im **Projektmappen-Explorer** auf den Projektknoten **BuildApp**.

2.  Im **Eigenschaftenbrowser** wird als **Projektdatei**-Eigenschaft *BuildApp.csproj* angezeigt. Alle Projektdateien werden mit dem Suffix *PROJ* benannt. Wenn Sie ein Visual Basic-Projekt erstellt hätten, wäre der Projektdateiname *BuildApp.vbproj*.

3.  Klicken Sie mit der rechten Maustaste auf den Projektknoten, und klicken Sie dann auf **Projekt entladen**.

4.  Klicken Sie erneut mit der rechten Maustaste auf den Projektknoten, klicken Sie dann auf **BuildApp.csproj bearbeiten**.

     Die Projektdatei wird im Code-Editor angezeigt.

## <a name="targets-and-tasks"></a>Ziele und Aufgaben
Projektdateien sind Dateien im XML-Format und dem Stammknoten [Project](../msbuild/project-element-msbuild.md).

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Sie müssen den xmlns-Namespace im Project-Element angeben. Wenn `ToolsVersion` in einem neuen Projekt enthalten ist, muss es sich um die Version „15.0“ handeln.

Das Erstellen einer Anwendung wird mit dem [Target](../msbuild/target-element-msbuild.md)-Element und dem [Task](../msbuild/task-element-msbuild.md)-Element ausgeführt.

-   Eine Aufgabe bildet die kleinste Arbeitseinheit, d. h. das „Atom“ eines Builds. Aufgaben sind unabhängige ausführbare Komponenten, die über Eingaben und Ausgaben verfügen können. Derzeit wird in der Projektdatei nicht auf Aufgaben verwiesen, und solche wurden nicht definiert. In den folgenden Abschnitten fügen Sie der Projektdatei Aufgaben hinzu. Weitere Informationen finden Sie im Thema [Aufgaben](../msbuild/msbuild-tasks.md).

-   Als Ziel wird eine benannte Sequenz von Aufgaben bezeichnet. Weitere Informationen finden Sie im Thema [Ziele](../msbuild/msbuild-targets.md).

Das Standardziel ist nicht in der Projektdatei definiert. Stattdessen wird es in importierten Projekten angegeben. Das [Import](../msbuild/import-element-msbuild.md)-Element gibt importierte Projekte an. Beispielsweise wird in einem C#-Projekt das Standardziel aus der Datei *Microsoft.CSharp.targets* importiert.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

Importierte Dateien werden letztlich in der Projektdatei eingefügt, in der sie mit Verweisen versehen werden.

> [!NOTE]
> Einige Projekttypen wie .NET Core verwenden ein vereinfachtes Schema mit einem `Sdk`-Attribut anstelle von `ToolsVersion`. Diese Projekte verfügen über implizite Importe und unterschiedliche Standardattributwerte.

MSBuild verfolgt die Ziele eines Builds nach und garantiert, dass jedes Ziel nicht mehr als einmal erstellt wird.

## <a name="add-a-target-and-a-task"></a>Hinzufügen eines Ziels und einer Aufgabe
 Fügen Sie der Projektdatei ein Ziel hinzu. Fügen Sie dem Ziel eine Aufgabe hinzu, mit der eine Meldung gedruckt wird.

#### <a name="to-add-a-target-and-a-task"></a>So fügen Sie ein Ziel und eine Aufgabe hinzu

1.  Fügen Sie der Projektdatei, genau nach der Import-Anweisung, die folgenden Zeilen hinzu:

    ```xml
    <Target Name="HelloWorld">
    </Target>
    ```

     So erstellen Sie das Ziel HelloWorld. Beachten Sie, dass beim Bearbeiten der Projektdatei IntelliSense unterstützt wird.

2.  Fügen Sie dem Ziel HelloWorld Zeilen hinzu, sodass der daraufhin angezeigte Abschnitt wie folgt aussieht:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Hello"></Message>  <Message Text="World"></Message>
    </Target>
    ```

3.  Speichern Sie die Projektdatei.

Die Message-Aufgabe ist eine der vielen Aufgaben, die im Lieferumfang von MSBuild enthalten sind. Eine vollständige Liste der verfügbaren Aufgaben sowie Nutzungsinformationen finden Sie unter [Aufgabenreferenz](../msbuild/msbuild-task-reference.md).

Die Message-Aufgabe erfordert den Zeichenfolgenwert des Text-Attributs als Eingabe und zeigt diesen auf dem Ausgabegerät an. Das HelloWorld-Ziel führt die Message-Aufgabe zweimal aus: zuerst wird "Hello" angezeigt, dann "World".

## <a name="build-the-target"></a>Erstellen des Ziels
 Führen Sie MSBuild an der **Visual Studio-Eingabeaufforderung** aus, um das oben definierte Ziel „HelloWorld“ zu erstellen. Verwenden Sie den Befehlszeilenschalter /target oder /t, um das Ziel auszuwählen.

> [!NOTE]
>  In den folgenden Abschnitten wird die **Visual Studio-Eingabeaufforderung** als **Befehlsfenster** bezeichnet.

#### <a name="to-build-the-target"></a>So erstellen Sie das Ziel

1.  Klicken Sie auf **Start**, und klicken Sie dann auf **Alle Programme**. Suchen Sie im Ordner **Visual Studio Tools** die **Visual Studio-Eingabeaufforderung**, und klicken Sie darauf.

2.  Navigieren Sie im Befehlsfenster zum Ordner mit der Projektdatei, in diesem Fall *D:\BuildApp\BuildApp*.

3.  Führen Sie msbuild mit dem Befehlsschalter /t:HelloWorld aus. Damit wird das Ziel HelloWorld ausgewählt und erstellt:

    ```cmd
    msbuild buildapp.csproj /t:HelloWorld
    ```

4.  Untersuchen Sie die Ausgabe im **Befehlsfenster**. Die beiden Zeilen "Hello" und "World" sollten angezeigt werden:

    ```
    Hello
    World
    ```

> [!NOTE]
>  Wenn stattdessen `The target "HelloWorld" does not exist in the project` angezeigt wird, haben Sie wahrscheinlich vergessen, die Projektdatei im Code-Editor zu speichern. Speichern Sie die Datei, und versuchen Sie es erneut.

 Durch Wechsel zwischen Code-Editor und dem Befehlsfenster können Sie die Projektdatei ändern und die Ergebnisse schnell anzeigen.

## <a name="build-properties"></a>Buildeigenschaften
 Buildeigenschaften sind Name-Wert-Paare, anhand derer der Build ausgeführt wird. Am Anfang der Projektdatei sind bereits mehrere Buildeigenschaften definiert:

```xml
<PropertyGroup>
...
  <ProductVersion>10.0.11107</ProductVersion>
  <SchemaVersion>2.0</SchemaVersion>
  <ProjectGuid>{30E3C9D5-FD86-4691-A331-80EA5BA7E571}</ProjectGuid>
  <OutputType>WinExe</OutputType>
...
</PropertyGroup>
```

 Alle Eigenschaften sind untergeordnete Elemente von PropertyGroup-Elementen. Der Name der Eigenschaft entspricht dem Namen des untergeordneten Elements, und der Wert der Eigenschaft entspricht dem Textelement des untergeordneten Elements. Ein auf ein Objekt angewendeter

```xml
<TargetFrameworkVersion>v15.0</TargetFrameworkVersion>
```

 definiert die Eigenschaft "TargetFrameworkVersion" und weist dieser den Zeichenfolgenwert „v15.0“ zu.

 Buildeigenschaften können jederzeit neu definiert werden. If

```xml
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
```

 später in der Projektdatei oder in einer später in die Projektdatei importierten Datei angegeben ist, nimmt TargetFrameworkVersion den neuen Wert "v3.5" an.

## <a name="examine-a-property-value"></a>Untersuchen eines Eigenschaftswerts
 Den Wert einer Eigenschaft rufen Sie mit der folgenden Syntax ab, wobei PropertyName den Namen der Eigenschaft darstellt:

```xml
$(PropertyName)
```

 Verwenden Sie die folgende Syntax, um einige Eigenschaften in der Projektdatei zu untersuchen.

#### <a name="to-examine-a-property-value"></a>So untersuchen Sie einen Eigenschaftswert

1.  Ersetzen Sie im Code-Editor das Ziel HelloWorld durch den folgenden Code:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Configuration is $(Configuration)" />
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />
    </Target>
    ```

2.  Speichern Sie die Projektdatei.

3.  Geben Sie im **Befehlsfenster** die folgende Zeile ein, und führen Sie diese aus:

    ```cmd
    msbuild buildapp.csproj /t:HelloWorld
    ```

4.  Prüfen Sie die Ausgabe. Die folgenden beiden Zeilen sollten angezeigt werden (die Version von .NET Framework kann abweichen):

    ```
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2017\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

> [!NOTE]
>  Wenn diese Zeilen nicht angezeigt werden, haben Sie wahrscheinlich vergessen, die Projektdatei im Code-Editor zu speichern. Speichern Sie die Datei, und versuchen Sie es erneut.

### <a name="conditional-properties"></a>Bedingte Eigenschaften
 Viele Eigenschaften, z. B. Configuration, werden bedingt definiert, das heißt, im Eigenschaftenelement wird das Condition-Attribut angezeigt. Bedingte Eigenschaften werden nur definiert oder erneut definiert, wenn die Bedingung "true" ergibt. Nicht definierten Eigenschaften wird der Standardwert, eine leere Zeichenfolge, zugewiesen. Ein auf ein Objekt angewendeter

```xml
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 bedeutet: "Wenn die Configuration-Eigenschaft noch nicht definiert wurde, definieren Sie diese, und weisen Sie ihr den Wert 'Debug' zu."

 Fast alle MSBuild-Elemente können ein Condition-Attribut besitzen. Die Verwendung des Condition-Attributs wird unter [Bedingungen](../msbuild/msbuild-conditions.md) näher besprochen.

### <a name="reserved-properties"></a>Reservierte Eigenschaften
 Einige Eigenschaftennamen werden von MSBuild reserviert, um Informationen zur Projektdatei und zu den Binärdateien von MSBuild zu speichern. Ein Beispiel für eine reservierte Eigenschaft ist "MSBuildToolsPath". Auf reservierte Eigenschaften wird wie auf jede andere Eigenschaft mit der $-Notation verwiesen. Weitere Informationen finden Sie unter [Vorgehensweise: Verweisen auf den Namen oder Speicherort der Projektdatei](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) und [Reservierte und bekannte Eigenschaften für MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).

### <a name="environment-variables"></a>Umgebungsvariablen
 Auf Umgebungsvariablen in Projektdateien kann auf die gleiche Weise verwiesen werden wie auf Buildeigenschaften. Um die PATH-Umgebungsvariable in der Projektdatei zu verwenden, verwenden Sie beispielsweise $(Path). Wenn das Projekt eine Eigenschaftendefinition enthält, die denselben Namen wie eine Umgebungsvariable hat, wird der Wert der Umgebungsvariablen von der Eigenschaft im Projekt überschrieben. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden von Umgebungsvariablen in einem Build](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="set-properties-from-the-command-line"></a>Festlegen von Eigenschaften in der Befehlszeile
 Eigenschaften können an der Befehlszeile mit dem Befehlszeilenschalter /property oder /p definiert werden. Die in der Projektdatei und in Umgebungsvariablen festgelegten Eigenschaftswerte werden durch die Eigenschaftswerte überschrieben, die von der Befehlszeile empfangen werden.

#### <a name="to-set-a-property-value-from-the-command-line"></a>So legen Sie einen Eigenschaftswert an der Befehlszeile fest

1.  Geben Sie im **Befehlsfenster** die folgende Zeile ein, und führen Sie diese aus:

    ```cmd
    msbuild buildapp.csproj /t:HelloWorld /p:Configuration=Release
    ```

2.  Prüfen Sie die Ausgabe. Die folgende Zeile sollte angezeigt werden:

    ```
    Configuration is Release.
    ```

MSBuild erstellt die Configuration-Eigenschaft und weist dieser den Wert "Release" zu.

## <a name="special-characters"></a>Sonderzeichen
 Bestimmte Zeichen haben in MSBuild-Projektdateien eine besondere Bedeutung. Beispiele für solche Zeichen sind Semikolons (;) und Sternchen (*). Um diese Sonderzeichen als Literale in einer Projektdatei zu verwenden, müssen sie mit der Syntax %\<xx> angegeben werden, wobei \<xx> den ASCII-Hexadezimalwert des Zeichens darstellt.

 Ändern Sie die Message-Aufgabe, um den Wert der Configuration-Eigenschaft mit Sonderzeichen anzuzeigen, um sie besser lesbar zu machen.

#### <a name="to-use-special-characters-in-the-message-task"></a>So verwenden Sie Sonderzeichen in der Message-Aufgabe

1.  Ersetzen Sie im Code-Editor beide Message-Aufgaben durch folgende Zeile:

    ```xml
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />
    ```

2.  Speichern Sie die Projektdatei.

3.  Geben Sie im **Befehlsfenster** die folgende Zeile ein, und führen Sie diese aus:

    ```cmd
    msbuild buildapp.csproj /t:HelloWorld
    ```

4.  Prüfen Sie die Ausgabe. Die folgende Zeile sollte angezeigt werden:

    ```
    $(Configuration) is "Debug"
    ```

Weitere Informationen finden Sie unter [MSBuild-Sonderzeichen](../msbuild/msbuild-special-characters.md).

## <a name="build-items"></a>Buildelemente
 Als Element wird eine Information, in der Regel ein Dateiname, bezeichnet, die als Eingabe für das Buildsystem verwendet wird. Eine Auflistung von Elementen, die Quelldateien darstellen, kann beispielsweise an die Aufgabe Compile übergeben werden, um sie zu einer Assembly zu kompilieren.

 Alle Elemente sind untergeordnete Elemente von ItemGroup-Elementen. Der Elementname entspricht dem Namen des untergeordneten Elements, und der Elementwert entspricht dem Wert des Include-Attributs für das untergeordnete Element. Die Werte von Elementen mit gleichem Namen werden in Elementtypen dieses Namens erfasst.  Ein auf ein Objekt angewendeter

```xml
<ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
</ItemGroup>
```

 definiert eine Elementgruppe mit zwei Elementen. Der Compile-Elementtyp umfasst zwei Werte: *Program.cs* und *Properties\AssemblyInfo.cs*.

 Mit folgendem Code wird der gleiche Elementtyp erstellt, indem die beiden durch ein Semikolon getrennten Dateien in einem Include-Attribut deklariert werden.

```xml
<ItemGroup>
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />
</ItemGroup>
```

Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).

> [!NOTE]
>  Dateipfade werden relativ zum Ordner mit der MSBuild-Projektdatei angegeben.

## <a name="examine-item-type-values"></a>Untersuchen der Elementtypwerte
 Werte eines Elementtyps rufen Sie mit der folgenden Syntax ab, wobei ItemType den Name des Elementtyps darstellt:

```xml
@(ItemType)
```

 Den Compile-Elementtyp in der Projektdatei untersuchen Sie mithilfe der folgenden Syntax.

#### <a name="to-examine-item-type-values"></a>So untersuchen Sie Elementtypwerte

1.  Ersetzen Sie im Code-Editor die Aufgabe für das Ziel HelloWorld durch den folgenden Code:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Compile item type contains @(Compile)" />
    </Target>
    ```

2.  Speichern Sie die Projektdatei.

3.  Geben Sie im **Befehlsfenster** die folgende Zeile ein, und führen Sie diese aus:

    ```cmd
    msbuild buildapp.csproj /t:HelloWorld
    ```

4.  Prüfen Sie die Ausgabe. Die folgende lange Zeile sollte angezeigt werden:

    ```
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
    ```

Die Werte eines Elementtyps werden standardmäßig durch Semikolons getrennt.

Wenn Sie das Trennzeichen für einen Elementtyp ändern möchten, verwenden Sie die folgende Syntax, wobei ItemType den Elementtyp und Separator eine Zeichenfolge aus einem oder mehreren Trennzeichen darstellt:

```xml
@(ItemType, Separator)
```

Ändern Sie die Message-Aufgabe, um Compile-Elemente mithilfe von Wagenrückläufen und Zeilenvorschüben (%0A%0D) auf jeweils eigenen Zeilen anzuzeigen.

#### <a name="to-display-item-type-values-one-per-line"></a>So zeigen Sie Elementtypwerte auf jeweils eigenen Zeilen an

1.  Ersetzen Sie die Message-Aufgabe im Code-Editor durch diese Zeile:

    ```xml
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />
    ```

2.  Speichern Sie die Projektdatei.

3.  Geben Sie im **Befehlsfenster** die folgende Zeile ein, und führen Sie diese aus:

    ```cmd
    msbuild buildapp.csproj /t:HelloWorld
    ```

4.  Prüfen Sie die Ausgabe. Die folgenden Zeilen sollten angezeigt werden:

    ```
    Compile item type contains Form1.cs
    Form1.Designer.cs
    Program.cs
    Properties\AssemblyInfo.cs
    Properties\Resources.Designer.cs
    Properties\Settings.Designer.cs
    ```

### <a name="include-exclude-and-wildcards"></a>Include, Exclude und Platzhalter
 Sie können mit dem Include-Attribut die Platzhalter „*“, „\*\*“ und „?“ verwenden, um einem Elementtyp Elemente hinzuzufügen. Ein auf ein Objekt angewendeter

```xml
<Photos Include="images\*.jpeg" />
```

 fügt alle Dateien mit der Dateierweiterung *JPEG* im Ordner *images* dem Photos-Elementtyp hinzu, während

```xml
<Photos Include="images\**.jpeg" />
```

 alle Dateien mit der Dateierweiterung *JPEG* im Ordner *images* und allen Unterordnern dem Photos-Elementtyp hinzufügt. Weitere Beispiele finden Sie unter [Vorgehensweise: Auswählen von Dateien für den Buildvorgang](../msbuild/how-to-select-the-files-to-build.md).

 Beachten Sie, dass deklarierte Elemente sofort dem jeweiligen Elementtyp hinzugefügt werden. Ein auf ein Objekt angewendeter

```xml
<Photos Include="images\*.jpeg" />
<Photos Include="images\*.gif" />
```

 erstellt den Elementtyp „Photo“ mit allen Dateien im Ordner *image*, die die Dateierweiterung *JPEG* oder *GIF* aufweisen. Dies entspricht der folgenden Zeile:

```xml
<Photos Include="images\*.jpeg;images\*.gif" />
```

 Mit dem Exclude-Attribut können Sie ein Element aus einem Elementtyp ausschließen. Ein auf ein Objekt angewendeter

```xml
<Compile Include="*.cs" Exclude="*Designer*">
```

 fügt dem Compile-Elementtyp alle Dateien mit der Dateierweiterung *CS* hinzu, mit Ausnahme von Dateien, deren Namen die Zeichenfolge *Designer* enthalten. Weitere Beispiele finden Sie unter [Vorgehensweise: Ausschließen von Dateien vom Buildvorgang](../msbuild/how-to-exclude-files-from-the-build.md).

Das Exclude-Attribut wirkt sich nur auf die Elemente aus, die über das Include-Attribut in dem Elementelement hinzugefügt wurden, das beide enthält. Ein auf ein Objekt angewendeter

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

In diesem Beispiel wird die Datei *Form1.cs*, die im vorherigen Elementelement hinzugefügt wurde, nicht ausgeschlossen.

##### <a name="to-include-and-exclude-items"></a>So schließen Sie Elemente ein oder aus

1.  Ersetzen Sie die Message-Aufgabe im Code-Editor durch diese Zeile:

    ```xml
    <Message Text="XFiles item type contains @(XFiles)" />
    ```

2.  Fügen Sie diese Elementgruppe genau nach dem Import-Element hinzu:

    ```xml
    <ItemGroup>
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />
    </ItemGroup>
    ```

3.  Speichern Sie die Projektdatei.

4.  Geben Sie im **Befehlsfenster** die folgende Zeile ein, und führen Sie diese aus:

    ```cmd
    msbuild buildapp.csproj /t:HelloWorld
    ```

5.  Prüfen Sie die Ausgabe. Die folgende Zeile sollte angezeigt werden:

    ```
    XFiles item type contains Form1.cs;Program.cs;Properties/Resources.resx
    ```

## <a name="item-metadata"></a>Elementmetadaten
 Zusätzlich zu den Informationen aus dem Include-Attribut und dem Exclude-Attribut können Elemente Metadaten enthalten. Diese Metadaten können von Aufgaben verwendet werden, die neben dem Elementwert weitere Informationen zu den Elementen erfordern.

 Elementmetadaten werden in der Projektdatei deklariert, indem ein Element mit dem Namen der Metadaten als untergeordnetes Element des Elements erstellt wird. Ein Element kann über 0 (null) oder mehr Metadatenwerte verfügen. Das folgende CSFile-Element weist z. B. Culture-Metadaten mit dem Wert "Fr" auf:

```xml
<ItemGroup>
    <CSFile Include="main.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Den Metadatenwert eines Elementtyps rufen Sie mit der folgenden Syntax ab, wobei ItemType den Namen des Elementtyps darstellt und MetaDataName den Namen der Metadaten:

```xml
%(ItemType.MetaDataName)
```

#### <a name="to-examine-item-metadata"></a>So untersuchen Sie die Metadaten von Elementen

1.  Ersetzen Sie die Message-Aufgabe im Code-Editor durch diese Zeile:

    ```xml
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />
    ```

2.  Speichern Sie die Projektdatei.

3.  Geben Sie im **Befehlsfenster** die folgende Zeile ein, und führen Sie diese aus:

    ```cmd
    msbuild buildapp.csproj /t:HelloWorld
    ```

4.  Prüfen Sie die Ausgabe. Die folgenden Zeilen sollten angezeigt werden:

    ```
    Compile.DependentUpon:
    Compile.DependentUpon: Form1.cs
    Compile.DependentUpon: Resources.resx
    Compile.DependentUpon: Settings.settings
    ```

Der Ausdruck "Compile.DependentUpon" wird mehrmals angezeigt. In dieser Syntax führt die Verwendung von Metadaten in einem Ziel zur "Batchverarbeitung". Batchverarbeitung bedeutet, dass die Aufgaben innerhalb des Ziels für jeden eindeutigen Metadatenwert einmal ausgeführt werden. Dies ist die MSBuild-Skriptentsprechung des häufig verwendeten Programmierkonstrukts "for-Schleife". Weitere Informationen finden Sie unter [MSBuild Batching (Batchverarbeitung)](../msbuild/msbuild-batching.md).

### <a name="well-known-metadata"></a>Bekannte Metadaten
 Wenn einer Elementliste ein Element hinzugefügt wird, werden diesem Element stets bekannte Metadaten zugewiesen. Beispielsweise gibt %(Filename) den Dateinamen eines beliebigen Elements zurück. Eine vollständige Liste bekannter Metadaten finden Sie unter [Bekannte Elementmetadaten](../msbuild/msbuild-well-known-item-metadata.md).

##### <a name="to-examine-well-known-metadata"></a>So untersuchen Sie bekannte Metadaten

1.  Ersetzen Sie die Message-Aufgabe im Code-Editor durch diese Zeile:

    ```xml
    <Message Text="Compile Filename: %(Compile.Filename)" />
    ```

2.  Speichern Sie die Projektdatei.

3.  Geben Sie im **Befehlsfenster** die folgende Zeile ein, und führen Sie diese aus:

    ```cmd
    msbuild buildapp.csproj /t:HelloWorld
    ```

4.  Prüfen Sie die Ausgabe. Die folgenden Zeilen sollten angezeigt werden:

    ```
    Compile Filename: Form1
    Compile Filename: Form1.Designer
    Compile Filename: Program
    Compile Filename: AssemblyInfo
    Compile Filename: Resources.Designer
    Compile Filename: Settings.Designer
    ```

Der Vergleich der beiden obigen Beispiele zeigt, dass zwar nicht jedes Element im Compile-Elementtyp DependentUpon-Metadaten aufweist, doch alle Elemente die bekannten Filename-Metadaten aufweisen.

### <a name="metadata-transformations"></a>Transformationen von Metadaten
 Elementlisten können in neue Elementlisten umgewandelt werden. Eine Elementliste transformieren Sie mit der folgenden Syntax, wobei „\<ItemType>“ den Namen des Elementtyps darstellt und „\<MetadataName>“ den Namen der Metadaten:

```xml
@(ItemType -> '%(MetadataName)')
```

Beispielsweise kann eine Elementliste von Quelldateien über einen Ausdruck, z. B. `@(SourceFiles -> '%(Filename).obj')`, in eine Auflistung von Objektdateien transformiert werden. Weitere Informationen finden Sie unter [Transformationen](../msbuild/msbuild-transforms.md).

##### <a name="to-transform-items-using-metadata"></a>So transformieren Sie Elemente mit Metadaten

1.  Ersetzen Sie die Message-Aufgabe im Code-Editor durch diese Zeile:

    ```xml
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />
    ```

2.  Speichern Sie die Projektdatei.

3.  Geben Sie im **Befehlsfenster** die folgende Zeile ein, und führen Sie diese aus:

    ```cmd
    msbuild buildapp.csproj /t:HelloWorld
    ```

4.  Prüfen Sie die Ausgabe. Die folgende Zeile sollte angezeigt werden:

    ```
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak
    ```

Beachten Sie, dass die in dieser Syntax ausgedrückten Metadaten keine Batchverarbeitung verursachen.

## <a name="whats-next"></a>Ausblick
 Probieren Sie die [Exemplarische Vorgehensweise: Erstellen einer neuen MSBuild-Projektdatei](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) aus, um zu erfahren, wie Sie schrittweise eine einfache Projektdatei erstellen können.

## <a name="see-also"></a>Siehe auch

- [Übersicht über MSBuild](../msbuild/msbuild.md)
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
