---
title: "T4 Include Directive | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8c3de9f3-755a-47c5-a30a-65717dcaaac2
caps.latest.revision: 6
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 6
---
# T4 Include Directive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In einer Textvorlage in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] können Sie Text aus einer anderen Datei mit einer `<#@include#>`\-Direktive einschließen.  Sie können `include`\-Direktiven an einer beliebigen Stelle in einer Textvorlage platzieren, und zwar vor dem ersten Klassenfunktionsblock `<#+ ... #>`.  Die eingeschlossenen Dateien können auch `include`\-Direktiven und andere Direktiven enthalten.  Dadurch können Sie Vorlagencode und Text mit Codebausteinen zwischen Vorlagen freigeben.  
  
## Verwenden von Include\-Direktiven  
  
```  
<#@ include file="filePath" [once="true"] #>  
```  
  
-   `filePath` kann absolut oder relativ zur aktuellen Vorlagendatei sein.  
  
     Außerdem können bestimmte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Erweiterungen eigene Verzeichnisse angeben, in denen nach Includedateien gesucht werden soll.  Wenn Sie z. B. das Visualisierungs\- und Modellierungs\-SDK \(DSL\-Tools\) installiert haben, wird der folgende Ordner der Includeliste hinzugefügt: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates`.  
  
     Diese zusätzlichen Includeordner können von der Dateierweiterung der einschließenden Datei abhängen.  Zum Beispiel können nur einschließende Dateien mit der Dateierweiterung `.tt` auf den Includeordner der DSL\-Tools zugreifen.  
  
-   `filePath` kann durch "%" begrenzte Umgebungsvariablen einschließen.  Beispiel:  
  
    ```  
    <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>  
    ```  
  
-   Für einen Namen einer eingeschlossenen Datei muss nicht die Erweiterung `".tt"` verwendet werden.  
  
     Sie können für eingeschlossene Dateien ggf. eine andere Erweiterung verwenden, z. B. `".t4"`.  Dies liegt daran, dass beim Hinzufügen einer `.tt`\-Datei zu einem Projekt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die Eigenschaft **Benutzerdefiniertes Tool** automatisch auf `TextTemplatingFileGenerator` festlegt.  Normalerweise sollen eingeschlossene Dateien nicht einzeln transformiert werden.  
  
     Andererseits sollten Sie beachten, dass die Dateierweiterung in einigen Fällen Einfluss darauf hat, welche zusätzlichen Ordner nach Includedateien durchsucht werden.  Dies könnte wichtig sein, wenn eine eingeschlossene Datei andere Dateien enthält.  
  
-   Der eingeschlossene Inhalt wird fast so verarbeitet, als wäre er Teil der jeweiligen Textvorlage.  Sie können jedoch auch dann eine Datei einschließen, die einen Klassenfunktionsblock `<#+...#>` enthält, wenn nach der `include`\-Direktive normale Text\- und Standardkontrollblöcke eingefügt werden.  
  
-   Verwenden Sie `once="true"`, um sicherzustellen, dass eine Vorlage nur einmal eingeschlossen wird, auch wenn sie von mehr als einer Includedatei aufgerufen wird.  
  
     Diese Funktion erleichtert es, eine Bibliothek mit wiederverwendbaren T4\-Ausschnitten zu erstellen, die Sie nach Belieben einschließen können, ohne zu befürchten, dass irgendein anderer Ausschnitt sie bereits eingeschlossen hat. Angenommen, Sie verfügen beispielsweise über eine Bibliothek mit sehr differenzierten Ausschnitten, die mit der Verarbeitung von Vorlagen und der C\#\-Generierung befasst sind. Daraufhin werden diese durch aufgabenspezifischere Hilfsprogramme verwendet, wie zum Generieren von Ausnahmen. Diese können Sie dann von jeder beliebigen anwendungsspezifischeren Vorlage aus verwendet.  Wenn Sie das Abhängigkeitsdiagramm zeichnen, sehen Sie, dass einige Ausschnitte mehrmals eingeschlossen würden.  Die Parameter `once` verhindert aber die darauffolgenden Einschlüsse.  
  
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
  
 **Die infolge des Vorgangs generierte Datei "MyTextTemplate.txt":**  
  
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
 Sie können Visual Studio\-Makros wie $ \(SolutionDir\) in einer Includedirektive verwenden, nicht aber in MSBuild.  Wenn Sie Vorlagen im Buildcomputer transformieren möchten, müssen Sie dies mithilfe von Projekteigenschaften tun.  
  
 Bearbeiten Sie die CSPROJ\- oder VBPROJ\-Datei, und definieren Sie eine Projekteigenschaft.  In folgendem Beispiel wird eine Eigenschaft mit dem Namen `myIncludeFolder` definiert:  
  
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