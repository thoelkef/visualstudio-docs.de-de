---
title: "-Out („devenv.exe“) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 52e3714249ceabd79a490a084fe44d4d1a69fcf4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
Gibt eine Datei an, die Fehler speichern und anzeigen soll, wenn Sie eine Projektmappe ausführen, erstellen, erneut erstellen oder bereitstellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
devenv /out FileName  
```  
  
## <a name="arguments"></a>Argumente  
 `FileName`  
 Erforderlich. Der Pfad und der Name der Datei, die beim Erstellen einer ausführbaren Datei Fehler empfangen soll.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein nicht vorhandener Dateiname angegeben wird, wird die Datei automatisch erstellt. Wenn die Datei bereits vorhanden ist, werden die Ergebnisse an die vorhandenen Inhalte der Datei angefügt.  
  
 Buildfehler in der Befehlszeile werden im **Befehlsfenster** und der Solution Builder-Ansicht des **Ausgabefensters** angezeigt. Diese Option erweist sich als nützlich, wenn Sie unbeaufsichtigte Builds ausführen und die Ergebnisse benötigen.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird `MySolution` ausgeführt, und es werden Fehler in die `MyErrorLog.txt`-Datei geschrieben.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [/Run („devenv.exe“)](../../ide/reference/run-devenv-exe.md)   
 [/Build („devenv.exe“)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild („devenv.exe“)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)