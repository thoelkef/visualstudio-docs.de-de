---
title: Überprüfen des Systems während der Entwicklung
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae2b7d81b1f166e6cc97debc3291661d59ee6960
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75594031"
---
# <a name="validate-your-system-during-development"></a>Überprüfen des Systems während der Entwicklung

Mithilfe von Visual Studio können Sie Ihre Software mit den Benutzer Anforderungen und der Architektur Ihres Systems konsistent halten.

Informationen dazu, welche Versionen von Visual Studio die einzelnen Funktionen unterstützen, finden Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Hauptaufgaben

Verwenden Sie die folgenden Aufgaben, um Ihre Software zu überprüfen:

|**Aufgaben**|**Verwandte Themen**|
|-|-|
|**Stellen Sie sicher, dass die Software die Anforderungen der Benutzer erfüllt**:<br /><br />Verwenden Sie Anforderungen und Architekturmodelle, um die Tests des Systems und seiner Komponenten zu organisieren. Durch diese Vorgehensweise können Sie sicherstellen, dass die Anforderungen, die für die Benutzer und andere Projektbeteiligte wichtig sind, getestet werden. Außerdem können Sie dadurch die Tests schneller aktualisieren, wenn sich die Anforderungen ändern.|- [Entwickeln von Tests aus einem Modell](../modeling/develop-tests-from-a-model.md)|
|**Stellen Sie sicher, dass die Software mit dem vorgesehenen Entwurf des Systems konsistent bleibt:**<br /><br />Abhängigkeits Diagramme beschreiben die beabsichtigten Abhängigkeiten zwischen den Komponenten der Anwendung. Während der Entwicklung können Sie überprüfen, ob die tatsächlichen Abhängigkeiten im Code dem vorgesehenen Entwurf entsprechen.|- [Erstellen von Abhängigkeitsdiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Überprüfen von Code mit Abhängigkeitsdiagrammen](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Externe Ressourcen

|**Kategorie**|**Links**|
|-|-|
|**Videos**|![Link zu Video ](../data-tools/media/playvideo.gif) [Channel 9: Doug 7: Code Verständnis und System Entwurf mit Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![Link zu Video ](../data-tools/media/playvideo.gif) [Channel 9: Architektur einer Anwendung](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application))|
|**Foren**|- [Visual Studio-Visualisierungs- & Modellierungstools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio-Erweiterbarkeit](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>Weitere Informationen

- [Modellieren von Benutzeranforderungen](../modeling/model-user-requirements.md)
- [Analyse und Modell Architektur](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
