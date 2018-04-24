---
title: Message-Aufgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0555ae538cb473d436727da67af40be037c992a4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="message-task"></a>Message-Aufgabe
Protokolliert eine Meldung während eines Builds  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter des `Message`-Tasks beschrieben.  
  
|Parameter|description|  
|---------------|-----------------|  
|`Importance`|Optionaler `String` -Parameter.<br /><br /> Gibt die Wichtigkeit der Nachricht an. Dieser Parameter kann den Wert `high`, `normal` oder `low`haben. Der Standardwert ist `normal`.|  
|`Text`|Optionaler `String` -Parameter.<br /><br /> Der zu protokollierende Fehlertext.|  
  
## <a name="remarks"></a>Hinweise  
 Aufgrund der `Message`-Aufgabe können [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projekte in verschiedenen Schritten des Buildprozesses Nachrichten an die Protokollierungen senden.  
  
 Wenn der `Condition`-Parameter `true` ergibt, wird der Wert des `Text`-Parameters protokolliert und der Build weiter ausgeführt. Wenn kein `Condition`-Parameter vorhanden ist, wird der Nachrichtentext protokolliert. Weitere Informationen zur Protokollierung finden Sie unter [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Die Nachricht wird in der Regel an die MSBuild-Konsolenprotokollierung gesendet. Sie können diese Einstellung ändern, indem Sie den <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>-Parameter festlegen. Die Protokollierung interpretiert den `Importance` Parameter.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel werden Nachrichten in allen registrierten Protokollierungen protokolliert.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="DisplayMessages">  
        <Message Text="Project File Name = $(MSBuildProjectFile)" />  
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)