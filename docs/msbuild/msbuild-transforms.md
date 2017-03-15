---
title: "MSBuild Transforms | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, transforms"
  - "transforms [MSBuild]"
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# MSBuild Transforms
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine Transformation ist eine 1:1\-Konvertierung einer Elementliste in eine andere.  Über Transformationen können nicht nur Elementlisten in einem Projekt umgewandelt werden, sondern auch direkte Zuordnungen zwischen Eingaben und Ausgaben eines Ziels identifiziert werden.  In diesem Thema wird erläutert, was Transformationen sind und wie sie von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zur effizienteren Erstellung von Projekten genutzt werden können.  
  
## Transformationsmodifizierer  
 Transformationen können nicht beliebig ausgeführt werden, sondern unterliegen bestimmten Syntaxbeschränkungen, durch die alle Transformationsmodifizierer das Format %\(*ItemMetaDataName*\) aufweisen müssen.  Alle Elementmetadaten können als Transformationsmodifizierer verwendet werden.  Dazu gehören auch die bekannten Elementmetadaten, die jedem Element bei der Erstellung zugewiesen werden.  Eine Liste bekannter Elementmetadaten finden Sie unter [Well\-known Item Metadata](../msbuild/msbuild-well-known-item-metadata.md).  
  
 Im folgenden Beispiel wird eine Liste von RESX\-Dateien in eine Liste von RESOURCES\-Dateien transformiert.  Durch den Transformationsmodifizierer %\(filename\) wird festgelegt, dass jede RESOURCES\-Datei denselben Dateinamen wie die entsprechende RESX\-Datei hat.  
  
```  
@(RESXFile->'%(filename).resources')  
```  
  
> [!NOTE]
>  Benutzerdefinierte Trennzeichen für transformierte Elementlisten werden genauso festgelegt wie Trennzeichen für Standardelementlisten.  Verwenden Sie beispielsweise folgenden XML\-Code, um eine transformierte Elementauflistung durch ein Komma \(,\) anstatt durch das standardmäßige Semikolon \(;\) zu trennen.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)', ',')  
```  
  
 Die Elemente der @\(RESXFile\)\-Elementliste lauten beispielsweise `Form1.resx`, `Form2.resx` und `Form3.resx`, und die Ausgaben in der transformierten Liste lauten `Form1.resources`, `Form2.resources` und `Form3.resources`.  
  
## Verwenden mehrerer Modifizierer  
 Transformationsausdrücke können mehrere Modifizierer enthalten, die in beliebiger Reihenfolge kombiniert und wiederholt werden können.  Im folgenden Beispiel wird der Name des Verzeichnisses geändert, das die Dateien enthält. Der Originalname und die Dateinamenerweiterung werden jedoch beibehalten.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)')  
```  
  
 Wenn die in der `RESXFile`\-Elementliste enthaltenen Elemente `Project1\Form1.resx`, `Project1\Form2.resx` und `Project1\Form3.text` sind, lauten die Ausgaben in der transformierten Liste `Toolset\Form1.resx`, `Toolset\Form2.resx` und `Toolset\Form3.text`.  
  
## Abhängigkeitsanalyse  
 Bei Transformationen wird eine 1:1\-Zuordnung zwischen der transformierten und der ursprünglichen Elementliste sichergestellt.  Wenn ein Ziel Ausgaben generiert, die Transformationen der Eingaben sind, kann [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] folglich die Timestamps der Eingaben und Ausgaben analysieren und entscheiden, ob ein Ziel erstellt, teilweise neu erstellt bzw. übersprungen wird.  
  
 Mit der [Copy Task](../msbuild/copy-task.md)\-Aufgabe im folgenden Beispiel wird jede Datei in der `BuiltAssemblies`\-Elementliste einer Datei im Zielordner der Aufgabe zugeordnet, der mit einer Transformation im `Outputs`\-Attribut angegeben wird.  Wenn sich eine Datei in der `BuiltAssemblies`\-Elementliste ändert, wird die `Copy`\-Aufgabe nur für die geänderten Dateien ausgeführt. Alle anderen Dateien werden übersprungen.  Weitere Informationen zur Abhängigkeitsanalyse und zur Verwendung von Transformationen finden Sie unter [How to: Build Incrementally](../msbuild/how-to-build-incrementally.md).  
  
```  
<Target Name="CopyOutputs"  
    Inputs="@(BuiltAssemblies)"  
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">  
  
    <Copy  
        SourceFiles="@(BuiltAssemblies)"  
        DestinationFolder="$(OutputPath)"/>  
  
</Target>  
```  
  
## Beispiel  
  
### Beschreibung  
 Im folgenden Beispiel wird eine [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projektdatei veranschaulicht, die Transformationen verwendet.  In diesem Beispiel wird davon ausgegangen, dass nur eine XSD\-Datei im Verzeichnis c:\\sub0\\sub1\\sub2\\sub3 vorhanden ist und dass das Arbeitsverzeichnis c:\\sub0 ist.  
  
### Code  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Schema Include="sub1\**\*.xsd"/>  
    </ItemGroup>  
  
    <Target Name="Messages">  
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>  
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>  
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>  
        <Message Text="identity: @(Schema->'%(identity)')"/>  
        <Message Text="filename: @(Schema->'%(filename)')"/>  
        <Message Text="directory: @(Schema->'%(directory)')"/>  
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>  
        <Message Text="extension: @(Schema->'%(extension)')"/>  
    </Target>  
</Project>  
```  
  
### Kommentare  
 Folgende Ergebnisse werden zurückgegeben:  
  
```  
rootdir: C:\  
fullpath: C:\xmake\sub1\sub2\sub3\myfile.xsd  
rootdir + directory + filename + extension: C:\xmake\sub1\sub2\sub3\myfile.xsd  
identity: sub1\sub2\sub3\myfile.xsd  
filename: myfile  
directory: xmake\sub1\sub2\sub3\  
relativedir: sub1\sub2\sub3\  
extension: .xsd  
```  
  
## Siehe auch  
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [How to: Build Incrementally](../msbuild/how-to-build-incrementally.md)