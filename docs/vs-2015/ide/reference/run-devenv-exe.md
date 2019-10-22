---
title: /Run („devenv.exe“) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b2716995e8ff3a318262284b5733a471086c68c1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665523"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kompiliert das angegebene Projekt oder die angegebene Projektmappe und führt sie aus.

## <a name="syntax"></a>Syntax

```
devenv {/run|/r} {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argumente
 `SolutionName` ist erforderlich. Der vollständige Pfad und Name einer Projektmappendatei

 `ProjectName` ist erforderlich. Der vollständige Pfad und Name einer Projektdatei

## <a name="remarks"></a>Anmerkungen
 Kompiliert das angegebene Projekt oder die angegebene Projektmappe entsprechend den Einstellungen, die für die aktive Projektmappenkonfiguration angegeben wurde, und führt sie aus. Dieser Schalter startet die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) und lässt sie aktiviert, nachdem die Ausführung des Projekts oder der Projektmappe beendet wurde.

- Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelten Anführungszeichen ein.

- Zusammenfassende Informationen inklusive Fehlermeldungen können im Fenster **Befehl** oder durch den `/out`-Schalter in einer Protokolldatei angezeigt werden.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird die Projektmappe `MySolution` mithilfe der aktiven Bereitstellungskonfiguration ausgeführt.

```
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Siehe auch
 Debug- [Befehls Zeilenschalter](../../ide/reference/devenv-command-line-switches.md) [/runexit ("abvenv. exe")](../../ide/reference/runexit-devenv-exe.md) [/Build (](../../ide/reference/build-devenv-exe.md) "abvenv. exe") [/Rebuild (](../../ide/reference/rebuild-devenv-exe.md) "") [("](../../ide/reference/out-devenv-exe.md) ")
