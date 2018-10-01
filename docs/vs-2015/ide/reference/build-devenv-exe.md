---
title: /Build („devenv.exe“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- builds [Team System], command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d04b927232936e3c1abc82c0334f4c3486457088
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522542"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [-Build (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/build-devenv-exe).  
  
  
Erstellt mithilfe einer angegebenen Konfigurationsdatei eine Projektmappe  
  
## <a name="syntax"></a>Syntax  
  
```  
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]  
```  
  
## <a name="arguments"></a>Argumente  
 `SolutionName`  
 Erforderlich. Der vollständige Pfad und Name der Projektmappendatei  
  
 `SolnConfigName`  
 Erforderlich. Der Name der Projektmappenkonfiguration, die für das Erstellen der Projektmappe verwendet wird, die in `SolutionName` benannt wurde  
  
 /project `ProjName`  
 Dies ist optional. Der Pfad und der Name einer Projektdatei innerhalb der Projektmappe. Sie können einen relativen Pfad vom `SolutionName`-Ordner zur Projektdatei, dem Anzeigenamen des Projekts oder dem vollständigen Pfad und Namen der Projektdatei eingeben.  
  
 /projectconfig `ProjConfigName`  
 Dies ist optional. Der Name der Projektbuildkonfiguration für die Erstellung des benannten `/project`.  
  
## <a name="remarks"></a>Hinweise  
 Dieser Schalter führt dieselbe Funktion aus wie der Menübefehl **Projektmappe erstellen** in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE).  
  
 Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelte Anführungszeichen ein.  
  
 Zusammenfassende Informationen für Builds, inklusive Fehlermeldungen, können im Fenster **Befehl** oder in einer Protokolldatei, die durch den Schalter `/out` angegeben wird, angezeigt werden.  
  
 Dieser Befehl erstellt nur Projekte, die seit dem letzten Build geändert wurden. Um alle Projekte in einer Projektmappe zu erstellen, verwenden Sie [/Rebuild („devenv.exe“)](../../ide/reference/rebuild-devenv-exe.md).  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird das Projekt `CSharpConsoleApp` mithilfe der `Debug`-Projektbuildkonfiguration in der `Debug`-Projektmappenkonfiguration von `MySolution` erstellt.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [/Rebuild („devenv.exe“)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Clean („devenv.exe“)](../../ide/reference/clean-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)



