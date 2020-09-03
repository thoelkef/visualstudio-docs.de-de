---
title: Der dsltexttransform-Befehl | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 599bf14a3d37fbd6bdff111f79e658f44624792b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658465"
---
# <a name="the-dsltexttransform-command"></a>Der DslTextTransform-Befehl
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dsltexttransform. cmd ist ein Skript, das TextTransform.exe aufruft und es mit allgemeinen Optionen ausführt. Sie können dsltexttransformation. cmd verwenden, um einen nächtlichen Build ihrer Projekte zu automatisieren [!INCLUDE[dsl](../includes/dsl-md.md)] . Weitere Informationen finden Sie unter [Erstellen von Dateien mit dem textTransform-Hilfsprogramm](../modeling/generating-files-with-the-texttransform-utility.md).

 Die Datei "dsltexttransform. cmd" befindet sich im folgenden Verzeichnis:

 **\<Visual Studio SDK Installation Path>\Visualstudiointegration\tools\bin**

 Sie können die folgenden Argumente als Eingabe für "dsltexttransform. cmd" angeben:

- Das Ausgabeverzeichnis des Domänen Modellprojekts.

- Das Ausgabeverzeichnis des Designer Definitions Projekts.

- Der Speicherort der Textvorlagen Datei.

  Dsltexttransform. cmd verarbeitet die angegebene Textvorlagen Datei mithilfe der Standard direktivenprozessoren und-Assemblys. Wenn Sie benutzerdefinierte direktivenprozessoren erstellen, können Sie eine eigene Batchdatei erstellen, die TextTransform.exe aufruft. In dieser Batchdatei können Sie die Assemblys und die zugeordneten benutzerdefinierten direktivenprozessoren angeben.
