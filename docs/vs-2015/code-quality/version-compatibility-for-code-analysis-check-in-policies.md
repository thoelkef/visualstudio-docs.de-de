---
title: Versions Kompatibilität für Eincheck Richtlinien für die Code Analyse | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 075981569cbee05e90afe17b3afc9558d7bbb270
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609321"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Versionskompatibilität für die Eincheckrichtlinien der Codeanalyse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie die Eincheck Richtlinien für die Code Analyse mithilfe verschiedener Versionen von [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] evaluieren und verfassen müssen, müssen Sie die Unterschiede in der Art und Weise kennen, wie [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] und [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] Eincheck Richtlinien auswerten.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Versions Kompatibilität für das Auswerten von Eincheck Richtlinien

- Wenn die Eincheck Richtlinien für die Code Analyse in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] ausgewertet werden, werden alle Regeln ignoriert, die in [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] vorhanden waren, jedoch nicht in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] vorhanden sind.

- Wenn die Eincheck Richtlinien für die Code Analyse in [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] ausgewertet werden, werden alle neuen Regeln ignoriert, die für [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] exklusiv sind.

- Wenn die Eincheck Richtlinie für die Code Analyse Regelassemblys angibt, ignoriert [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] alle Regeln, die von nicht erkannten Assemblys angegeben werden.

- Wenn die Eincheck Richtlinie für die Code Analyse Regeln für Regelassemblys angibt, die [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] nicht erkennt, wird eine Meldung angezeigt.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Versions Kompatibilität für die Erstellung von Eincheck Richtlinien

- Wenn Sie eine Eincheck Richtlinie für die Code Analyse mithilfe der [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] Version von [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] erstellt haben, können Sie die [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] Version von [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] nicht verwenden, um Sie zu ändern. Außerdem [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] die Richtlinie nicht auswerten können.

- Wenn Sie eine Eincheck Richtlinie für die Code Analyse mithilfe [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] in [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] erstellt haben, können Sie [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] verwenden, um Sie zu ändern, und die Richtlinie kann auch von [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] ausgewertet werden. Nachdem Sie die Richtlinie mithilfe von [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] geändert haben, können Sie die Richtlinie nicht mehr mithilfe [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] in [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] bearbeiten. [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] können die Richtlinien ohne Probleme mit nicht übereinstimmenden starken Namen auswerten.

- Zum Erstellen einer Eincheck Richtlinie für die Code Analyse mit Regel Einstellungen, die sowohl für [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] als auch für [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] gelten, müssen Sie die Richtlinie in [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] erstellen, alle benötigten Änderungen vornehmen und die Richtlinie speichern. Wenn die Änderungen an Regeln nur in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] vorhanden sind, ändern und speichern Sie die Richtlinie in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)].

     Nachdem Sie die Richtlinie in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] gespeichert haben, können Sie die Einstellungen für Regeln, die nur in [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] vorhanden sind, nicht mehr ändern.
