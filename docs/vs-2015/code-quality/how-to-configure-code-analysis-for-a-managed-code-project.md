---
title: 'Vorgehensweise: Konfigurieren der Code Analyse für ein Projekt mit verwaltetem Code | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1ac04a3d8834e3fc24f148fc36327d101e43720a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658847"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Gewusst wie: Konfigurieren der Codeanalyse für ein Projekt mit verwaltetem Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] können Sie [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] und [!INCLUDE[vsPro](../includes/vspro-md.md)] aus einer Liste von Code Analyse- *Regelsätzen* auswählen, die auf ein Projekt mit verwaltetem Code angewendet werden sollen. Der Standardregelsatz sind die Microsoft-Mindestregeln. Sie können einen anderen Regelsatz auf ein Projekt oder alle Projekte in einer Projektmappe anwenden.

> [!NOTE]
> Informationen zum Konfigurieren eines Regelsatzes für ASP.NET-Webanwendungen finden Sie unter Gewusst [wie: Konfigurieren der Code Analyse für eine ASP.NET-Webanwendung](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).

### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>So konfigurieren Sie einen Regelsatz für ein .NET Framework-Projekt

1. Klicken Sie in **Projektmappen-Explorer**auf das Projekt.

2. Klicken Sie im Menü **analysieren** auf **Code Analyse für** *ProjectName*konfigurieren.

3. Klicken Sie in den Listen **Konfiguration** und **Plattform** auf die Buildkonfiguration und die Zielplattform.

4. Wenn Sie die Code Analyse bei jedem Erstellen des Projekts mithilfe der ausgewählten Konfiguration ausführen möchten, aktivieren Sie das Kontrollkästchen **Code Analyse für Build aktivieren (definiert CODE_ANALYSIS Konstante)** . Sie können die Code Analyse auch manuell ausführen, indem Sie das Menü **analysieren** öffnen und **auf Code Analyse für** *ProjectName*ausführen klicken.

5. Standardmäßig meldet die Codeanalyse keine Warnungen zu Code, der automatisch von Tools von Drittanbietern generiert wird. Um Warnungen aus generiertem Code anzuzeigen, deaktivieren Sie das Kontrollkästchen **Ergebnisse aus generiertem Code unterdrücken** .

    > [!NOTE]
    > Allerdings werden durch diese Option keine Codeanalysefehler und -warnungen zu generiertem Code unterdrückt, wenn die Fehler und Warnungen in Formularen und Vorlagen auftreten. Der Quellcode für ein Formular oder eine Vorlage kann sowohl angezeigt als auch verwaltet werden.

6. Führen Sie in der Liste **diesen Regelsatz ausführen** einen der folgenden Schritte aus:

    - Wählen Sie den Regelsatz, den Sie verwenden möchten.

    - Klicken Sie auf **\<Browse... >** , um einen vorhandenen benutzerdefinierten Regelsatz anzugeben, der nicht in der Liste enthalten ist.

    - Definieren Sie einen benutzerdefinierten Regelsatz.

         Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md).

## <a name="see-also"></a>Siehe auch
 [Exemplarische Vorgehensweise: Konfigurieren und Verwenden eines benutzerdefinierten Regelsatzes](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
