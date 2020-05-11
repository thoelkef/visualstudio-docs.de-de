---
title: -RunExit („devenv.exe“)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- RunExit Devenv switch
- Devenv, /RunExit switch
- /RunExit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18ca581c5a8a7f631138e8b3eacff02a031e0931
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593602"
---
# <a name="runexit-devenvexe"></a>/RunExit (devenv.exe)

Kompiliert das angegebene Projekt oder die angegebene Projektmappe, führt diese aus und schließt die Integrierte Entwicklungsumgebung (Integrated Development Environment; IDE)

## <a name="syntax"></a>Syntax

```shell
devenv /RunExit {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Argumente

- *SolutionName*

  Der vollständige Pfad und Name einer Projektmappendatei

- *Projektname*

  Der vollständige Pfad und Name einer Projektdatei

- `/Out` *OutputFilename*

  Dies ist optional. Der Name der Datei, an die die Ausgabe des Tools gesendet werden soll. Wenn die Datei bereits vorhanden ist, fügt das Tool die Ausgabe an das Ende der Datei an.

## <a name="remarks"></a>Bemerkungen

Kompiliert das angegebene Projekt oder die angegebene Projektmappe entsprechend den Einstellungen, die für die aktive Projektmappenkonfiguration angegeben wurde, und führt sie aus. Dieser Schalter minimiert die IDE, während das Projekt oder die Projektmappe ausgeführt wird. Er schließt die IDE, nachdem die Ausführung des Projekts oder der Projektmappe beendet wurde.

- Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelten Anführungszeichen ein.

- Zusammenfassende Informationen inklusive Fehlermeldungen können im Fenster **Befehl** oder durch den `/Out`-Schalter in einer Protokolldatei angezeigt werden.

## <a name="example"></a>Beispiel

In diesem Beispiel wird die Projektmappe mit der aktiven Bereitstellungskonfiguration `MySolution` in einer minimierten integrierten Entwicklungsumgebung ausgeführt. Diese wird anschließend geschlossen.

```
devenv /runexit "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Weitere Informationen

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [/Run („devenv.exe“)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
