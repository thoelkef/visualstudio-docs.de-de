---
title: Der DslTextTransform-Befehl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 11fb12f3716fe9f8b5fee13a7eecd88ee107ff45
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="the-dsltexttransform-command"></a>Der DslTextTransform-Befehl
DslTextTransform.cmd ist ein Skript, das TextTransform.exe aufruft und mit allgemeinen Optionen ausgeführt. Können Sie DslTextTransformation.cmd einen nächtlichen Buildvorgang der Automatisieren Ihrer [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Projekte. Weitere Informationen finden Sie unter [Generieren von Dateien mit dem TextTransform-Hilfsprogramm](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd befindet sich im folgenden Verzeichnis:  
  
 **\<Visual Studio SDK-Installationspfad > \VisualStudioIntegration\Tools\Bin**  
  
 Sie können die folgenden Argumente als Eingabe für DslTextTransform.cmd angeben:  
  
-   Das Ausgabeverzeichnis des Projekts Modell Domäne.  
  
-   Das Ausgabeverzeichnis des Projekts Definition des Designers.  
  
-   Der Speicherort der Textvorlagendatei.  
  
 DslTextTransform.cmd verarbeitet die angegebene Textvorlagendatei mit dem Standard-Direktivenprozessoren und Assemblys. Wenn Sie benutzerdefinierte Direktivenprozessoren erstellt haben, können Sie eigene Batchdatei erstellen, die TextTransform.exe aufruft. In dieser Batchdatei können Sie die Assemblys und die zugeordnete benutzerdefinierten Direktivenprozessoren angeben.