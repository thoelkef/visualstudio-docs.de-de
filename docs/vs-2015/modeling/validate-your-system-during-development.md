---
title: Überprüfen des Systems während der Entwicklung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b3de5cb1cc62d159567eee804c1aadef865e500a
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75845394"
---
# <a name="validate-your-system-during-development"></a>Überprüfen des Systems während der Entwicklung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio unterstützt Sie dabei, die Software mit den Anforderungen der Benutzer und der Architektur des Systems in Einklang zu bringen.

 Informationen dazu, welche Versionen von Visual Studio die einzelnen Funktionen unterstützen, finden Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Hauptaufgaben
 Überprüfen Sie die Software mithilfe der folgenden Aufgaben.

|**Tasks** (MSBuild-Aufgaben)|**Verwandte Themen**|
|---------------|---------------------------|
|**Stellen Sie sicher, dass das Modell konsistent ist:**<br /><br /> Abhängig davon, wie Modelle im Projekt verwendet und interpretiert werden, kann es sinnvoll sein, einige Kombinationen von Elementen nicht zuzulassen. Sie können z.B. durch eine Einschränkung festlegen, dass UML-Klassen immer [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]-kompatible Namen haben müssen. Solche Einschränkungen können in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Erweiterungen definiert werden.|-   Überprüfen des [UML-Modells](../modeling/validate-your-uml-model.md)<br />-   [Definieren von Validierungs Einschränkungen für UML-Modelle](../modeling/define-validation-constraints-for-uml-models.md)|
|**Stellen Sie sicher, dass die Software die Anforderungen der Benutzer erfüllt**:<br /><br /> Sie können Anforderungen und architektonische Modelle verwenden, um die Tests des Systems und seiner Komponenten zu organisieren. Durch diese Vorgehensweise können Sie sicherstellen, dass die Anforderungen, die für die Benutzer und andere Projektbeteiligte wichtig sind, getestet werden. Außerdem können Sie dadurch die Tests schneller aktualisieren, wenn sich die Anforderungen ändern.|-   [entwickeln von Tests aus einem Modell](../modeling/develop-tests-from-a-model.md)|
|**Stellen Sie sicher, dass die Software mit dem vorgesehenen Entwurf des Systems konsistent bleibt:**<br /><br /> Ebenendiagramme beschreiben die vorgesehenen Abhängigkeiten zwischen den Komponenten der Anwendung. Während der Entwicklung können Sie überprüfen, ob die tatsächlichen Abhängigkeiten im Code dem vorgesehenen Entwurf entsprechen.|-   [Erstellen von ebenendiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Überprüfen von Code mit ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Externe Ressourcen

|**Kategorie**|**Links**|
|------------------|---------------|
|**Videos**|![Link zu Video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Doug 7: Code Verständnis und System Entwurf mit Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![Link zu Video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Architektur einer Anwendung mithilfe eines ebenendiagramms](https://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-5-Architecting-an-Application)<br /><br /> ![Link zu Video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN-Gewusst wie-Reihe: Überprüfen von Code mit ebenendiagrammen](https://msdn.microsoft.com/vstudio/gg501755)|
|**Foren**|-   [Visual Studio-Visualisierungs- & Modellierungstools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blogs**|-   [Visual Studio ALM + Team Foundation Server Blog](https://blogs.msdn.com/b/visualstudioalm)|
|**Technische Artikel und Journale**|[MSDN Architecture Center](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Siehe auch
 [Testen der Anwendung](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [Erweitern von UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md) [Modellieren von Benutzer Anforderungen](../modeling/model-user-requirements.md) [analysieren und modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md)
