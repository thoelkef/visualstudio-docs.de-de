---
title: Anpassen des Buildsystems
description: In diesem Artikel erhalten Sie eine kurze Einführung in das MSBuild-System, das von Visual Studio für Mac verwendet wird.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: 97416ef126ee77f9955d8fa486d7bb7e2ceb725e
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983450"
---
# <a name="customizing-the-build-system"></a>Anpassen des Buildsystems

MSBuild ist eine von Microsoft entwickelte Build-Engine, mit der hauptsächlich .NET-Anwendungen erstellt werden können. Das Mono-Framework hat zudem seine eigene Implementierung der Build-Engine von Microsoft mit dem Namen **xbuild**. xbuild wurde jedoch abgeschafft, damit MSBuild unter sämtlichen Betriebssystemen ausgeführt werden kann.

**MSBuild** wird hauptsächlich für Buildsysteme für Projekte in Visual Studio für Mac verwendet.

MSBuild arbeitet mit einem Eingabensatz, wie z.B. Quelldateien, und wandelt diese in Ausgaben um, wie z.B. ausführbare Dateien. Diese Ausgabe wird durch den Aufruf von Tools wie dem Compiler erzielt.

## <a name="msbuild-file"></a>MSBuild-Datei

MSBuild verwendet eine XML-Datei, die die *Elemente* definiert, die Teil Ihres Projekts sind (wie z.B. Bildressourcen) sowie die *Eigenschaften*, die zum Erstellen Ihres Projekts erforderlich sind. Diese Projektdatei hat immer eine Dateiendung mit `proj`, wie z.B. `.csproj` für C#-Projekte.

### <a name="viewing-the-msbuild-file"></a>Anzeigen der MSBuild-Datei

Sie finden die MSBuild-Datei, indem Sie mit der rechten Maustaste auf den Projektnamen und dann auf **Im Finder anzeigen** klicken. Im Finderfenster werden alle Dateien und Ordner angezeigt, die mit Ihrem Projekt in Verbindung stehen, einschließlich der `.csproj`-Datei, wie in der folgenden Abbildung dargestellt:

![Speicherort der CSPROJ-Datei im Finder](media/customizing-build-system-image1.png)

Um die `.csproj`-Datei auf einer neuen Registerkarte in Visual Studio für Mac anzuzeigen, klicken Sie mit der rechten Maustaste auf Ihren Projektnamen und navigieren dann zu **Extras > Datei bearbeiten**:

![CSPROJ-Datei im Quellen-Editor öffnen](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>Zusammensetzung der MSBuild-Datei

Alle MSBuild-Dateien enthalten ein erforderliches `Project`-Stammelement, wie unten dargestellt:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

Das Projekt importiert in der Regel auch eine `.targets`-Datei. Diese Datei enthält viele der Regeln, in denen beschrieben wird, wie Sie verschiedene Dateien verarbeiten und erstellen. Der Import ist in der Regel im unteren Teil Ihrer `proj`-Datei enthalten und sieht für C#-Projekte ungefähr folgendermaßen aus:

```xml
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

Die .targets-Datei ist eine weitere MSBuild-Datei. Die Datei enthält MSBuild-Code, der von mehreren Objekten wiederverwendet werden kann. Die `Microsoft.CSharp.targets`-Datei, die sich in einem Verzeichnis befindet, das von der `MSBuildBinPath`-Eigenschaft (oder -Variablen) dargestellt wird, enthält z.B. die Logik zum Erstellen von C+-Assemblys aus C#-Quelldateien.

### <a name="items-and-properties"></a>Elemente und Eigenschaften

Es gibt zwei grundlegende Datentypen in MSBuild: *Elemente* und *Eigenschaften*, die in den folgenden Abschnitten ausführlicher besprochen werden.

#### <a name="properties"></a>Eigenschaften

Eigenschaften sind Schlüssel-Wert-Paare, die verwendet werden, um Einstellungen zu speichern, die die Kompilierung beeinträchtigen, wie z.B. Compileroptionen.

Sie werden mit einer Eigenschaftengruppe festgelegt und können wiederum beliebig viele Eigenschaftengruppen enthalten, die beliebig viele Eigenschaften enthalten können.

Die Eigenschaftengruppe einer einfachen Konsolenanwendung kann z.B. wie die folgende XML-Datei aussehen:

```xml
<PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
    <ProjectGuid>{E248730E-1393-43CC-9183-FFA42F63BE81}</ProjectGuid>
    <OutputType>Exe</OutputType>
    <RootNamespace>refactoring</RootNamespace>
    <AssemblyName>refactoring</AssemblyName>
    <TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
</PropertyGroup>
```

Auf Eigenschaften kann von Ausdrücken aus mit `$()`-Syntax verwiesen werden. `$(Foo)` wird z.B. als Wert der `Foo`-Eigenschaft bewertet. Wenn die Eigenschaft nicht festgelegt wurde, wird sie als leere Zeichenfolge bewertet, ohne dass ein Fehler auftritt.

#### <a name="items"></a>Items

Elemente bieten eine Möglichkeit zum Verarbeiten von Eingaben in einem Buildsystem als Listen oder Mengen und stellen normalerweise Dateien dar. Jedes Element hat einen *Elementtyp*, eine *Elementspezifikation* und optionale willkürliche *Metadaten*. Beachten Sie, dass MSBuild keine einzelnen Elemente verarbeitet, sondern alle Elemente eines angegebenen Typs akzeptiert: Dies wird als *Elementmenge* bezeichnet.

Elemente werden durch die Deklaration einer `ItemGroup` erstellt. Es kann eine beliebige Zahl an Elementgruppen geben, die wiederum eine beliebige Zahl an Elementen enthalten können.

Durch den folgenden Codeabschnitt werden z.B. die iOS-Startbildschirme erstellt. Die Startbildschirme haben den Buildtyp `BundleResource` mit der Spezifikation wie der Pfad zu dem Image:

```xml
 <ItemGroup>
    <BundleResource Include="Resources\Default-568h%402x.png" />
    <BundleResource Include="Resources\Default%402x.png" />
    <BundleResource Include="Resources\Default.png" />
    <BundleResource Include="Resources\Default-Portrait.png" />
    <BundleResource Include="Resources\Default-Portrait%402x.png" />
    <BundleResource Include="Resources\Default-Landscape%402x.png" />
  </ItemGroup>
 ```

 Auf festgelegte Elemente kann von Ausdrücken aus mit `@()`-Syntax verwiesen werden. `@(BundleResource)` wird z.B. als Elementmenge BundleResource bewertet, sprich alle BundleResource-Elemente. Wenn es keine Elemente dieses Typs gibt, ist es leer, ohne Fehler.

## <a name="resources-for-learning-msbuild"></a>Ressourcen zu Informationen zu MSBuild

Schauen Sie sich die folgenden Ressourcen an, um mehr über MSBuild zu erfahren:

* [Übersicht über MSBuild](/visualstudio/msbuild/msbuild)
* [MSBuild-Grundlagen](/visualstudio/msbuild/msbuild-concepts)
