---
title: /Run („devenv.exe“) | Microsoft-Dokumentation
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
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 98ec2d8be12b8d0dbf9f3283b31c62d90d55e7b4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523044"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [-Run (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/run-devenv-exe).  
  
  
Kompiliert das angegebene Projekt oder die angegebene Projektmappe und führt sie aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
devenv {/run|/r} {SolutionName|ProjectName}  
```  
  
## <a name="arguments"></a>Argumente  
 `SolutionName`  
 Erforderlich. Der vollständige Pfad und Name einer Projektmappendatei  
  
 `ProjectName`  
 Erforderlich. Der vollständige Pfad und Name einer Projektdatei  
  
## <a name="remarks"></a>Hinweise  
 Kompiliert das angegebene Projekt oder die angegebene Projektmappe entsprechend den Einstellungen, die für die aktive Projektmappenkonfiguration angegeben wurde, und führt sie aus. Dieser Schalter startet die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) und lässt sie aktiviert, nachdem die Ausführung des Projekts oder der Projektmappe beendet wurde.  
  
-   Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelten Anführungszeichen ein.  
  
-   Zusammenfassende Informationen inklusive Fehlermeldungen können im Fenster **Befehl** oder durch den `/out`-Schalter in einer Protokolldatei angezeigt werden.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird die Projektmappe `MySolution` mithilfe der aktiven Bereitstellungskonfiguration ausgeführt.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [/Runexit („devenv.exe“)](../../ide/reference/runexit-devenv-exe.md)   
 [/Build („devenv.exe“)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild („devenv.exe“)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)



