---
title: 'Vorgehensweise: Erzwingen von wart barem Code mit einer Eincheck Richtlinie für die Code Analyse | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0d54ca9a31e8a1bbd2496bf8689a119e53580c79
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660219"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Gewusst wie: Erzwingen von wartbarem Code mit einer Eincheckrichtlinie für die Codeanalyse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Entwickler können das Tool Codemetriken verwenden, um die Komplexität und Verwaltbarkeit Ihres Codes zu messen, aber Sie können keine Codemetriken als Teil einer Eincheck Richtlinie aufrufen. Ein Team kann jedoch Code Analyse Regeln aktivieren, mit denen die Kompatibilität Ihres Codes mit Codemetrikstandards überprüft und die Regeln mithilfe von Check-in-Richtlinien erzwungen werden. Weitere Informationen zu Codemetriken finden Sie in den [Code Metrikwerten](../code-quality/code-metrics-values.md).

 Entwickler können die Tiefe von Vererbung, Klassen Kopplung, verwaltbarkeitsindex und Komplexitäts Regeln aktivieren, um verwaltbaren Code durch Eincheck Richtlinien für die Code Analyse zu erzwingen. Alle vier dieser Regeln finden Sie unter der Kategorie "wart barkeits Regeln" im Code Analyse Richtlinien-Editor.

 Administratoren der Versionskontrolle für [!INCLUDE[esprfound](../includes/esprfound-md.md)] können den Check-in-Richtlinien Anforderungen die wart barkeits Regeln für die Code Analyse hinzufügen. Diese Eincheck Richtlinien erfordern, dass Entwickler die Code Analyse auf der Grundlage dieser Regeländerungen ausführen, bevor Sie einen Eincheck Vorgang einleiten.

### <a name="to-open-the-code-analysis-policy-editor"></a>So öffnen Sie den Code Analyse Richtlinien-Editor

1. Klicken Sie in **Team Explorer**mit der rechten Maustaste auf das Teamprojekt, klicken Sie auf **Teamprojekt Einstellungen**und dann auf **Quell**Code Verwaltung.

     Das Dialogfeld **Quell** Code Verwaltung wird angezeigt.

2. Klicken Sie auf der Registerkarte **Check-in-Richtlinie** auf **Hinzufügen**.

     Das Dialogfeld " **Eincheck Richtlinie hinzufügen** " wird angezeigt.

3. Aktivieren Sie in der Liste **Eincheck Richtlinie** das Kontrollkästchen **Code Analyse** , und klicken Sie dann auf **OK**.

     Das Dialogfeld Editor für die **Code Analyse Richtlinie** wird angezeigt.

### <a name="to-enable-code-analysis-maintainability-rules"></a>So aktivieren Sie die wart barkeits Regeln für die Code Analyse

1. Erweitern Sie im Dialogfeld Editor für die **Code Analyse Richtlinien** unter **Regel Einstellungen**den Knoten **wart barkeits Regeln** .

2. Aktivieren Sie die Kontrollkästchen für die folgenden Regeln:

    - Vererbungs Tiefe: **CA1501 avoidexcessiveinvererance** -Threshold: Warnung auf mehr als 5 Ebenen tief

    - Komplexität: **CA1502 avoidexcessivekomplexitäts** Schwellenwert: Warnung bei mehr als 25

    - Wart barkeits Index: **CA1505 vermeidunwart ablecode** -Threshold: Warnung bei weniger als 20

    - Klassen Kopplung: **CA1506 AvoidExcessiveClassCoupling** -Threshold: Warnung bei mehr als 80 für eine Klasse und mehr als 30 für eine Methode

    - Wenn Sie einen Buildvorgang verhindern möchten, aktivieren Sie außerdem das Kontrollkästchen **Warnung als Fehler behandeln** neben der Regel Beschreibung.

3. Klicken Sie auf **OK**. Die neue Eincheck Richtlinie gilt jetzt für künftige Eincheck Vorgänge.

## <a name="see-also"></a>Siehe auch
 [Codemetriewerte](../code-quality/code-metrics-values.md) zum [Erstellen und Verwenden von Eincheck Richtlinien für die Code Analyse](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
