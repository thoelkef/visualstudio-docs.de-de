---
title: Versionskompatibilität für die Eincheckrichtlinien der Codeanalyse
ms.date: 11/04/2016
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
ms.openlocfilehash: c233d174922c0853d771356e0b68185c51c368ea
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448733"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Versionskompatibilität für die Eincheckrichtlinien der Codeanalyse

Wenn Sie die Eincheck Richtlinien für die Code Analyse mithilfe verschiedener Versionen von [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] evaluieren und verfassen müssen, müssen Sie die Unterschiede in der Art und Weise kennen, wie [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] und [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] Eincheck Richtlinien auswerten.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Versions Kompatibilität für das Auswerten von Eincheck Richtlinien

- Wenn die Eincheck Richtlinien für die Code Analyse in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ausgewertet werden, werden alle Regeln ignoriert, die in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] vorhanden waren, jedoch nicht in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] vorhanden sind.

- Wenn die Eincheck Richtlinien für die Code Analyse in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ausgewertet werden, werden alle neuen Regeln ignoriert, die für [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] exklusiv sind.

- Wenn die Eincheck Richtlinie für die Code Analyse Regelassemblys angibt, ignoriert [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] alle Regeln, die von nicht erkannten Assemblys angegeben werden.

- Wenn die Eincheck Richtlinie für die Code Analyse Regeln für Regelassemblys angibt, die [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] nicht erkennt, wird eine Meldung angezeigt.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Versions Kompatibilität für die Erstellung von Eincheck Richtlinien

- Wenn Sie eine Eincheck Richtlinie für die Code Analyse mithilfe der [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] Version von [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] erstellt haben, können Sie die [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] Version von [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] nicht verwenden, um Sie zu ändern. Außerdem [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] die Richtlinie nicht auswerten können.

- Wenn Sie eine Eincheck Richtlinie für die Code Analyse mithilfe [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] erstellt haben, können Sie [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] verwenden, um Sie zu ändern, und die Richtlinie kann auch von [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ausgewertet werden. Nachdem Sie die Richtlinie mithilfe von [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] geändert haben, können Sie die Richtlinie nicht mehr mithilfe [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] bearbeiten. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] können die Richtlinien ohne Probleme mit nicht übereinstimmenden starken Namen auswerten.

- Zum Erstellen einer Eincheck Richtlinie für die Code Analyse mit Regel Einstellungen, die sowohl für [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] als auch für [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] gelten, müssen Sie die Richtlinie in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] erstellen, alle benötigten Änderungen vornehmen und die Richtlinie speichern. Wenn die Änderungen an Regeln nur in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] vorhanden sind, ändern und speichern Sie die Richtlinie in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].

   Nachdem Sie die Richtlinie in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] gespeichert haben, können Sie die Einstellungen für Regeln, die nur in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] vorhanden sind, nicht mehr ändern.
