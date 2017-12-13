---
title: Anpassen des Buildsystems | Microsoft-Dokumentation
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: 2d17a952c58e5ef7e593ee7aeb1980e09a376800
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="customizing-the-build-system"></a>Anpassen des Buildsystems

MSBuild ist ein von Microsoft entwickeltes Buildmodul, mit dem hauptsächlich .NET-Anwendungen erstellt werden können. Das Mono-Framework hat zudem seine eigene Implementierung des Buildmoduls von Microsoft mit dem Namen **xbuild**. xbuild wurde allerdings auslaufen gelassen, um auf allen Betriebssystemen Platz für MSBuild zu machen.

**MSBuild** wird hauptsächlich für Buildsysteme für Projekte in Visual Studio für Mac verwendet. 

MSBuild arbeitet mit einem Eingabensatz, wie z.B. Quelldateien, und wandelt diese in Ausgaben um, wie z.B. ausführbare Dateien, und erreicht diese Ausgabe, indem es Tools wie z.B. den Compiler aufruft. 


## <a name="msbuild-file"></a>MSBuild-Datei

MSBuild verwendet eine XML-Datei, die die *Elemente* definiert, die Teil Ihres Projekts sind (wie z.B. Bildressourcen) sowie die *Eigenschaften*, die zum Erstellen Ihres Projekts erforderlich sind. Diese Projektdatei hat immer eine Dateiendung mit `proj`, wie z.B. `.csproj` für C#-Projekte. 

### <a name="viewing-the-msbuild-file"></a>Anzeigen der MSBuild-Datei
Sie können diese Datei finden, indem Sie mit der rechten Maustaste auf den Projektnamen und dann auf **Im Finder anzeigen** klicken. Dann werden alle Dateien und Ordner angezeigt, die mit Ihrem Projekt in Verbindung stehen, einschließlich der `.csproj`-Datei, wie unten veranschaulicht:

![](media/customizing-build-system-image1.png)

Sie können die `.csproj`-Datei auch in einer neuen Registerkarte in Visual Studio für Mac anzeigen, indem Sie mit der rechten Maustaste auf Ihren Projektnamen klicken und dann zu **Extras > Datei bearbeiten** navigieren.

![](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>Zusammensetzung der MSBuild-Datei

Alle MSBuild-Dateien enthalten ein erforderliches `Project`-Stammelement, wie unten dargestellt:

```
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

Normalerweise importiert das Projekt auch eine `.targets`-Datei, die viele Regeln enthält, in denen beschrieben wird, wie Sie verschiedenen Dateien verarbeiten und erstellen können. Dies tritt meistens gegen Ende Ihrer `proj`-Datei auf und sieht für C#-Projekte ungefähr folgendermaßen aus:

```
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

Die .targets-Datei ist eine weitere MSBuild-Datei. Die Datei enthält MSBuild-Code, der von mehreren Objekten wiederverwendet werden kann. Die `Microsoft.CSharp.targets`-Datei, die sich in einem Verzeichnis befindet, das von der `MSBuildBinPath`-Eigenschaft (oder -Variablen) dargestellt wird, enthält z.B. die Logik zum Erstellen von C+-Assemblys aus C#-Quelldateien.

### <a name="items-and-properties"></a>Elemente und Eigenschaften

Es gibt zwei grundlegende Datentypen in MSBuild: *Elemente* und *Eigenschaften*, die weitere unten ausführlicher besprochen werden.

#### <a name="properties"></a>Eigenschaften

Eigenschaften sind Schlüssel-Wert-Paare, die verwendet werden, um Einstellungen zu speichern, die die Kompilierung beeinträchtigen, wie z.B. Compileroptionen.

Sie werden mit einer Eigenschaftengruppe festgelegt und können wiederum beliebig viele Eigenschaftengruppen enthalten, die beliebig viele Eigenschaften enthalten können. 

Die Eigenschaftengruppe einer einfachen Konsolenanwendung kann z.B. folgendermaßen aussehen:

```
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

#### <a name="items"></a>Elemente

Elemente bieten eine Möglichkeit zum Verarbeiten von Eingaben in einem Buildsystem als Listen oder Mengen und stellen normalerweise Dateien dar. Jedes Element hat einen *Elementtyp*, eine *Elementspezifikation* und optionale willkürliche *Metadaten*. Beachten Sie, dass MSBuild keine einzelnen Elemente verarbeitet, sondern alle Elemente eines angegebenen Typs akzeptiert: Dies wird als *Elementmenge* bezeichnet.

Elemente werden durch die Deklaration einer `ItemGroup` erstellt. Es kann eine beliebige Zahl an Elementgruppen geben, die wiederum eine beliebige Zahl an Elementen enthalten können. 

Durch den untenstehenden Codeabschnitt werde die iOS-Startbildschirme erstellt. Diese sind vom Typ `BundleResource`, und die Spezifikation ist der Pfad des Images:

```
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

* [MSDN – Übersicht](https://msdn.microsoft.com/library/dd393574.aspx)
* [MSDN – Konzepte](https://msdn.microsoft.com/library/dd637714.aspx)


