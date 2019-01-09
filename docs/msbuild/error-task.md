---
title: Error-Aufgabe| Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d9e55fe148ccb973a6fdcbf0722d354d91cc1816
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53833017"
---
# <a name="error-task"></a>Fehleraufgabe
Beendet einen Build, und protokolliert einen Fehler basierend auf einer ausgewerteten Bedingungsanweisung.  

## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `Error` -Aufgabe beschrieben.  


| Parameter | Beschreibung |
|---------------| - |
| `Code` | Optionaler `String` -Parameter.<br /><br /> Der dem Fehler zuzuordnende Fehlercode. |
| `File` | Optionaler `String` -Parameter.<br /><br /> Der Name der Datei, die den Fehler enthält. Wenn kein Dateiname angegeben wird, wird die Datei verwendet, die die Error-Aufgabe enthält. |
| `HelpKeyword` | Optionaler `String` -Parameter.<br /><br /> Das dem Fehler zuzuordnende Hilfeschlüsselwort. |
| `Text` | Optionaler `String` -Parameter.<br /><br /> Der Fehlertext, den [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] protokolliert, wenn die `Condition`-Parameter `true` ergeben. |

## <a name="remarks"></a>Hinweise  
 Die `Error`-Aufgabe ermöglicht es [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projekten, Fehlertexte an Protokollierungen herauszugeben und die Buildausführung zu beenden.  

 Wenn der `Condition`-Parameter `true` entspricht wird der Build beendet und ein Fehler protokolliert. Wenn kein `Condition`-Parameter vorhanden ist, wird der Fehler Protokolliert und die Buildausführung wird beendet. Weitere Informationen zur Protokollierung finden Sie unter [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md).  

 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).  

## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird überprüft, ob alle erforderlichen Eigenschaften festgelegt sind. Wenn sie nicht festgelegt sind, löst das Projekt ein Fehlerereignis aus, und protokolliert den Wert des `Text`-Parameters der `Error`-Aufgabe.  

```xml  
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
 [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)   
 [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)