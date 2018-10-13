---
title: SetEnv-Aufgabe| Microsoft-Dokumentation
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
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c15f0be4498c3ff3014c273d31657851c9e65b8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205666"
---
# <a name="setenv-task"></a>SetEnv-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
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



