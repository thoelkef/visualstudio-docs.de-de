---
title: 'Vorgehensweise: Aktivieren und Deaktivieren der automatischen Code Analyse für verwalteten Code | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 7c22d194-5fea-4f23-b02d-19344fa64a64
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d87cc57b31e63ae7aafa53c335df2b56f86a0409
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658101"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Gewusst wie: Aktivieren und Deaktivieren der automatischen Codeanalyse für verwalteten Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Code Analyse so konfigurieren, dass Sie vor jedem Build eines Projekts mit verwaltetem Code ausgeführt wird. Sie können für jede [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Konfiguration verschiedene Code Analyse Eigenschaften festlegen.

### <a name="to-enable-or-disable-automatic-code-analysis"></a>So aktivieren oder deaktivieren Sie die automatische Code Analyse

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.

2. Klicken Sie im Dialogfeld Eigenschaften für das Projekt auf **Code Analyse**.

3. Geben Sie den Buildtyp in der **Konfiguration** und die Zielplattform in der **Plattform**an.

4. Aktivieren bzw. deaktivieren Sie das Kontrollkästchen **Code Analyse für Build aktivieren (definiert CODE_ANALYSIS Konstante)** , um die automatische Code Analyse zu aktivieren oder zu deaktivieren.
