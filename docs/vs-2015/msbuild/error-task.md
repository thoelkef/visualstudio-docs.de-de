---
title: Error-Aufgabe| Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Error
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Error task [MSBuild]
- MSBuild, Error task
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff957a54c27c4ae4860e31e4fb7001b7f831ab3a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212718"
---
# <a name="error-task"></a>Error-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Beendet einen Build, und protokolliert einen Fehler basierend auf einer ausgewerteten Bedingungsanweisung.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter des `Error`-Tasks beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`Code`|Optionaler `String` -Parameter.<br /><br /> Der dem Fehler zuzuordnende Fehlercode.|  
|`File`|Optionaler `String` -Parameter.<br /><br /> Der Name der Datei, die den Fehler enthält. Wenn kein Dateiname angegeben wird, wird die Datei verwendet, die die Error-Aufgabe enthält.|  
|`HelpKeyword`|Optionaler `String` -Parameter.<br /><br /> Das dem Fehler zuzuordnende Hilfeschlüsselwort.|  
|`Text`|Optionaler `String` -Parameter.<br /><br /> Der Fehlertext, den [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] protokolliert, wenn die `Condition`-Parameter `true` ergeben.|  
  
## <a name="remarks"></a>Hinweise  
 Die `Error`-Aufgabe ermöglicht es [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Projekten, Fehlertexte an Protokollierungen herauszugeben, und die Buildausführung zu beenden.  
  
 Wenn der `Condition`-Parameter `true` entspricht wird der Build beendet und ein Fehler protokolliert. Wenn kein `Condition`-Parameter vorhanden ist, wird der Fehler Protokolliert und die Buildausführung wird beendet. Weitere Informationen zur Protokollierung finden Sie unter [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird überprüft, ob alle erforderlichen Eigenschaften festgelegt sind. Wenn sie nicht festgelegt sind, löst das Projekt ein Fehlerereignis aus, und protokolliert den Wert des `Text`-Parameters der `Error`-Aufgabe.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Error  
            Text=" The 0 property must be set on the command line."  
            Condition="'$(0)' == ''" />  
        <Error  
            Text="The FREEBUILD property must be set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)



