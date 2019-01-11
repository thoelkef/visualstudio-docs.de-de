---
title: Überprüfen und Debuggen von SharePoint-Code | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1705e77472ba9b8fa7a01d047c0aadaf342b7932
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916834"
---
# <a name="verify-and-debug-sharepoint-code"></a>Überprüfen und Debuggen von SharePoint-code
Mit IntelliTrace und Unittests können Sie die SharePoint-Lösungen leichter debuggen und sicherstellen, dass jede Methode in ihnen ordnungsgemäß funktioniert. Sie können diese Funktionen für SharePoint-Projekte in Visual Studio verwenden, indem Sie die gleichen Schritte wie für andere Typen von Projekten.

## <a name="intellitrace"></a>IntelliTrace
Mit IntelliTrace können Sie nicht nur den aktuellen Zustand der SharePoint-Lösung bestimmen, sondern auch in der Vergangenheit aufgetretene Ereignisse sowie den Kontext, in dem sie aufgetreten sind. Sie können zwischen verschiedenen Zeitpunkten in Ihrer SharePoint-Lösung, an denen relevante Ereignisse erfasst wurden, hin und her navigieren und die Zustände und Werte von Variablen an jedem Punkt überprüfen. Indem Sie diese dynamische Navigation verwenden, können Sie die SharePoint-Lösungen schneller und einfacher debuggen, ohne zahlreiche Haltepunkte festzulegen. Sie können auch die Debugsitzung in einem IntelliTrace-Protokoll speichern (*ITRACE*) Datei, öffnen Sie es später noch Mal in Visual Studio Enterprise und führen Sie nach einem Absturz zu debuggen. Die *ITRACE* -Datei enthält ausführliche Informationen, wann und wo bestimmte SharePoint-Fehler aufgetreten ist, so, dass Sie einfacher herausfinden, was den Fehler verursacht. Die Informationen in den *ITRACE* Datei ist eine Teilmenge des vollständigen Fehlerprotokolls, das die vereinheitlichten Protokollierungsdiensts (ULS) in SharePoint erstellt. Diese Informationen umfassen Ereignisse, die für SharePoint spezifisch sind, wie z. B. wenn ein Benutzerprofil geöffnet oder geschlossen wird und wenn Eigenschaften in einem SharePoint-Projekt geladen, gelesen oder geändert werden. Sie können konfigurieren, welche Ereignisse IntelliTrace aufzeichnet. Weitere Informationen finden Sie unter [Verwenden gespeicherter IntelliTrace-Daten](../debugger/using-saved-intellitrace-data.md).

Wenn ein Fehler in SharePoint auftritt, zeigt das Fehlerdialogfeld einen "Korrelations-ID"-Bezeichner für diesen speziellen Fehler an. Sie können auch Korrelations-IDs abrufen, von Ereignissen, die in aufgeführt sind die *ITRACE* Datei. Um eine Liste aller Ereignisse anzuzeigen, die mit der angegebenen Korrelations-ID aufgetreten sind, können Sie eingeben, die ID in der **Analysis** Teil der Seite der IntelliTrace-Zusammenfassung. In diesem Abschnitt können Sie auswählen, ob nur die Namen der aufgetretenen Ereignisse angezeigt werden sollen oder die Namen der Ereignisse zusammen mit ihren Aufrufinformationen, wie z. B. der Funktionsname, die Beendigungs- und Einstiegspunkte, Parameter und Rückgabewerte.

Sie können Visual Studio-Ereignisse in IntelliTrace abrufen, indem Sie die Auswahl der **F5** Schlüssel. Um für SharePoint spezifische Ereignisse abzurufen, müssen Sie jedoch IntelliTrace-Daten in SharePoint-Lösungen sammeln, indem Sie Microsoft Monitoring Agent verwenden. Dieses Tool sammelt IntelliTrace-Daten und erstellt *ITRACE* -Dateien für Anwendungen, die außerhalb von Visual Studio bereitgestellt werden. Weitere Informationen finden Sie unter [IntelliTrace-Funktionen](../debugger/intellitrace-features.md) und [mit den eigenständigen IntelliTrace Collector](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="unit-test"></a>Komponententest
Sie können Fehler im Code leichter finden, indem Sie Unittests ausführen, bei denen Sie Testcode in Testmethoden schreiben und ausführen. Diese Methoden enthalten leere Variablen und eine Assert-Anweisung, die Sie verwenden können, um die Logik und die Funktionalität des Projekts auf Grundlage des SharePoint-Objektmodells zu überprüfen. Weitere Informationen finden Sie unter [Komponententests des Codes](../test/unit-test-your-code.md).

### <a name="support-for-microsoft-fakes-framework"></a>Unterstützung für Microsoft Fakes-framework
SharePoint-Projekte unterstützen Microsoft Fakes, ein Isolationsframework, in dem Sie delegatbasierte Test-Stubs und -Shims in Anwendungen erstellen können, die auf .NET Framework basieren. Mithilfe des Fakes Framework können Sie Platzhalterimplementierungen in Ihren Komponententests erstellen, verwalten und einfügen. Diese Stubs und Shims isolieren die Komponententests von der Umgebung. Sie können Stubs erstellen, um Code zu testen, der Schnittstellen oder nicht versiegelte Klassen mit überschreibbaren Methoden verwendet. Sie können Shims erstellen, um hartcodierte Aufrufe von versiegelten Klassen mit statischen oder nicht überschreibbaren Methoden zu einer alternativen Shim-Implementierung umzuleiten. Sie können auch Delegate mit Stub-Typen und Shim-Typen verwenden, um das Verhalten einzelner Stub-Member dynamisch anzupassen. Weitere Informationen finden Sie unter [Isolieren von getestetem Code mithilfe von Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

## <a name="related-articles"></a>Verwandte Artikel

|Titel|Beschreibung|
|-----------|-----------------|
|[IntelliTrace](../debugger/intellitrace.md)|Beschreibt, wie Visual Studio-Projektmappen mithilfe von IntelliTrace leichter zu debuggen sind.|
|[Exemplarische Vorgehensweise: Debuggen einer SharePoint-Anwendung mit IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Veranschaulicht, wie IntelliTrace verwendet wird, um Codefehler in einem SharePoint-Projekt zu suchen.|
|[Komponententest für Code](../test/unit-test-your-code.md)|Beschreibt, wie logische Fehler in Ihrem Code anhand von Komponententests gesucht werden.|

## <a name="see-also"></a>Siehe auch

- [Verbessern der Codequalität](../test/improve-code-quality.md)