---
title: Der DslTextTransform-Befehl
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8c1be8b041fcf5f4eb70b37a53b7c32705f6cfcf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876619"
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