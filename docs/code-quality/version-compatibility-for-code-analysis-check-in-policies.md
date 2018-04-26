---
title: Versionskompatibilität für die Eincheckrichtlinien der Codeanalyse
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 01a8a0c4e859e6f03ba55176d535b0b4e7e6a1b0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Versionskompatibilität für die Eincheckrichtlinien der Codeanalyse
Wenn Sie auswerten und erstellen Einchecken Codeanalyserichtlinien mit verschiedenen Versionen des müssen [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], benötigen Sie die Unterschiede bei der Art [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] und [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] Eincheckrichtlinien auswerten.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Versionskompatibilität für die Bewertung von Eincheckrichtlinien

-   Bei der Auswertung von Eincheckrichtlinien für die Analyse in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], alle Regeln, die im befanden, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] aber nicht vorhanden [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] werden ignoriert.

-   Bei der Auswertung von Eincheckrichtlinien für die Analyse in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], alle neue Regeln, die exklusiv zugewiesen sind [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] werden ignoriert.

-   Wenn die Eincheckrichtlinie für die Analyse Regelassemblys, gibt [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignoriert alle Regeln, die von Assemblys angegeben sind, dass er nicht erkennt.

-   Wenn die Eincheckrichtlinie für die Analyse Regelassemblys angibt, die [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] nicht erkennt, wird eine Meldung angezeigt.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Versionskompatibilität für die Erstellung von Eincheckrichtlinien

-   Wenn Sie mit einer Eincheckrichtlinie für die Analyse erstellt die [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] Version des [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], können Sie keine der [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] Version von [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] , diese zu ändern. Aber auch [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] die Richtlinie kann nicht ausgewertet werden.

-   Wenn Sie mit einer Eincheckrichtlinie für die Analyse erstellt [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], können Sie [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] zu ändern, und die Richtlinie können auch von ausgewertet werden [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. Nach dem Ändern der Richtlinie mit [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], die Richtlinie kann nicht mehr bearbeitet werden, mithilfe von [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] Richtlinien ohne Probleme mit starken Namen können ausgewertet werden.

-   So erstellen Sie eine Eincheckrichtlinie für die Analyse mit regeleinstellungen, die gelten für beide [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] und [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], müssen Sie die Richtlinie in erstellen [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], alle erforderlichen Änderungen vornehmen und speichern Sie die Richtlinie. Wenn die Änderungen an Regeln, nur in vorhanden [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], ändern und speichern Sie die Richtlinie in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].

     Nach dem Speichern der Richtlinie in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], Sie können Einstellungen für Regeln, die in nicht mehr ändern [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] nur.