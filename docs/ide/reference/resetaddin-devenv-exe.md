---
title: -ResetAddin (devenv.exe) | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 36b003f4890b16a7b69f7f66f8b0ef83a0ade7ac
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
Entfernt Befehle und die Befehlsbenutzeroberfläche, die dem angegebenen Add-In zugeordnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>Argumente  
 `AddIn`  
 Dies ist optional. Der Befehlsname des Add-Ins.  
  
## <a name="remarks"></a>Hinweise  
 Standardmäßig entspricht der Befehlsname des Add-Ins *\<AddInSolutionName>*.Connect*.\<AddInSolutionName>* und wird in Connect.cs als `commandName`-Parameter der `Exec`-Methode angezeigt. Sie können den Befehlsnamen auch überprüfen, indem Sie den Namen des Add-Ins im Befehlsfenster von Visual Studio eingeben und die Eingabe von IntelliSense vervollständigen lassen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird Visual Studio gestartet. Die Ausführung des Add-Ins `MyAddin` beim Starten wird verhindert.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Personalisieren der Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md)   
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)