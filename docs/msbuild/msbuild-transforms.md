---
title: MSBuild-Transformationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
caps.latest.revision: 13
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b02c8b6c16bf0d1ffd75ee52d34d72446a06ed25
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="msbuild-transforms"></a>MSBuild-Transformationen
Eine Transformation ist eine 1:1-Konvertierung von einer Elementliste in eine andere. Über Transformationen können nicht nur Elementlisten in einem Projekt transformiert werden, sondern auch direkte Zuordnungen zwischen Eingaben und Ausgaben eines Ziels identifiziert werden. In diesem Artikel werden Transformationen thematisiert, und es wird erläutert, wie sie von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zur effizienteren Erstellung von Projekten verwendet werden.  
  
## <a name="transform-modifiers"></a>Transformationsmodifizierer  
Transformationen werden nicht auf willkürliche Art und Weise erstellt, sondern sind auf eine spezielle Syntax beschränkt, in der alle Transformationsmodifizierer dem Format %(*Elementmetadatenname*) entsprechen müssen. Alle Elementmetadaten können als Transfomationsmodifizierer verwendet werden, einschließlich des bekannten Elementmetadatenelements, das jedem Element bei der Erstellung zugewiesen wird. Eine vollständige Liste bekannter Metadaten finden Sie unter [Well-known Item Metadata (Bekannte Elementmetadaten)](../msbuild/msbuild-well-known-item-metadata.md).  
  
Im folgenden Beispiel wird eine Liste mit *RESX*-Dateien in eine Liste mit *RESOURCES*-Dateien transformiert. Der Transformationsmodifizierer %(dateiname) gibt an, dass jeder *RESOURCES*-Datei derselbe Dateiname wie der zugehörigen *RESX*-Datei zugeordnet wird.  
  
```  
@(RESXFile->'%(filename).resources')  
```

Wenn die Elemente in der @(resxfile)-Elementliste beispielsweise *Form1.resx*, *Form2.resx* und *Form3.resx* sind, lauten die Ausgaben in der transformierten Liste *Form1.resources*, *Form2.resources* und *Form3.resources*.  

> [!NOTE]
>  Sie können eine benutzerdefinierte Trennlinie für eine transformierte Elementliste auf dieselbe Weise angeben, wie Sie eine Trennlinie für eine Standardelementliste angeben. Verwenden Sie beispielsweise das folgende XML, um eine transformierte Elementliste durch ein Komma („,“) anstatt durch das standardmäßige Semikolon („;“) zu unterteilen:  
> `@(RESXFile->'Toolset\%(filename)%(extension)', ',')`
  
## <a name="using-multiple-modifiers"></a>Verwenden mehrerer Modifizierer  
 Ein Tranformationsausdruck kann mehrere Modifizierer enthalten, die in einer beliebigen Reihenfolge kombiniert und wiederholt werden können. Im folgenden Beispiel wird der Name des Verzeichnisses geändert, das die Dateien enthält. Dabei behalten die Dateien allerdings ihren ursprünglichen Namen und ihre Erweiterungen.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)')  
```  
  
 Wenn die Elemente, die in der `RESXFile`-Elementliste enthalten sind, beispielsweise *Project1\Form1.resx*, *Project1\Form2.resx* und *Project1\Form3.text* sind, lauten die Ausgaben in der transformierten Liste *Toolset\Form1.resx*, *Toolset\Form2.resx* und *Toolset\Form3.text*.  
  
## <a name="dependency-analysis"></a>Abhängigkeitsanalyse  
 Tansformationen garantieren eine 1:1-Zuordnung zwischen der transformierten und der ursprünglichen Elementliste. Wenn daher ein Ziel Ausgaben erzeugt, die Transformationen der Eingaben sind, kann [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] die Zeitstempel der Ein- und Ausgaben analysieren und entscheiden, ob ein Ziel übersprungen, erstellt oder teilweise neu erstellt werden soll.  
  
 In der [Kopieraufgabe](../msbuild/copy-task.md) im folgenden Beispiel ist jede Datei in der `BuiltAssemblies`-Elementliste einer Datei im Zielordner der Aufgabe zugeordnet, die durch eine Transformation im `Outputs`-Attribut bestimmt wird. Wenn eine Datei in der `BuiltAssemblies`-Elementliste geändert wird, wird die `Copy`-Aufgabe nur für die geänderte Datei ausgeführt, und alle anderen Dateien werden übersprungen. Weitere Informationen zur Abhängigkeitsanalyse finden Sie unter [How to: Build Incrementally (Vorgehensweise: Inkrementelles Erstellen)](../msbuild/how-to-build-incrementally.md).  
  
```xml  
<Target Name="CopyOutputs"  
    Inputs="@(BuiltAssemblies)"  
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">  
  
    <Copy  
        SourceFiles="@(BuiltAssemblies)"  
        DestinationFolder="$(OutputPath)"/>  
  
</Target>  
```  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>description  
 Im folgenden Beispiel wird eine [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projektdatei dargestellt, die die Transformationen verwendet. Es wird angenommen, dass nur eine XSD-Datei im Verzeichnis C:\sub0\sub1\sub2\sub3 vorhanden ist, und dass das Arbeitsverzeichnis C:\sub0 lautet.  
  
### <a name="code"></a>Code  
  
```xml  
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
  
### <a name="comments"></a>Kommentare  
 Dieses Beispiel erzeugt die folgende Ausgabe:  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)  (MSBuild-Grundlagen)  
 [MSBuild Reference](../msbuild/msbuild-reference.md)  (MSBuild-Referenz)  
 [Gewusst wie: Inkrementelles Erstellen](../msbuild/how-to-build-incrementally.md)