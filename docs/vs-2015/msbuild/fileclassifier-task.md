---
title: FileClassifier-Aufgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- classifying a resource set to embed in an assembly [WPF MSBuild]
- non-localizable resources [WPF MSBuild], classifying to embed in an assembly
- FileClassifier task [WPF MSBuild]
ms.assetid: 14e03310-fcc0-4bb2-a84d-cda12be66367
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06decaf5a2a59b4efb2e4f30f41298ebd3e5d533
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524192"
---
# <a name="fileclassifier-task"></a>FileClassifier-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [FileClassifier-Aufgabe](https://docs.microsoft.com/visualstudio/msbuild/fileclassifier-task).  
  
  
Der <xref:Microsoft.Build.Tasks.Windows.FileClassifier>-Task klassifiziert eine Gruppe von Quellressourcen als diejenigen, die in eine Assembly eingebettet werden. Wenn eine Ressource nicht lokalisierbar ist, wird sie in die Hauptanwendungsassembly eingebettet; andernfalls wird sie in eine Satellitenassembly eingebettet.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`CLREmbeddedResource`|Nicht verwendet.|  
|`CLRResourceFiles`|Nicht verwendet.|  
|`CLRSatelliteEmbeddedResource`|Nicht verwendet.|  
|`Culture`|Optionaler **String**-Parameter.<br /><br /> Legt die Kultur für den Build fest. Dieser Wert kann **NULL** sein, wenn der Build nicht lokalisierbar ist. Wenn der Wert **NULL** ist, ist der Standardwert der von **CultureInfo.InvariantCulture** zurückgegebene Wert in Kleinbuchstaben.|  
|`MainEmbeddedFiles`|Optionaler **ITaskItem[]**-Ausgabeparameter.<br /><br /> Gibt die nicht lokalisierbaren Ressourcen an, die in die Hauptassembly eingebettet sind.|  
|`OutputType`|Erforderlicher **String**-Parameter.<br /><br /> Gibt den Dateityp an, der in die angegebenen Quelldateien eingebettet werden soll. Gültige Werte sind **exe**, **winexe**, oder **library**.|  
|`SatelliteEmbeddedFiles`|Optionaler **ITaskItem[]**-Ausgabeparameter.<br /><br /> Gibt die lokalisierbaren Dateien an, die für die durch den **Culture**-Parameter angegebene Kultur in die Satellitenassembly eingebettet werden.|  
|`SourceFiles`|Erforderlicher **ITaskItem[]**-Parameter.<br /><br /> Gibt die Liste der zu klassifizierenden Dateien an.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn der **Culture**-Parameter nicht festgelegt ist, sind alle mit dem **SourceFiles**-Parameter angegebenen Ressourcen nicht lokalisierbar; andernfalls sind sie lokalisierbar, es sei denn, sie sind mit einem **Localizable**-Attribut verknüpft, das auf **false** festgelegt ist.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird eine einzelne Quelldatei als Ressource klassifiziert und dann in eine Satellitenassembly für die Kultur kanadisches Französisch (fr-CA) eingebettet.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.FileClassifier"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <ItemGroup>  
    <Resource Include="Resource1.bmp" />  
  </ItemGroup>  
  <Target Name="FileClassifierTask">  
    <FileClassifier  
      SourceFiles="Resource1.bmp"  
      Culture="fr-CA"  
      OutputType="exe" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [WPF-MSBuild-Referenz](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [MSBuild Reference](../msbuild/msbuild-reference.md)  (MSBuild-Referenz)  
 [Task Reference](../msbuild/msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [Erstellen einer WPF-Anwendung (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)



