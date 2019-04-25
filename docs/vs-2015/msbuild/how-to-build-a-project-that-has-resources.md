---
title: 'Vorgehensweise: Erstellen eines Projekts, das über Ressourcen verfügt | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0806df31b7e1f225ecefc823cbcbdb0a72ff2058
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59660267"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Gewusst wie: Erstellen eines Projekts, das über Ressourcen verfügt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie lokalisierte Versionen eines Projekts erstellen, müssen alle Benutzeroberflächenelemente in Ressourcendateien für die verschiedenen Sprachen eingeteilt werden. Wenn das Projekt nur Zeichenfolgen verwendet, können die Ressourcendateien Textdateien verwenden. Alternativ können Sie RESX-Dateien als Ressourcendateien verwenden.  
  
## <a name="compiling-resources-with-msbuild"></a>Kompilieren von Ressourcen mit MSBuild  
 Die Bibliothek von allgemeinen Aufgaben, die mit [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] bereitgestellt werden, enthalten eine Aufgaben `GenerateResource`, die Sie zum Kompilieren von Ressourcen in RESX- oder Textdateien verwenden können. Diese Aufgabe umfasst den Parameter `Sources`, um anzugeben, welche Ressourcendateien zu kompilieren sind, und den Parameter `OutputResources`, um Namen für die Ausgabe der Ressourcendateien anzugeben. Weitere Informationen zu der `GenerateResource`-Aufgabe finden Sie unter [GenerateResource-Aufgabe](../msbuild/generateresource-task.md).  
  
#### <a name="to-compile-resources-with-msbuild"></a>So kompilieren Sie Ressourcen mit MSBuild  
  
1.  Identifizieren Sie die Ressourcendateien des Projekts und übergeben Sie sie entweder als Elementlisten oder als Dateinamen an die `GenerateResource`-Aufgabe.  
  
2.  Geben Sie den Parameter `OutputResources` der Aufgabe `GenerateResource` an, was Ihnen ermöglicht die Namen für die Ausgabenressourcendateien festzulegen.  
  
3.  Verwenden Sie zum Speichern des Werts des Parameters `OutputResources` in einem Element das Element `Output` der Aufgabe.  
  
4.  Verwenden Sie das Element, das aus dem Element `Output` erstellt wurde, als Ausgabe in eine andere Aufgabe.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird gezeigt wie das Element `Output` angibt, dass das Attribut `OutputResources` der Aufgabe `GenerateResource` die kompilierten Ressourcendateien `alpha.resources` und `beta.resources` enthält und dass diese zwei Dateien in die Elementliste `Resources` gelegt werden. Indem Sie diese Ressourcendateien als eine Auflistung von Elementen mit gleichem Namen identifizieren, können Sie sie einfach als Eingabe für eine andere Aufgabe wie der [Csc](../msbuild/csc-task.md)-Aufgabe verwenden.  
  
 Diese Aufgabe entspricht der Verwendung des **/compile**-Schalters für [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4):  
  
 `Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`  
  
```  
<GenerateResource  
    Sources="alpha.resx; beta.txt"  
    OutputResources="alpha.resources; beta.resources">  
    <Output TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispielprojekt enthält zwei Aufgaben: die Aufgabe `GenerateResource` zur Kompilierung von Ressourcen und die Aufgabe `Csc` zum Kompilieren von Quellcodedateien und kompilierten Ressourcendateien. Die von der Aufgabe `GenerateResource` kompilierten Ressourcendateien sind im Element `Resources` gespeichert und werde an die Aufgabe `Csc` geleitet.  
  
```  
<Project DefaultTargets = "Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <Target Name="Resources">  
        <GenerateResource  
            Sources="alpha.resx; beta.txt"  
            OutputResources="alpha.resources; beta.resources">  
            <Output TaskParameter="OutputResources"  
                ItemName="Resources"/>  
        </GenerateResource>  
    </Target>  
  
    <Target Name="Build" DependsOnTargets="Resources">  
        <Csc Sources="hello.cs"  
                Resources="@(Resources)"  
                OutputAssembly="hello.exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
[MSBuild](msbuild.md)  
 [GenerateResource-Aufgabe](../msbuild/generateresource-task.md)   
 [Csc-Aufgabe](../msbuild/csc-task.md)   
 [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)
