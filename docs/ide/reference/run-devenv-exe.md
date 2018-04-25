---
title: /Run („devenv.exe“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2290215caa401c5cc4a639874b0b2bd7012b2cd5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
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