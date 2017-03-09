---
title: "Gewusst wie: Erstellen eines Projekts, das &#252;ber Ressourcen verf&#252;gt | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ressourcendateien Kompilieren mit MSBuild"
  - "Ressourcen [Visual Studio] Kompilieren mit MSBuild"
  - "[Projekte [.NET Framework], erstellen"
  - "MSBuild Erstellen eines Projekts mit Ressourcen"
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Erstellen eines Projekts, das &#252;ber Ressourcen verf&#252;gt
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie lokalisierte Versionen eines Projekts erstellen, müssen alle Benutzeroberflächenelemente in Ressourcendateien für die verschiedenen Sprachen getrennt werden. Wenn das Projekt nur Zeichenfolgen verwendet werden, können die Ressourcendateien Textdateien verwenden. Alternativ können Sie RESX-Dateien als Ressourcendateien verwenden.  
  
## <a name="compiling-resources-with-msbuild"></a>Kompilieren von Ressourcen mit MSBuild  
 Die Bibliothek von allgemeinen Aufgaben, die mit geliefert wird [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] enthält eine `GenerateResource` Aufgabe, die Sie zur Kompilierung von Ressourcen in RESX-oder Textdateien verwenden können. Diese Aufgabe umfasst die `Sources` Parameter, um anzugeben, welche Ressourcendateien kompiliert und die `OutputResources` Parameter, um die Namen für die Ausgabedateien für die Ressource angeben. Weitere Informationen zu den `GenerateResource` task, finden Sie unter [GenerateResource-Aufgabe](../msbuild/generateresource-task.md).  
  
#### <a name="to-compile-resources-with-msbuild"></a>Zur Kompilierung von Ressourcen mit MSBuild  
  
1.  Identifizieren von Ressourcendateien des Projekts, und übergeben sie die `GenerateResource` Aufgabe, entweder als Elementlisten oder als Dateinamen.  
  
2.  Geben Sie die `OutputResources` Parameter von der `GenerateResource` Aufgabe können Sie die Namen für die Ausgabedateien für die Ressource festlegen.  
  
3.  Verwenden der `Output` Element des Vorgangs zum Speichern des Werts, der die `OutputResources` Parameter in einem Element.  
  
4.  Verwenden Sie das erstellte aus der `Output` Element als Eingabe in eine andere Aufgabe.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht wie die `Output` Element gibt an, dass die `OutputResources` -Attribut des der `GenerateResource` Aufgabe enthält die kompilierten Ressourcendateien `alpha.resources` und `beta.resources` und, die diese beiden Dateien befinden sich innerhalb der `Resources` Elementliste. Durch diese RESOURCES-Dateien als eine Auflistung von Elementen mit dem gleichen Namen identifiziert werden, problemlos können sie als Eingaben für eine andere Aufgabe, z. B. die [Csc](../msbuild/csc-task.md) Aufgabe.  
  
 Diese Aufgabe ist äquivalent zur Verwendung der **/compile** switch [Resgen.exe](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md):  
  
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
 Die folgenden Beispielprojekt enthält zwei Aufgaben: die `GenerateResource` Aufgabe zur Kompilierung von Ressourcen und die `Csc` Aufgabe zum Kompilieren der Quellcodedateien und kompilierten Ressourcendateien. Ressourcendateien kompiliert die `GenerateResource` Aufgabe befinden sich der `Resources` Element und wird an die `Csc` Aufgabe.  
  
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
[MSBuild](../msbuild/msbuild1.md)  
 [GenerateResource-Aufgabe](../msbuild/generateresource-task.md)   
 [Csc-Aufgabe](../msbuild/csc-task.md)   
 [Resgen.exe (Resource File Generator)](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md)