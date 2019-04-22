---
title: /Runexit („devenv.exe“) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 412dee9ec920d4d94e2b4f2f176d1b1634a34eef
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59648899"
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
## <a name="remarks"></a>Anmerkungen  
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
