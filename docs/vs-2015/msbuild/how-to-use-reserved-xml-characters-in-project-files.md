---
title: 'Vorgehensweise: Verwenden reservierter XML-Zeichen in Projektdateien | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de8e6693b56a36f9b795b132e0181aa0531c7f33
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199666"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Gewusst wie: Verwenden reservierter XML-Zeichen in Projektdateien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Wenn Sie Projektdateien erstellen, müssen Sie reservierte XML-Zeichen verwenden, z.B. in Eigenschaftswerten oder Aufgabenparameterwerten. Einige reservierte Zeichen müssen jedoch durch eine benannte Entität ersetzt werden, sodass die Projektdatei analysiert werden kann.  
  
## <a name="using-reserved-characters"></a>Reservierte Zeichen verwenden  
 Die folgende Tabelle beschreibt die reservierten XML-Zeichen, die durch die entsprechende benannte Entität ersetzt werden müssen, damit die Projektdatei analysiert werden kann.  
  
|Reserviertes Zeichen|Benannte Entität|  
|------------------------|------------------|  
|\<|&lt;|  
|>|&gt;|  
|&|&amp;|  
|"|&quot;|  
|'|&apos;|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>Doppelte Anführungszeichen in einer Projektdatei verwenden  
  
-   Ersetzen Sie die doppelten Anführungszeichen durch die entsprechende benannte Entität &quot;. Um beispielsweise doppelte Anführungszeichen um die `EXEFile`-Elementliste zu setzen, geben Sie Folgendes ein:  
  
    ```  
    <Message Text="The output file is "@(EXEFile)"."/>  
    ```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel werden doppelte Anführungszeichen zum Markieren des Dateinamens in der Meldung benutzt, die von der Projektdatei ausgegeben wird.  
  
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
 [MSBuild-Referenz](../msbuild/msbuild-reference.md) [MSBuild](msbuild.md)


