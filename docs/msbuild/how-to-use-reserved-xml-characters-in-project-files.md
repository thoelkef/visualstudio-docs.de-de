---
title: "Gewusst wie: Verwenden reservierter XML-Zeichen in Projektdateien | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild verwenden von reservierten XML-Zeichen"
  - "MSBuild reservierte XML-Zeichen"
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Verwenden reservierter XML-Zeichen in Projektdateien
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie Projektdateien erstellen, müssen Sie reservierte XML-Zeichen, z. B. in Eigenschaftswerte oder Aufgabe Parameterwerte verwenden. Einige reservierten Zeichen müssen jedoch durch eine benannte Entität ersetzt werden, so, dass die Projektdatei analysiert werden kann.  
  
## <a name="using-reserved-characters"></a>Verwenden von reservierten Zeichen  
 Die folgende Tabelle beschreibt die reservierten XML-Zeichen, die durch die entsprechende benannte Entität ersetzt werden müssen, damit die Projektdatei analysiert werden kann.  
  
|Reservierte Zeichen|Benannte Entität|  
|------------------------|------------------|  
|\<|&lt;|  
|>|&gt;|  
|&|&amp;|  
|"|&quot;|  
|'|&apos;|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>Verwenden Sie doppelte Anführungszeichen in einer Projektdatei  
  
-   Ersetzen Sie die doppelten Anführungszeichen durch die entsprechenden benannten Entität &quot;. Um beispielsweise doppelte Anführungszeichen zu setzen die `EXEFile` Element aus, geben:  
  
    ```  
    <Message Text="The output file is "@(EXEFile)"."/>  
    ```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel werden doppelte Anführungszeichen zum Markieren Sie des Dateinamen in der Meldung, die ausgegeben wird von der Projektdatei.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>"HelloWorldCS"</appname>  
    </PropertyGroup>  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs" />  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input  
        files of type CSFile -->  
        <Csc Sources = "@(CSFile)">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile"/>  
        </Csc>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is "@(EXEFile)"."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zu MSBuild-](../msbuild/msbuild-reference.md)
 [MSBuild](../msbuild/msbuild1.md)