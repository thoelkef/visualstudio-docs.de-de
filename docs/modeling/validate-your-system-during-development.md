---
title: Überprüfen des Systems während der Entwicklung
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98cde01932d2e0d73fdae1dad0ef4e5b3e659f34
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970373"
---
# <a name="validate-your-system-during-development"></a>Überprüfen des Systems während der Entwicklung
Visual Studio unterstützt Sie dabei, die Software mit den Anforderungen der Benutzer und der Architektur des Systems in Einklang zu bringen.

 Informationen dazu, welche Versionen von Visual Studio die einzelnen Funktionen unterstützen, finden Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Hauptaufgaben
 Überprüfen Sie die Software mithilfe der folgenden Aufgaben.

|**Aufgaben**|**Verwandte Themen**|
|-|-|
|**Stellen Sie sicher, dass die Software die Anforderungen der Benutzer erfüllt**:<br /><br /> Sie können Anforderungen und architektonische Modelle verwenden, um die Tests des Systems und seiner Komponenten zu organisieren. Durch diese Vorgehensweise können Sie sicherstellen, dass die Anforderungen, die für die Benutzer und andere Projektbeteiligte wichtig sind, getestet werden. Außerdem können Sie dadurch die Tests schneller aktualisieren, wenn sich die Anforderungen ändern.|-   [Entwickeln von Tests aus einem Modell](../modeling/develop-tests-from-a-model.md)|
|**Stellen Sie sicher, dass die Software mit dem vorgesehenen Entwurf des Systems konsistent bleibt:**<br /><br /> Abhängigkeitsdiagramme beschreiben die beabsichtigten Abhängigkeiten zwischen den Komponenten Ihrer Anwendung. Während der Entwicklung können Sie überprüfen, ob die tatsächlichen Abhängigkeiten im Code dem vorgesehenen Entwurf entsprechen.|-   [Erstellen von Abhängigkeitsdiagrammen aus Ihrem code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Überprüfen von Code mit Abhängigkeitsdiagrammen](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Externe Ressourcen

|**Kategorie**|**Links**|
|-|-|
|**Videos**|![Link zum Video](../data-tools/media/playvideo.gif) [Channel 9: Doug Seven: Verstehen von Code und Systementwurf mit Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![Link zum Video](../data-tools/media/playvideo.gif) [Channel 9: Entwerfen einer Anwendung mit einem Abhängigkeitsdiagramm](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![Link zum Video](../data-tools/media/playvideo.gif) [MSDN-Reihe: Überprüfen von Code mithilfe von Abhängigkeitsdiagrammen](http://go.microsoft.com/fwlink/?LinkID=214405)|
|**Foren**|-   [Visual Studio-Visualisierungs- & Modellierungstools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](http://go.microsoft.com/fwlink/?LinkId=184721)|
|**Blogs**|-   [Microsoft DevOps](https://blogs.msdn.microsoft.com/devops/)|
|**Technische Artikel und Journale**|[MSDN Architecture Center](http://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>Siehe auch

- [Testen der Anwendung](/azure/devops/test/overview?view=vsts)
- [Modellieren von Benutzeranforderungen](../modeling/model-user-requirements.md)
- [Analysieren und Modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
