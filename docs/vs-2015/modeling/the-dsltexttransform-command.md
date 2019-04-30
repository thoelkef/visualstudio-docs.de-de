---
title: Der DslTextTransform-Befehl | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 220ceab29cb2b9bc1b117a98326d22c3c546a162
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548497"
---
# <a name="the-dsltexttransform-command"></a>Der DslTextTransform-Befehl
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform.cmd ist es sich um ein Skript, das Aufrufe TextTransform.exe mit allgemeinen Optionen ausführt. Können Sie DslTextTransformation.cmd einen nächtlichen Buildvorgang von Automatisieren Ihrer [!INCLUDE[dsl](../includes/dsl-md.md)] Projekte. Weitere Informationen finden Sie unter [Generieren von Dateien mit dem TextTransform-Hilfsprogramm](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd befindet sich im folgenden Verzeichnis:  
  
 **\<Visual Studio SDK-Installationspfad > \VisualStudioIntegration\Tools\Bin**  
  
 Sie können die folgenden Argumente als Eingabe für DslTextTransform.cmd angeben:  
  
- Das Ausgabeverzeichnis des modellprojekts Domäne.  
  
- Das Ausgabeverzeichnis des Projekts Designer Definition.  
  
- Der Speicherort der Textvorlagendatei.  
  
  DslTextTransform.cmd verarbeitet die angegebene Vorlage Textdatei mit dem Standard-anweisungsprozessoren und Assemblys. Wenn Sie benutzerdefinierte anweisungsprozessoren erstellen, können Sie Ihre eigenen Batch-Datei erstellen, die TextTransform.exe aufruft. In dieser Batchdatei können Sie Ihre Assemblys und die zugeordnete benutzerdefinierten anweisungsprozessoren angeben.
