---
title: T4-Include-Direktive | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c3de9f3-755a-47c5-a30a-65717dcaaac2
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e8de721b7f26152cd4e7f5df1ee7eb4d04770511
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49835942"
---
# <a name="t4-include-directive"></a>T4-Include-Anweisung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In einer Textvorlage in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] können Sie Text aus einer anderen Datei mit einer `<#@include#>`-Anweisung einschließen. Sie können `include`-Direktiven an einer beliebigen Stelle in einer Textvorlage platzieren, und zwar vor dem ersten Klassenfunktionsblock `<#+ ... #>`. Die eingeschlossenen Dateien können auch `include`-Direktiven und andere Direktiven enthalten. Dadurch können Sie Vorlagencode und Text mit Codebausteinen zwischen Vorlagen freigeben.  
  
## <a name="using-include-directives"></a>Verwenden von Include-Direktiven  
  
```  
<#@ include file="filePath" [once="true"] #>  
```  
  
- `filePath` kann absolut oder relativ zur aktuellen Vorlagendatei sein.  
  
   Außerdem können bestimmte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Erweiterungen eigene Verzeichnisse angeben, in denen nach Includedateien gesucht werden soll. Z. B., wenn Sie die Visualisierungs- und Modellierungs-SDK (DSL-Tools) installiert haben, der folgende Ordner wird hinzugefügt, der Include-Liste: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates`.  
  
   Diese zusätzlichen Includeordner können von der Dateierweiterung der einschließenden Datei abhängen. Zum Beispiel können nur einschließende Dateien mit der Dateierweiterung `.tt` auf den Includeordner der DSL-Tools zugreifen.  
  
- `filePath` kann durch "%" begrenzte Umgebungsvariablen einschließen. Zum Beispiel:  
  
  ```  
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>  
  ```  
  
- Für einen Namen einer eingeschlossenen Datei muss nicht die Erweiterung `".tt"` verwendet werden.  
  
   Sie können für eingeschlossene Dateien ggf. eine andere Erweiterung verwenden, z. B. `".t4"`. Dies liegt daran, dass beim Hinzufügen einer `.tt` Datei zu einem Projekt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] legt automatisch die **benutzerdefiniertes Tool** Eigenschaft, um `TextTemplatingFileGenerator`. Normalerweise sollen eingeschlossene Dateien nicht einzeln transformiert werden.  
  
   Andererseits sollten Sie beachten, dass die Dateierweiterung in einigen Fällen Einfluss darauf hat, welche zusätzlichen Ordner nach Includedateien durchsucht werden. Dies könnte wichtig sein, wenn eine eingeschlossene Datei andere Dateien enthält.  
  
- Der eingeschlossene Inhalt wird fast so verarbeitet, als wäre er Teil der jeweiligen Textvorlage. Sie können jedoch auch dann eine Datei einschließen, die einen Klassenfunktionsblock `<#+...#>` enthält, wenn nach der `include`-Direktive normale Text- und Standardkontrollblöcke eingefügt werden.  
  
- Verwenden Sie `once="true"`, um sicherzustellen, dass eine Vorlage nur einmal eingeschlossen wird, auch wenn sie von mehr als einer Includedatei aufgerufen wird.  
  
   Dieses Feature macht es einfach, um eine Bibliothek mit wiederverwendbaren T4-Ausschnitten zu erstellen, die Sie am einschließen können wird, ohne sich Gedanken machen, die verfügt über einige andere Codeausschnitt bereits diese enthalten.  Nehmen wir beispielsweise an, dass Sie eine Bibliothek mit sehr differenzierten Ausschnitten verfügen, die mit dem Verarbeiten der Vorlage und C#-Generierung zu behandeln.  Diese dienen wiederum durch einige mehr aufgabenspezifische-Hilfsprogramme, z. B. das Generieren von Ausnahmen, die Sie über eine beliebige weitere anwendungsspezifische-Vorlage verwenden können. Wenn Sie das Abhängigkeitsdiagramm zeichnen, sehen Sie, dass einige Ausschnitte mehrmals eingeschlossen würden. Die Parameter `once` verhindert aber die darauffolgenden Einschlüsse.  
  
  **MyTextTemplate.tt:**  
  
```  
<#@ output extension=".txt" #>  
Output message 1 (from top template).  
<#@ include file="TextFile1.t4"#>  
Output message 5 (from top template).  
<#  
   GenerateMessage(6); // defined in TextFile1.t4  
   AnotherGenerateMessage(7); // defined in TextFile2.t4  
#>  
  
```  
  
 **TextFile1.t4:**  
  
```  
   Output Message 2 (from included file).  
<#@include file="TextFile2.t4" #>  
   Output Message 4 (from included file).  
<#+ // Start of class feature control block.  
void GenerateMessage(int n)  
{  
#>  
   Output Message <#= n #> (from GenerateMessage method).  
<#+  
}  
#>  
  
```  
  
 **TextFile2.t4:**  
  
```  
        Output Message 3 (from included file 2).  
<#+ // Start of class feature control block.  
void AnotherGenerateMessage(int n)  
{  
#>  
       Output Message <#= n #> (from AnotherGenerateMessage method).  
<#+  
}  
#>  
  
```  
  
 **Die generierte Datei "MyTextTemplate.txt":**  
  
```  
Output message 1 (from top template).  
   Output Message 2 (from included file).  
        Output Message 3 (from included file 2).  
  
   Output Message 4 (from included file).  
  
Output message 5 (from top template).  
   Output Message 6 (from GenerateMessage method).  
       Output Message 7 (from AnotherGenerateMessage method).  
  
```  
  
##  <a name="msbuild"></a> Verwenden von Projekteigenschaften in MSBuild und Visual Studio  
 Sie können Visual Studio-Makros wie $ (SolutionDir) in einer Includeanweisung verwenden, nicht aber in MSBuild. Wenn Sie Vorlagen im Buildcomputer transformieren möchten, müssen Sie dies mithilfe von Projekteigenschaften tun.  
  
 Bearbeiten Sie die CSPROJ- oder VBPROJ-Datei, und definieren Sie eine Projekteigenschaft. In folgendem Beispiel wird eine Eigenschaft mit dem Namen `myIncludeFolder` definiert:  
  
```xml  
<!-- Define a project property, myIncludeFolder: -->  
<PropertyGroup>  
    <myIncludeFolder>$(MSBuildProjectDirectory)\..\libs</myIncludeFolder>  
</PropertyGroup>  
  
<!-- Tell the MSBuild T4 task to make the property available: -->  
<ItemGroup>  
    <T4ParameterValues Include="myIncludeFolder">  
      <Value>$(myIncludeFolder)</Value>  
    </T4ParameterValues>  
  </ItemGroup>  
  
```  
  
 Nun können Sie die Projekteigenschaft in Textvorlagen verwenden, die sowohl in Visual Studio als auch in MSBuild ordnungsgemäß transformiert werden:  
  
```  
<#@ include file="$(myIncludeFolder)\defs.tt" #>  
```



