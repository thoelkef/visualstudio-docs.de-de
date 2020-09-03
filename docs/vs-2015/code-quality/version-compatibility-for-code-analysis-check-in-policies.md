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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609321"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Versionskompatibilität für die Eincheckrichtlinien der Codeanalyse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Eincheck Richtlinien für die Code Analyse mithilfe verschiedener Versionen von auswerten und verfassen müssen [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] , müssen Sie die Unterschiede in der Art und Weise der [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] Auswertung von [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] Eincheck Richtlinien kennen.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Versions Kompatibilität für das Auswerten von Eincheck Richtlinien

- Wenn Eincheck Richtlinien für die Code Analyse in ausgewertet werden [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , werden alle Regeln ignoriert, die in vorhanden sind, [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] jedoch nicht in vorhanden [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] sind.

- Wenn Eincheck Richtlinien für die Code Analyse in ausgewertet werden [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , werden alle neuen Regeln, die exklusiv für sind, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] ignoriert.

- Wenn die Eincheck Richtlinie für die Code Analyse Regelassemblys angibt, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] ignoriert alle Regeln, die von den nicht erkannten Assemblys angegeben werden.

- Wenn die Eincheck Richtlinie für die Code Analyse Regelassemblys angibt, die von [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] nicht erkannt werden, wird eine Meldung angezeigt.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Versions Kompatibilität für die Erstellung von Eincheck Richtlinien

- Wenn Sie eine Eincheck Richtlinie für die Code Analyse mithilfe der- [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] Version von erstellt [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] haben, können Sie Sie nicht mit der- [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] Version von [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] ändern. Außerdem [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] kann die Richtlinie nicht auswerten.

- Wenn Sie eine Eincheck Richtlinie für die Code Analyse mithilfe von [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] in erstellt [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] haben, können Sie Sie in verwenden, [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] um Sie zu ändern, und die Richtlinie kann auch von ausgewertet werden [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] . Nachdem Sie die Richtlinie mithilfe von [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] in geändert [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] haben, können Sie die Richtlinie nicht mehr mithilfe von [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] in bearbeiten [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] . [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] kann die Richtlinien ohne Probleme mit nicht übereinstimmenden starken Namen auswerten.

- Zum Erstellen einer Eincheck Richtlinie für die Code Analyse mit Regel Einstellungen, die sowohl für [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] als auch gelten [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , müssen Sie die Richtlinie in Erstellen [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , alle benötigten Änderungen vornehmen und die Richtlinie speichern. Wenn die Änderungen an Regeln nur in vorhanden [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] sind, ändern und speichern Sie die Richtlinie in [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] .

     Nachdem Sie die Richtlinie in gespeichert [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] haben, können Sie die Einstellungen für Regeln, die nur in vorhanden sind, nicht mehr ändern [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] .
