---
title: Der DslTextTransform-Befehl
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32c01401eda8fb1bbe2bdcfc2950a51b968e98b7
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114913"
---
# <a name="the-dsltexttransform-command"></a>Der DslTextTransform-Befehl
Dsltexttransform. cmd ist ein Skript, das "textTransform. exe" aufruft und mit allgemeinen Optionen ausführt. Sie können dsltexttransformation. cmd verwenden, um einen nächtlichen Build ihrer [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Projekte zu automatisieren. Weitere Informationen finden Sie unter [Erstellen von Dateien mit dem textTransform-Hilfsprogramm](../modeling/generating-files-with-the-texttransform-utility.md).

 Die Datei "dsltexttransform. cmd" befindet sich im folgenden Verzeichnis:

 **\<Visual Studio SDK-Installationspfad > \visualstudiointegration\tools\bin**

 Sie können die folgenden Argumente als Eingabe für "dsltexttransform. cmd" angeben:

- Das Ausgabeverzeichnis des Domänen Modellprojekts.

- Das Ausgabeverzeichnis des Designer Definitions Projekts.

- Der Speicherort der Textvorlagen Datei.

  Dsltexttransform. cmd verarbeitet die angegebene Textvorlagen Datei mithilfe der Standard direktivenprozessoren und-Assemblys. Wenn Sie benutzerdefinierte direktivenprozessoren erstellen, können Sie eine eigene Batchdatei erstellen, die "textTransform. exe" aufruft. In dieser Batchdatei können Sie die Assemblys und die zugeordneten benutzerdefinierten direktivenprozessoren angeben.
