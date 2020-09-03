---
title: 'Vorgehensweise: Erstellen oder Aktualisieren von Standard mäßigen Eincheck Richtlinien für die Code Analyse | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5e8016032a0ea8d1b8c62b2dfc2bbdf72251590c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661775"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Gewusst wie: Erstellen oder Aktualisieren von Standardeincheckrichtlinien für die Codeanalyse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe der Eincheck Richtlinie für die Code Analyse können Sie festlegen, dass die Code Analyse für alle Code Projekte in einem Teamprojekt ausgeführt werden soll. Wenn Sie die Code Analyse benötigen, können Sie die Qualität des Codes verbessern, der in die Codebasis eingecheckt wird.

> [!NOTE]
> Diese Funktion ist nur verfügbar, wenn Sie Team Foundation Server verwenden.

 Eincheck Richtlinien für die Code Analyse werden in den Teamprojekt Einstellungen festgelegt und gelten für jedes Code Projekt im Teamprojekt. Code Analyse Ausführungen werden für Code Projekte in der Projektdatei (. XXPROJ) für das Code Projekt konfiguriert. Code Analyse Ausführungen werden auf dem lokalen Computer ausgeführt. Wenn Sie eine Eincheck Richtlinie für die Code Analyse aktivieren, müssen die Dateien in einem Code Projekt, das eingecheckt werden soll, nach der letzten Bearbeitung kompiliert werden, und es muss eine Code Analyse ausgeführt werden, in der mindestens die Regeln in den Teamprojekt Einstellungen auf dem Computer ausgeführt werden müssen, auf dem die Änderungen vorgenommen wurden.

- Bei verwaltetem Code legen Sie die Eincheck Richtlinie durch Angabe eines *Regelsatzes* fest, der eine Teilmenge der Code Analyse Regeln enthält.

- Bei C/C++-Code erfordert die Eincheck Richtlinie, dass alle Code Analyse Regeln ausgeführt werden. Sie können Präprozessordirektiven hinzufügen, um bestimmte Regeln für die einzelnen Code Projekte im Teamprojekt zu deaktivieren.

  Nachdem Sie eine Eincheck Richtlinie für verwalteten Code angegeben haben, können die Teammitglieder ihre Code Analyse Einstellungen für Code Projekte mit den Teamprojekt-Richtlinien Einstellungen synchronisieren.

### <a name="to-open-the-check-in-policy-editor"></a>So öffnen Sie den Editor für Check-in-Richtlinien

1. Klicken Sie in Team Explorer mit der rechten Maustaste auf den Teamprojekt Namen, zeigen Sie auf **Teamprojekt Einstellungen**, und klicken Sie dann auf **Quell**Code Verwaltung.

2. Wählen Sie im Dialogfeld **Quell** Code Verwaltung die Registerkarte **Check-in-Richtlinie** aus.

3. Führen Sie eines der folgenden Verfahren aus:

    - Klicken Sie auf **Hinzufügen** , um eine neue Eincheck Richtlinie zu erstellen.

    - Doppelklicken Sie in der Liste **Richtlinientyp** auf das vorhandene **Code Analyse** Element, um die Richtlinie zu ändern.

### <a name="to-set-policy-options"></a>So legen Sie Richtlinien Optionen fest

- Aktivieren oder deaktivieren Sie die folgenden Optionen:

    |Option|BESCHREIBUNG|
    |------------|-----------------|
    |**Erzwingen Sie den Eincheck Vorgang, sodass nur Dateien enthalten sind, die Teil der aktuellen Projekt Mappe sind.**|Die Code Analyse kann nur für Dateien ausgeführt werden, die in den Projektmappen-und Projekt Konfigurationsdateien Diese Richtlinie stellt sicher, dass der gesamte Code, der Teil einer Lösung ist, analysiert wird.|
    |**C/C++-Code Analyse erzwingen (/analyze)**|Erfordert, dass alle C-oder C++-Projekte mit der/analyze-Compileroption erstellt werden, um die Code Analyse auszuführen, bevor Sie eingeglichen werden können.|
    |**Code Analyse für verwalteten Code erzwingen**|Erfordert, dass alle verwalteten Projekte eine Code Analyse ausführen und erstellt werden, bevor Sie eingeglichen werden können.|

-

### <a name="to-specify-a-managed-rule-set"></a>So geben Sie einen verwalteten Regelsatz an

- Verwenden Sie in der Liste **diesen Regelsatz ausführen** eine der folgenden Methoden:

  - Wählen Sie einen Microsoft Standard-Regelsatz aus.

  - Um einen benutzerdefinierten Regelsatz auszuwählen, klicken Sie auf **\<Select Rule Set from Source Control...>** , und geben Sie dann den Versions Kontroll Pfad des Regelsatzes im Quellcodeverwaltungs-Browser ein. Die Syntax eines Versions Kontroll Pfads lautet wie folgt:

  - **$/** `TeamProjectName` **/** `VersionControlPath`

  - Weitere Informationen zum Erstellen und Implementieren eines benutzerdefinierten Eincheck Richtlinien-Regelsatzes finden Sie unter [Implementieren von benutzerdefinierten Eincheck Richtlinien für verwalteten Code](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Weitere Informationen
 [Erstellen und Verwenden von Eincheckrichtlinien für die Codeanalyse](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
