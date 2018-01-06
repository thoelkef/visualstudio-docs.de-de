---
title: Der DslTextTransform-Befehl | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: "30"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 4b8c7040cabf05b30920654996891bc8d19f42db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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