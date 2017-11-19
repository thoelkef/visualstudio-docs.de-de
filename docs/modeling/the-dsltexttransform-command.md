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
ms.openlocfilehash: fd45a33b421e889b05fd78eceddc0b05126e4a21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
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