---
title: SetEnv-Aufgabe| Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- SetEnv task (MSBuild (Visual C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: "6"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 0223d57cf4c16166149b1fc9e8903f563b724d20
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="setenv-task"></a>SetEnv-Aufgabe
Legt den Wert einer bestimmten Umgebungsvariable fest oder löscht ihn.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der **SetEnv**-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|**Name**|Erforderlicher **String**-Parameter.<br /><br /> Der Name einer Umgebungsvariablen.|  
|**OutputEnvironmentVariable**|Optionaler **String**-Ausgabeparameter.<br /><br /> Enthält den Wert, der der Umgebungsvariablen zugewiesen ist, die durch den Parameter **Name** angegeben wird.|  
|**Prefix**|Erforderlicher `Boolean`-Parameter.<br /><br /> Wenn `true`, wird der Wert des **Value**-Parameters vor dem Wert der Umgebungsvariablen verkettet, die durch den **Name**-Parameter angegeben wird. Anschließend wird der Umgebungsvariable das Ergebnis zugewiesen. Wenn `false`, wird der Umgebungsvariablen nur der Wert des **Value**-Parameters zugewiesen.|  
|**Target**|Optionaler **String**-Parameter.<br /><br /> Gibt den Ort an, an dem eine Umgebungsvariable gespeichert wird. Geben Sie „`User`“ oder „`Machine`“an.<br /><br /> Weitere Informationen finden Sie unter „EnvironmentVariableTarget-Enumeration“ auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website.|  
|**Wert**|Optionaler **String**-Parameter.<br /><br /> Der Wert, der der Umgebungsvariablen zugewiesen ist, die durch den Parameter **Name** angegeben wird. Die Variable wird gelöscht wenn **Value** leer und die Variable vorhanden ist. Wenn die Variable vorhanden ist, tritt kein Fehler auf, obwohl der Vorgang nicht ausgeführt werden kann.<br /><br /> Weitere Informationen finden Sie unter „Environment::SetEnvironmentVariable-Methode“ auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)