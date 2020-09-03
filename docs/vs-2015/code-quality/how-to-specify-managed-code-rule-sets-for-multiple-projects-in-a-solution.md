---
title: 'Gewusst wie: Angeben von Regelsätzen für verwalteten Code für mehrere Projekte in einer Projekt Mappe | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e5333f6133dd3fd56077c14d6e56cd6fdada4404
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656424"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Gewusst wie: Angeben von Regelsätzen für verwalteten Code für mehrere Projekte in einer Projektmappe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Standardmäßig wird allen verwalteten Projekten einer Projekt Mappe der Code Analyse- *Regelsatz*der empfohlenen Microsoft-Regeln zugewiesen. Sie können die Regelsätze ändern, die den Projekten einer Projektmappe im Eigenschaftendialogfeld für die Projektmappe zugewiesen werden.

> [!NOTE]
> Standardmäßig wird die Projektcodeanalyse nicht als Buildschritt ausgeführt. Informationen zum Aktivieren der Code Analyse als Buildschritt finden Sie unter Gewusst [wie: Konfigurieren der Code Analyse für ein Projekt mit verwaltetem Code](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>So geben Sie einen Regelsatz für mehrere Projekte in einer Projektmappe mit verwaltetem Code an

1. In [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], oder [!INCLUDE[vsPro](../includes/vspro-md.md)] Öffnen Sie die Projekt Mappe.

2. Klicken Sie im Menü **analysieren** auf **Code Analyse für**Projekt Mappe konfigurieren.

3. Erweitern Sie ggf. **Allgemeine Eigenschaften**, und klicken Sie dann auf **Code Analyse Einstellungen**.

4. Sie können einen Regelsatz für ein oder mehrere Projekte angeben.

    - Klicken Sie auf den Projektnamen, um einen Regelsatz für ein einzelnes Projekt anzugeben.

    - Halten Sie die STRG-TASTE gedrückt, und klicken Sie auf die Projektnamen, um einen Regelsatz für mehrere Projekte anzugeben.

    - Halten Sie die UMSCHALTTASTE gedrückt, und klicken Sie in die Projektliste, um alle Projekte in der Projektmappe anzugeben.

5. Klicken Sie auf das Feld **Regelsatz** eines Projekts, und klicken Sie dann auf den Namen des Regelsatzes, den Sie anwenden möchten.
