---
title: 'Vorgehensweise: Konfigurieren der Code Analyse für eine ASP.NET-Webanwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 423264362118343d573b417cd055d2d722df995e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657465"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Gewusst wie: Konfigurieren der Codeanalyse für eine ASP.NET-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] und [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] können Sie eine Liste der Code Analyse- *Regelsätze* auswählen, die auf [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Webanwendung angewendet werden sollen. Der Standard Regelsatz sind die empfohlenen Microsoft Mininimum-Regeln. Sie können einen anderen Regelsatz auswählen, der auf die Website angewendet werden soll.

### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>So konfigurieren Sie einen Regelsatz für ein ASP.NET-Seitenframeworkprojekt

1. Wählen Sie in **Projektmappen-Explorer**die Website aus.

2. Klicken Sie im Menü **analysieren** auf **Code Analyse für Website konfigurieren**.

3. Wenn Sie die Projekt Mappe ausgewählt haben und die Projekt Mappe mehr als ein Projekt enthält, wählen Sie die Buildkonfiguration und das Ziel Betriebssystem aus den Listen **Konfiguration** und **Plattform** aus.

4. Klicken Sie für jedes Projekt in der Projekt Mappe auf die Spalte **Regelsatz** , und klicken Sie dann auf den Namen des Regelsatzes, der ausgeführt werden soll.

5. Standardmäßig wird die Code Analyse für alle Projekte in der Projekt Mappe ausgeführt. Um die Code Analyse für ein bestimmtes Projekt zu deaktivieren oder zu aktivieren, führen Sie die folgenden Schritte aus:

    1. Klicken Sie mit der rechten Maustaste auf den Projektnamen und dann auf Eigenschaften.

    2. Aktivieren oder deaktivieren Sie das Kontrollkästchen **Code Analyse aktivieren** . Sie können die Code Analyse auch manuell ausführen, indem Sie im Menü **analysieren** die Option **Code Analyse auf Website ausführen** auswählen.

6. Führen Sie in der Dropdown Liste **diesen Regelsatz ausführen** die folgenden Schritte aus:

    - Wählen Sie den Regelsatz aus, den Sie verwenden möchten.

    - Wählen Sie **\<Browse >** aus, um einen vorhandenen benutzerdefinierten Regelsatz anzugeben, der nicht in der Liste enthalten ist.

    - Definieren Sie einen benutzerdefinierten Regelsatz. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md).
