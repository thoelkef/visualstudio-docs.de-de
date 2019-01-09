---
title: Hierarchische Organisation der Ressourcen für die Lokalisierung
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- resource files, localized
- localization [Visual Studio], resources
- fallback resources
- international applications [Visual Studio], storing resources
- satellite assemblies, resource hierarchies
- globalization [Visual Studio], resources
- satellite assemblies
- resources [Visual Studio], fallback system
- resource files, fallback processes
ms.assetid: dadf8f2c-f74c-44d7-bec0-a1e956d8d38d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dca07960458360ebec0dd0952125e92e2572ab34
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53965503"
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>Hierarchische Organisation der Ressourcen für die Lokalisierung

In Visual Studio werden lokalisierte Ressourcen (kulturspezifische Daten wie Zeichenfolgen und Bilder) in separaten Dateien gespeichert und je nach Kultureinstellung der Benutzeroberfläche geladen. Um zu verstehen, wie lokalisierte Ressourcen geladen werden, ist es hilfreich, sie als auf hierarchische Weise organisiert zu betrachten.

## <a name="kinds-of-resources-in-the-hierarchy"></a>Arten von Ressourcen in der Hierarchie

- Ganz oben in der Hierarchie befinden sich die Fallbackressourcen für Ihre Standardkultur, zum Beispiel Englisch („en“). Diese Fallbackressourcen sind die einzigen Ressourcen, die keine eigene Datei haben. Sie sind in der Hauptassembly gespeichert.

- Unterhalb der Fallbackressourcen befinden sich die Ressourcen für die neutralen Kulturen. Eine neutrale Kultur ist nicht einem Land/einer Region, sondern einer Sprache zugeordnet. Eine neutrale Kultur zum Beispiel Französisch („fr“). (Die Fallbackressourcen gelten zwar auch für neutrale Kulturen, jedoch nur für spezielle.)

- Unterhalb der Ressourcen für neutrale Kulturen befinden sich die Ressourcen für die spezifischen Kulturen. Eine spezifische Kultur ist einer Sprache und einem Land/einer Region zugeordnet. Eine spezifische Kultur ist zum Beispiel kanadisches Französisch („fr-CA“).

Wenn eine Anwendung versucht, eine lokalisierte Ressource, zum Beispiel eine Zeichenfolge, zu laden, diese aber nicht finden kann, wird die Hierarchie durchsucht, bis eine Ressourcendatei gefunden wird, die die angeforderte Ressource enthält.

Die beste Möglichkeit, Ihre Ressourcen zu speichern, ist sie so weit wie möglich zu generalisieren. Das bedeutet, dass lokalisierte Zeichenfolgen, Bilder usw. nach Möglichkeit in Ressourcendateien für neutrale und nicht für spezifische Kulturen gespeichert werden. Beispiel: Wenn Sie über Ressourcen für belgisches Französisch („fr-BE“) verfügen und die unmittelbar darüber liegenden Ressourcen die Fallbackressourcen in Englisch sind, könnte möglicherweise ein Problem entstehen, wenn jemand Ihre Anwendung auf einem für kanadisches Französisch konfigurierten System verwendet. Das System sucht nach einer Satellitenassembly für „fr-CA“, findet jedoch keine. Daraufhin wird die Hauptassembly geladen, die die Fallbackressource (Englisch) enthält, statt die französischen Ressourcen zu laden. In der folgenden Abbildung wird dieses unerwünschte Szenario dargestellt.

![Nur bestimmte Ressourcen](../ide/media/vbspecificresourcesonly.gif)

Wenn Sie der empfohlenen Vorgehensweise folgen und möglichst viele Ressourcen in einer neutralen Ressourcendatei für die Kultur „fr“ speichern, werden einem kanadisch-französischen Benutzer keine für die Kultur „fr-BE“ gekennzeichneten Ressourcen, sondern französische Zeichenfolgen angezeigt. In der folgenden Abbildung wird dieses bevorzugte Szenario dargestellt.

![Grafik zu NeutralSpecificResources](../ide/media/vbneutralspecificresources.gif)

## <a name="see-also"></a>Siehe auch

- [Neutrale Ressourcensprachen für die Lokalisierung](../ide/neutral-resources-languages-for-localization.md)
- [Sicherheit und lokalisierte Satellitenassemblys](../ide/security-and-localized-satellite-assemblies.md)
- [Lokalisieren von Anwendungen](../ide/localizing-applications.md)
- [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)