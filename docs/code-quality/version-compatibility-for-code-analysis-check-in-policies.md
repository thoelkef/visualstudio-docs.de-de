---
title: "Versionskompatibilit&#228;t f&#252;r die Eincheckrichtlinien der Codeanalyse | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Eincheckrichtlinien, Versionskompatibilität für die Codeanalyse"
  - "Versionskompatibilität, Eincheckrichtlinie für die Codeanalyse"
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# Versionskompatibilit&#228;t f&#252;r die Eincheckrichtlinien der Codeanalyse
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie Eincheckrichtlinien für die Codeanalyse mit verschiedenen Versionen von [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] erstellen und auswerten müssen, ist es erforderlich, die Unterschiede bei der Auswertung von Eincheckrichtlinien mit [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] und mit [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] zu kennen.  
  
## Versionskompatibilität für die Auswertung von Eincheckrichtlinien  
  
-   Bei der Auswertung von Eincheckrichtlinien für die Codeanalyse in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] werden alle Regeln, die in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] vorhanden waren, in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] jedoch nicht vorhanden sind, ignoriert.  
  
-   Bei der Auswertung von Eincheckrichtlinien für die Codeanalyse in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] werden alle neuen Regeln, die nur in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] vorhanden sind, ignoriert.  
  
-   Wenn die Eincheckrichtlinie für die Codeanalyse Regelassemblys angibt, ignoriert [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] alle mit Assemblys angegebenen Regeln, die vom Programm nicht erkannt werden.  
  
-   Wenn die Eincheckrichtlinie für die Codeanalyse Regelassemblys angibt, die von [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] nicht erkannt werden, wird eine entsprechende Meldung angezeigt.  
  
## Versionskompatibilität für die Erstellung von Eincheckrichtlinien  
  
-   Eincheckrichtlinien für die Codeanalyse, die mit der [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]\-Version von [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] erstellt wurden, können mit der [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]\-Version von [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] nicht geändert werden.  Außerdem kann die Richtlinie von [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] nicht ausgewertet werden.  
  
-   Wenn Sie eine Eincheckrichtlinie für die Codeanalyse mit [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] erstellt haben, können Sie [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] verwenden, um diese zu ändern. Die Auswertung der Richtlinie kann ebenfalls mit [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] erfolgen.  Nach dem Speichern der Richtlinie ändern, indem Sie [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)][!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] verwenden, können Sie diese nicht mehr bearbeiten, indem Sie [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] verwenden.  [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] kann die Richtlinien ohne Probleme mit nicht übereinstimmende starken Namen ausgewertet werden.  
  
-   Um eine Eincheckrichtlinie für die Codeanalyse mit Regeleinstellungen zu erstellen, die sowohl für [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] als auch für [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] gelten, müssen Sie die Richtlinie in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] erstellen, alle erforderlichen Änderungen vornehmen und die Richtlinie speichern.  Wenn die Regeländerungen nur in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] vorhanden sind, ändern und speichern Sie die Richtlinie in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].  
  
     Nach dem Speichern der Richtlinie in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] können Regeleinstellungen, die nur in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] vorhanden sind, nicht mehr geändert werden.