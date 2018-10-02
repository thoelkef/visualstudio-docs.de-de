---
title: 'Vorgehensweise: Verwenden eines Ziels in mehreren Projektdateien | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ece9041d03ee8a17a4f97f8aad3971e1181edf9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513026"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Gewusst wie: Verwenden eines Ziels in mehreren Projektdateien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Verwenden eines Ziels in mehreren Projektdateien](https://docs.microsoft.com/visualstudio/msbuild/how-to-use-the-same-target-in-multiple-project-files).  
  
  
Wenn Sie mehrere [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Projektdateien autorisiert haben, haben Sie möglicherweise festgestellt, dass Sie die gleichen Aufgaben und Ziele in verschiedenen Projektdateien verwenden müssen. Statt die vollständige Beschreibung dieser Aufgaben oder Ziele in jede Projektdatei einzuschließen, können Sie ein Ziel in einer separaten Projektdatei speichern und dieses Projekt anschließend in einem beliebigen anderen Projekt importieren, in dem das Ziel verwendet werden muss.  
  
## <a name="using-the-import-element"></a>Verwenden des Import-Elements  
 Das `Import`-Element wird verwendet, um eine Projektdatei in eine andere Projektdatei einzufügen. Die Projektdatei, die importiert wird, muss eine gültige [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Projektdatei sein, die wohlgeformtes XML enthält. Das Attribut `Project` gibt den Pfad zur importierten Projektdatei an. Weitere Informationen zu dem `Import`-Element finden Sie unter [Import-Element (MSBuild)](../msbuild/import-element-msbuild.md).  
  
#### <a name="to-import-a-project"></a>So importieren Sie ein Projekt  
  
1.  Definieren Sie in der importierten Projektdatei alle Eigenschaften und Elemente, die als Parameter für Eigenschaften und Elemente im importierten Projekt verwendet werden.  
  
2.  Verwenden Sie das `Import`-Element zum Importieren des Projekts. Zum Beispiel:  
  
     `<Import Project="MyCommon.targets"/>`  
  
3.  Definieren Sie nach dem `Import`-Element alle Eigenschaften und Elemente, mit denen Standarddefinitionen von Eigenschaften und Elementen im importierten Projekt überschrieben werden müssen.  
  
## <a name="order-of-evaluation"></a>Reihenfolge der Auswertung  
 Wenn [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ein `Import`-Element erreicht, wird das importierte Projekt effektiv in das importierte Projekt an den Speicherort des `Import`-Elements eingefügt. Aus diesem Grund kann der Speicherort des `Import`-Elements Auswirkungen auf die Werte der Eigenschaften und Elemente haben. Die Eigenschaften und Elemente, die durch das importierte Projekt festgelegt wurden, und die Eigenschaften und Elemente, die vom importierten Projekt verwendet werden, müssen bekannt sein.  
  
 Wenn das Projekt erstellt wird, werden zunächst alle Eigenschaften ausgewertet, gefolgt von den Elementen. Folgende XML definiert z.B. die importierte Projektdatei MyCommon.targets:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyCommon</Name>  
    </PropertyGroup>  
  
    <Target Name="Go">  
        <Message Text="Name=$(Name)"/>  
    </Target>  
</Project>  
```  
  
 Folgende XML definiert MyApp.proj, worüber MyCommon.targets importiert wird:  
  
```  
<Project  
    DefaultTargets="Go"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyApp</Name>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
 Wenn das Projekt erstellt wird, wird die folgende Nachricht angezeigt:  
  
 `Name="MyCommon"`  
  
 Da der Import des Projekts nach der Definition der Eigenschaft `Name` in MyApp.proj erfolgt ist, wird mit der Definition von `Name` in MyCommon.targets die Definition in MyApp.proj überschrieben. Wenn der Import des Projekts vor der Definition der Eigenschaft „Name“ erfolgt, würde im Build folgende Nachricht angezeigt:  
  
 `Name="MyApp"`  
  
#### <a name="use-the-following-approach-when-importing-projects"></a>Gehen Sie beim Importieren von Projekten wie folgt vor  
  
1.  Definieren Sie in der Projektdatei alle Eigenschaften und Elemente, die als Parameter für Eigenschaften und Elemente im importierten Projekt verwendet werden.  
  
2.  Importieren Sie das Projekt.  
  
3.  Definieren Sie in der Projektdatei alle Eigenschaften und Elemente, mit denen Standarddefinitionen von Eigenschaften und Elementen im importierten Projekt überschrieben werden müssen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird die Datei MyCommon.targets dargestellt-Datei, die im zweiten Codebeispiel importiert wird. Die .targets-Datei wertet Eigenschaften des importierten Projekts für die Konfiguration des Builds aus.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>  
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>  
        <appname>$(MSBuildProjectName)</appname>  
    <PropertyGroup>  
    <Target Name="Build">  
        <Csc Sources="hello.cs"  
            Optimize="$(Optimize)"  
            OutputAssembly="$(appname).exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird die Datei MyCommon.targets importiert.  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor>RETAIL</Flavor>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Import Element (MSBuild)](../msbuild/import-element-msbuild.md)  (Import-Element (MSBuild))  
 [Ziele](../msbuild/msbuild-targets.md)



