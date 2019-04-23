---
title: Analysieren von Visual Basic und C# Qualität in Store-apps, die mit der statischen Codeanalyse von code
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb.express
ms.assetid: cab553fc-19a9-4cbf-858e-8200258ffe50
caps.latest.revision: 16
author: erickson-doug
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: daa26ed2e893d4e11b9f2e18ef5127aafe847b96
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60108336"
---
# <a name="analyze-visual-basic-and-c-code-quality-in-store-apps-using-visual-studio-static-code-analysis"></a>Analysieren der Qualität von Visual Basic- und C#-Code in Store-Apps mit der statischen Codeanalyse von Visual Studio

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gilt Sie für Windows und Windows Phone] (.. /Image/windows_and_phone_content.png "Windows_and_phone_content")

 Das Codeanalysetool in Visual Studio Express überprüft den Code auf eine Reihe von allgemeinen Fehlern und auf Verstöße gegen gebräuchliche Programmiergrundlagen. Codeanalysewarnungen unterscheiden sich von C#-Compilerfehlern und -Warnungen, da das Codeanalysetool nach bestimmten Codeschemata sucht, die gültig sind, jedoch Probleme für Sie oder andere Personen bereiten können, die den Code verwenden. Codeanalyse kann auch Fehler im Code suchen, die schwierig durch Tests zu erkennen sind. Das regelmäßige Ausführen des Codeanalysetools während des Entwicklungsprozesses kann die Qualität der App erhöhen.

> [!NOTE]
>  In Visual Studio Ultimate, Visual Studio Premium und Visual Studio Professional können Sie sämtliche Funktionen der Codeanalyse verwenden. Siehe [Analysieren der Anwendungsqualität mit Codeanalysetools](http://msdn.microsoft.com/library/dd264897.aspx) in der MSDN Library.

## <a name="in-this-topic"></a>In diesem Thema
 Erfahren Sie:

 [Ausführen der Codeanalyse](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Run)

 [Analysieren und Auflösen von Codeanalysewarnungen](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Analyze)

 [Unterdrücken der Codeanalysewarnungen](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Suppress)

 [Durchsuchen und Filtern von Codeanalyseergebnissen](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Search)

 [Visual Basic- und C#-Codeanalysewarnungen](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Warnings)

## <a name="BKMK_Run"></a> Ausführen der Codeanalyse
 So führen Sie die Codeanalyse in der Visual Studio-Projektmappe aus

- Wählen Sie im Menü **Build** die Option **Codeanalyse für Lösung ausführen** aus.

  So führen Sie die Codeanalyse beim Erstellen eines Projekts jedes Mal automatisch aus

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektnamen und dann auf **Eigenschaften**.

2. Klicken Sie auf der Seite der Projekteigenschaften auf **Codeanalyse**, und klicken Sie dann auf **Codeanalyse beim Erstellen aktivieren** (definiert eine CODE_ANALYSIS-Konstante) aus.

   Die Projektmappe wird kompiliert und die Codeanalyse ausgeführt. Die Ergebnisse werden im Codeanalysefenster angezeigt.

   ![Codeanalysefenster](../test/media/ca-managed-collapsed.png "CA_Managed_Collapsed")

## <a name="BKMK_Analyze"></a> Analysieren und Auflösen von Codeanalysewarnungen
 Um eine bestimmte Warnung zu analysieren, klicken Sie im Codeanalysefenster auf den Titel der Warnung. Die Warnung wird erweitert, um ausführliche Informationen zum Problem anzuzeigen.

 ![Erweiterte Codeanalysewarnung](../test/media/ca-managed-callouts.png "CA_Managed_Callouts")

 Wenn Sie eine Warnung erweitern, wird die Codezeile, die die Warnung verursacht hat im Code-Editor von Visual Studio hervorgehoben.

 ![Textmarkierung für Codeanalyse](../test/media/ca-managed-sourceline.png "CA_Managed_SourceLine")

 Nachdem Sie die Ursache des Problems verstanden haben, können Sie es im Code beheben. Wiederholen Sie die Codeanalyse, um sicherzustellen, dass die Warnung nicht mehr im Codeanalysefenster angezeigt wird und dass die Lösung des Problems keine neuen Warnungen ausgelöst hat.

> [!TIP]
>  Sie können die Codeanalyse im Codeanalysefenster erneut ausführen. Klicken Sie auf **Analysieren**, und wählen Sie den Bereich der Analyse aus. Sie können die Analyse für die gesamte Projektmappe oder für ein ausgewähltes Projekt erneut ausführen.

## <a name="BKMK_Suppress"></a> Unterdrücken der Codeanalysewarnungen
 Mitunter möchten Sie möglicherweise darauf verzichten, eine Codeanalysewarnung zu korrigieren. So kann es beispielsweise vorkommen, dass das Auflösen der Warnung im Verhältnis zur Wahrscheinlichkeit, dass das Problem in einer realen Implementierung des Codes auftritt, eine zu große Bearbeitung des Codes erfordert. Oder Sie gehen davon aus, dass die für die Warnung verwendete Analyse für den jeweiligen Kontext ungeeignet ist. Sie können Warnungen unterdrücken, sodass diese nicht mehr im Codeanalysefenster angezeigt werden.

 So unterdrücken Sie eine Warnung

1. Wenn die ausführlichen Informationen nicht angezeigt werden, klicken Sie auf den Titel der Warnung, um sie zu erweitern.

2. Wählen Sie unten in der Warnung den Link **Aktionen** aus.

3. Zeigen Sie auf **Meldung unterdrücken**, und wählen Sie dann entweder **In Source** (In Quelle) oder **In Suppression File** (In Unterdrückungsdatei) aus.

   - **In Quelle** fügt ein `SuppressMessage`-Attribut in der Quelldatei über der Methode ein, die die Warnung generiert. Dadurch wird die Unterdrückung leichter gefunden.

   - **In Unterdrückungsdatei** fügt ein `SuppressMessage`-Attribut zur **GlobalSuppressions.cs**-Datei des Projekts hinzu. Dies kann die Verwaltung der Unterdrückungen vereinfachen. Beachten Sie, dass das `SuppressMessage`-Attribut, das zu **GlobalSuppression.cs** hinzugefügt wurde, auch auf die Methode angewendet wird, die die Warnung generiert. Sie unterdrückt die Warnung nicht global.

     Die Entscheidung, ob die Warnung in der Quelldatei oder in der Unterdrückungsdatei unterdrückt wird, hängt vom Programmierstil und den Anforderungen ab.

## <a name="BKMK_Search"></a> Suchen und Filtern der Codeanalyseergebnisse
 Sie können lange Listen mit Warnmeldungen durchsuchen und Warnungen in Projektmappen mit mehreren Projekten filtern.

 ![Fenster zum Suchen und Filtern der Codeanalyse](../test/media/ca-searchfilter.png "CA_SearchFilter")

 In [!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)] haben alle Codeanalysewarnungen den Schweregrad der Warnung.

## <a name="BKMK_Warnings"></a> Visual Basic- und C#-Codeanalysewarnungen
 Codeanalyse löst die folgenden Warnungen aus:

 [CA1001: Typen, die löschbare Felder besitzen, müssen gelöscht werden können](http://msdn.microsoft.com/library/ms182172.aspx)

 [CA1821: Leere Finalizer entfernen](http://msdn.microsoft.com/library/bb264476.aspx)

 [CA2213: Verwerfbare Felder verwerfen](http://msdn.microsoft.com/library/ms182328.aspx)

 [CA2229: Serialisierungskonstruktoren implementieren](http://msdn.microsoft.com/library/ms182343.aspx)

 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](http://msdn.microsoft.com/library/ms182359.aspx)
