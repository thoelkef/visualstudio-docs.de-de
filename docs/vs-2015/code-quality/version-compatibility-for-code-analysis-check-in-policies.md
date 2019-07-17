---
title: Versionskompatibilität für die Eincheckrichtlinien für die Analyse | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0a63ead03baffaa0ce8047220ff1ce8a33c88be8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201172"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Versionskompatibilität für die Eincheckrichtlinien der Codeanalyse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie erstellen und Code Analysis Check-in-Richtlinien mit verschiedenen Versionen des auswerten [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], benötigen Sie die Unterschiede bei [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] und [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] Auswerten der Check-in-Richtlinien.  
  
## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Versionskompatibilität für Ihre Evaluierung von Eincheckrichtlinien  
  
- Bei der Auswertung von Eincheckrichtlinien für die Analyse in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], Regeln, die im vorhanden [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] jedoch nicht vorhanden [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] werden ignoriert.  
  
- Bei der Auswertung von Eincheckrichtlinien für die Analyse in [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], alle neuen Regeln, die exklusiv für [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] werden ignoriert.  
  
- Wenn der Eincheckrichtlinie für die Analyse Regelassemblys angibt [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] ignoriert alle Regeln, die von Assemblys angegeben sind, dass er nicht erkennt.  
  
- Wenn der Eincheckrichtlinie für die Analyse Regelassemblys angibt, die [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] nicht erkennt, wird eine Meldung angezeigt.  
  
## <a name="version-compatibility-for-authoring-check-in-policies"></a>Versionskompatibilität für die Erstellung von Eincheckrichtlinien  
  
- Wenn Sie mit einer Eincheckrichtlinie für die Analyse erstellt der [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] Version von [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], kann nicht verwendet werden der [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] Version von [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] ändern. Auch [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] die Richtlinie kann nicht ausgewertet werden.  
  
- Wenn Sie mit einer Eincheckrichtlinie für die Analyse erstellt [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] in [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], können Sie [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] so ändern Sie ihn, und die Richtlinie auch von ausgewertet werden können [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]. Nach dem Ändern der Richtlinie mithilfe von [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], Sie können die Richtlinie nicht mehr bearbeiten, mit [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] in [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]. [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] die Richtlinien ohne Probleme bei den starken Namen können ausgewertet werden.  
  
- Eincheckrichtlinie für die Analyse mit Regel zu erstellen, die für beide gelten [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] und [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], müssen Sie die Richtlinie in erstellen [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], die erforderlichen Änderungen vornehmen und speichern Sie die Richtlinie. Wenn die Änderungen an Regeln, nur in vorhanden [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], Sie ändern und speichern Sie die Richtlinie in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)].  
  
     Nach dem Speichern der Richtlinie in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], ändern Sie nicht mehr Einstellungen für Regeln, die im vorhanden [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] nur.
