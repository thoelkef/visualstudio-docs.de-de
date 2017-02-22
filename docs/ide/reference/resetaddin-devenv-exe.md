---
title: "/ResetAddin (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "AddIn-Zustand"
  - "Deaktivieren von AddIn"
  - "Zurücksetzen von AddIn"
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Entfernt Befehle und die Befehlsbenutzeroberfläche, die dem angegebenen Add\-In zugeordnet sind.  
  
## Syntax  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## Argumente  
 `AddIn`  
 Optional.  Der Befehlsname des Add\-Ins.  
  
## Hinweise  
 Standardmäßig entspricht der Befehlsname des Add\-Ins *\<Name der Add\-In\-Lösung\>*.Connect*.\<Name der Add\-In\-Lösung\>*, und wird in Connect.cs als `commandName`\-Parameter der `Exec`\-Methode angezeigt.  Sie können den Befehlsnamen auch überprüfen, indem Sie den Namen des Add\-Ins im Befehlsfenster von Visual Studio eingeben und die Eingabe von IntelliSense vervollständigen lassen.  
  
## Beispiel  
 Im folgenden Beispiel wird Visual Studio gestartet und die Ausführung des `MyAddin`\-Add\-Ins beim Start verhindert.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## Siehe auch  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)