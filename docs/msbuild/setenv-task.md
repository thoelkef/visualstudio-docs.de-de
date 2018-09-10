---
title: SetEnv-Aufgabe| Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.setenv
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2d9cec2c76b2159e14b1e7abe19b93ab91f6688
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153773"
---
# <a name="setenv-task"></a>SetEnv-Aufgabe
Legt den Wert einer bestimmten Umgebungsvariable fest oder löscht ihn.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der **SetEnv**-Aufgabe beschrieben.  
  
|Parameter|Beschreibung |  
|---------------|-----------------|  
|**Name**|Erforderlicher **String**-Parameter.<br /><br /> Der Name einer Umgebungsvariablen.|  
|**OutputEnvironmentVariable**|Optionaler **String**-Ausgabeparameter.<br /><br /> Enthält den Wert, der der Umgebungsvariablen zugewiesen ist, die durch den Parameter **Name** angegeben wird.|  
|**Prefix**|Erforderlicher `Boolean`-Parameter.<br /><br /> Wenn `true`, wird der Wert des **Value**-Parameters vor dem Wert der Umgebungsvariablen verkettet, die durch den **Name**-Parameter angegeben wird. Anschließend wird der Umgebungsvariable das Ergebnis zugewiesen. Wenn `false`, wird der Umgebungsvariablen nur der Wert des **Value**-Parameters zugewiesen.|  
|**Target**|Optionaler **String**-Parameter.<br /><br /> Gibt den Ort an, an dem eine Umgebungsvariable gespeichert wird. Geben Sie „User“ oder „Machine“ an.<br /><br /> Weitere Informationen finden Sie unter [EnvironmentVariableTarget-Enumeration](https://msdn.microsoft.com/library/system.environmentvariabletarget(v=vs.110).aspx) auf der MSDN-Website.|  
|**Wert**|Optionaler **String**-Parameter.<br /><br /> Der Wert, der der Umgebungsvariablen zugewiesen ist, die durch den Parameter **Name** angegeben wird. Die Variable wird gelöscht wenn **Value** leer und die Variable vorhanden ist. Wenn die Variable vorhanden ist, tritt kein Fehler auf, obwohl der Vorgang nicht ausgeführt werden kann.<br /><br /> Weitere Informationen finden Sie unter [Environment::SetEnvironmentVariable-Methode](https://msdn.microsoft.com/library/96xafkes(v=vs.110).aspx) auf der MSDN-Website.|  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)