---
title: "/Runexit („devenv.exe“) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 039c797fd5ea56a5dd1cff834764b9d905854b56
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
Kompiliert das angegebene Projekt oder die angegebene Projektmappe, führt diese aus und schließt die Integrierte Entwicklungsumgebung (Integrated Development Environment; IDE)  
  
## <a name="syntax"></a>Syntax  
  
```  
devenv /runexit {SolutionName|ProjectName}  
```  
  
## <a name="arguments"></a>Argumente  
 `SolutionName`  
 Erforderlich. Der vollständige Pfad und Name einer Projektmappendatei  
  
 `ProjectName`  
 Erforderlich. Der vollständige Pfad und Name einer Projektdatei  
  
## <a name="remarks"></a>Hinweise  
 Kompiliert das angegebene Projekt oder die angegebene Projektmappe entsprechend den Einstellungen, die für die aktive Projektmappenkonfiguration angegeben wurde, und führt sie aus. Dieser Schalter minimiert die Integrierte Entwicklungsumgebung während das Projekt oder die Projektmappe ausgeführt wird und schließt die Entwicklungsumgebung, wenn die Ausführung abgeschlossen ist.  
  
-   Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelten Anführungszeichen ein.  
  
-   Zusammenfassende Informationen inklusive Fehlermeldungen können im Fenster **Befehl** oder durch den `/out`-Schalter in einer Protokolldatei angezeigt werden.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird die Projektmappe mit der aktiven Bereitstellungskonfiguration `MySolution` in einer minimierten integrierten Entwicklungsumgebung ausgeführt. Diese wird anschließend geschlossen.  
  
```  
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [/Run („devenv.exe“)](../../ide/reference/run-devenv-exe.md)   
 [/Build („devenv.exe“)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild („devenv.exe“)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)