---
title: Der DslTextTransform-Befehl
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 97ddf1fb9dd9e59c2d00f3733069a5cdb14553bf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037901"
---
# <a name="the-dsltexttransform-command"></a>Der DslTextTransform-Befehl
DslTextTransform.cmd ist es sich um ein Skript, das Aufrufe TextTransform.exe mit allgemeinen Optionen ausführt. Können Sie DslTextTransformation.cmd einen nächtlichen Buildvorgang von Automatisieren Ihrer [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Projekte. Weitere Informationen finden Sie unter [Generieren von Dateien mit dem TextTransform-Hilfsprogramm](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform.cmd befindet sich im folgenden Verzeichnis:

 **\<Visual Studio SDK-Installationspfad > \VisualStudioIntegration\Tools\Bin**

 Sie können die folgenden Argumente als Eingabe für DslTextTransform.cmd angeben:

- Das Ausgabeverzeichnis des modellprojekts Domäne.

- Das Ausgabeverzeichnis des Projekts Designer Definition.

- Der Speicherort der Textvorlagendatei.

  DslTextTransform.cmd verarbeitet die angegebene Vorlage Textdatei mit dem Standard-anweisungsprozessoren und Assemblys. Wenn Sie benutzerdefinierte anweisungsprozessoren erstellen, können Sie Ihre eigenen Batch-Datei erstellen, die TextTransform.exe aufruft. In dieser Batchdatei können Sie Ihre Assemblys und die zugeordnete benutzerdefinierten anweisungsprozessoren angeben.