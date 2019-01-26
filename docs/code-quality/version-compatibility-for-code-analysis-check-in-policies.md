---
title: Versionskompatibilität für die Eincheckrichtlinien der Codeanalyse
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41de42c02916165d9c0be91c6af5076279e0b4d4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922242"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Versionskompatibilität für die Eincheckrichtlinien der Codeanalyse

Wenn Sie erstellen und Code Analysis Check-in-Richtlinien mit verschiedenen Versionen des auswerten [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], benötigen Sie die Unterschiede bei [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] und [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] Auswerten der Check-in-Richtlinien.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Versionskompatibilität für Ihre Evaluierung von Eincheckrichtlinien

- Bei der Auswertung von Eincheckrichtlinien für die Analyse in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], Regeln, die im vorhanden [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] jedoch nicht vorhanden [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] werden ignoriert.

- Bei der Auswertung von Eincheckrichtlinien für die Analyse in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], alle neuen Regeln, die exklusiv für [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] werden ignoriert.

- Wenn der Eincheckrichtlinie für die Analyse Regelassemblys angibt [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignoriert alle Regeln, die von Assemblys angegeben sind, dass er nicht erkennt.

- Wenn der Eincheckrichtlinie für die Analyse Regelassemblys angibt, die [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] nicht erkennt, wird eine Meldung angezeigt.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Versionskompatibilität für die Erstellung von Eincheckrichtlinien

- Wenn Sie mit einer Eincheckrichtlinie für die Analyse erstellt der [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] Version von [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], kann nicht verwendet werden der [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] Version von [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] ändern. Auch [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] die Richtlinie kann nicht ausgewertet werden.

- Wenn Sie mit einer Eincheckrichtlinie für die Analyse erstellt [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], können Sie [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] so ändern Sie ihn, und die Richtlinie auch von ausgewertet werden können [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. Nach dem Ändern der Richtlinie mithilfe von [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], Sie können die Richtlinie nicht mehr bearbeiten, mit [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] die Richtlinien ohne Probleme bei den starken Namen können ausgewertet werden.

- Eincheckrichtlinie für die Analyse mit Regel zu erstellen, die für beide gelten [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] und [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], müssen Sie die Richtlinie in erstellen [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], die erforderlichen Änderungen vornehmen und speichern Sie die Richtlinie. Wenn die Änderungen an Regeln, nur in vorhanden [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], Sie ändern und speichern Sie die Richtlinie in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].

   Nach dem Speichern der Richtlinie in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], ändern Sie nicht mehr Einstellungen für Regeln, die im vorhanden [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] nur.