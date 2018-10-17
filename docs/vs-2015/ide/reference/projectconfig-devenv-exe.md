---
title: /ProjectConfig („devenv.exe“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 669378e02b2a38fa8b94c23543c6cc0136d8e07e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181637"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Gibt eine Projektbuildkonfiguration an, die beim Erstellen, Bereinigen, Neuerstellen oder Bereitstellen des im `/project`-Argument benannten Projekts angewendet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
```  
  
## <a name="arguments"></a>Argumente  
 /build  
 Erstellt das durch `/project` `ProjName` angegebene Projekt  
  
 /clean  
 Bereinigt alle Zwischendateien und Ausgabeverzeichnisse, die während eines Builds erstellt werden  
  
 /rebuild  
 Bereinigt und erstellt das durch `/project` `ProjName` angegebene Projekt  
  
 /deploy  
 Gibt an, dass das Projekt nach dem Erstellen oder Neuerstellen bereitgestellt werden soll  
  
 `SolnConfigName`  
 Erforderlich. Der Name der Projektmappenkonfiguration, die auf die in `SolutionName` benannte Projektmappe angewendet wird  
  
 `SolutionName`  
 Erforderlich. Der vollständige Pfad und Name der Projektmappendatei  
  
 /project `ProjName`  
 Dies ist optional. Der Pfad und der Name einer Projektdatei innerhalb der Projektmappe. Sie können einen relativen Pfad vom `SolutionName`-Ordner zur Projektdatei, dem Anzeigenamen des Projekts oder dem vollständigen Pfad und Namen der Projektdatei eingeben.  
  
 /projectconfig `ProjConfigName`  
 Dies ist optional. Der Name der Projektbuildkonfiguration für die Anwendung auf das benannte `/project`  
  
## <a name="remarks"></a>Hinweise  
  
-   Muss zusammen mit dem `/project`-Schalter als Teil eines `devenv /build`-, /`clean`-, `/rebuild`- oder `/deploy`-Befehls verwendet werden.  
  
-   Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelten Anführungszeichen ein.  
  
-   Zusammenfassende Informationen für Builds, inklusive Fehlermeldungen, können im Fenster **Befehl** oder in einer Protokolldatei, die durch den Schalter `/out` angegeben wird, angezeigt werden.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird das Projekt `CSharpConsoleApp` mithilfe der `Debug`-Projektbuildkonfiguration in der `Debug`-Projektmappenkonfiguration von `MySolution` erstellt.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>Siehe auch  
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [/Project („devenv.exe“)](../../ide/reference/project-devenv-exe.md)   
 [/Build („devenv.exe“)](../../ide/reference/build-devenv-exe.md)   
 [/Clean („devenv.exe“)](../../ide/reference/clean-devenv-exe.md)   
 [/Rebuild („devenv.exe“)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy („devenv.exe“)](../../ide/reference/deploy-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)



