---
title: Anwendungsfehler bei der Codeanalyse
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio ALM], code analysis
- code analysis, errors
- managed code, code analysis errors
- code analysis, policy errors
ms.assetid: d8fd9475-ac9b-4085-b5a3-b0c807922cac
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 25ee5a4e9a84201f93783bcef64f92ec74206fc6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62422746"
---
# <a name="code-analysis-application-errors"></a>Anwendungsfehler bei der Codeanalyse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Dieser Abschnitt ist eine Referenz für die Fehlermeldungen, die vom Analysetool für verwalteten Code generiert werden. Um Hilfe für eine bestimmte Fehlermeldung erhalten, geben Sie die Fehlernummer in der **suchen Sie nach** Feld im Index.

## <a name="in-this-section"></a>In diesem Abschnitt

|||
|-|-|
|[CA0001](ca0001.md)|In verwaltetem Code Analysetool, das einen erwarteten Fehlerzustand nicht angegeben, wurde eine Ausnahme ausgelöst.|
|[CA0051](ca0051.md)|Es wurden keine Regeln ausgewählt.|
|[CA0052](ca0052.md)|Es wurden keine Ziele ausgewählt, um zu analysieren.|
|[CA0053](ca0053.md)|Regelassembly konnte nicht geladen werden.|
|[CA0054](ca0054.md)|Eine benutzerdefinierte Regelassembly verfügt über ungültige XML-Ressourcen.|
|[CA0055](ca0055.md)|Datei konnte nicht geladen:\<Pfad >|
|[CA0056](ca0056.md)|Eine Projektdatei hat eine falsche Version des Analysetools.|
|[CA0057](ca0057.md)|Verstöße gegen können nicht den aktuellen Satz von Zielen und Regeln zugeordnet werden.|
|[CA0058](ca0058.md)|Fehler beim Laden von Assemblys, die auf die verwiesen wird.|
|[CA0059](ca0059.md)|Fehler bei Befehlszeilenschaltern.|
|[CA0060](ca0060.md)|Fehler beim Laden von Assemblys, die auf die indirekt verwiesen wird.|
|[CA0061](ca0061.md)|Die Regel "*RuleId*' wurde nicht gefunden.|
|[CA0062](ca0062.md)|Die Regel "*RuleId*"auf die im Regelsatz verwiesen wird"*RuleSetName*' wurde nicht gefunden.|
|[CA0063](ca0063.md)|Fehler beim Laden der Regelsatzdatei oder eine der abhängigen Regelsatzdateien.|
|[CA0064](ca0064.md)|Es wurde keine Analyse durchgeführt, da der angegebene Regelsatz nicht FxCop-Regeln enthalten hat.|
|[CA0065](ca0065.md)|Nicht unterstütztes Metadatenkonstrukt: Typ "*TypeName*"enthält sowohl eine Eigenschaft als auch ein Feld mit dem gleichen Namen"*NameDesEigenschaftenfelds*"|
|[CA0066](ca0066.md)|Der Wert "*VersionID*" bereitgestellt, um die **für/TargetFrameworkVersion** ist keine erkannte Version.|
|[CA0067](ca0067.md)|Verzeichnis wurde nicht gefunden.|
|[CA0068](ca0068.md)|Debuggen von Informationen konnte nicht gefunden werden, für die Zielassembly *"AssemblyName"*.|
|[CA0069](ca0069.md)|Verwenden alternative Plattform. *FrameworkVersion1* konnte nicht gefunden werden. Mithilfe von *FrameworkVersion2* stattdessen. Für optimale Analyseergebnisse zu erzielen stellen Sie sicher, dass die richtige .NET Framework installiert ist.|
|[CA0070](ca0070.md)|Assembly bzw. aufgrund von Berechtigungen für die Codezugriffssicherheit kann nicht geladen werden.|
|[CA0501](ca0501.md)|Lesen der Ausgabebericht kann nicht ausgeführt werden.|
|[CA0502](ca0502.md)|Nicht unterstützte Sprache.|
|[CA0503](ca0503.md)|Die Eigenschaft ist veraltet. Verwenden Sie die ersetzende Eigenschaft|
|[CA0504](ca0504.md)|Regelverzeichnis wurde ignoriert, da sie nicht vorhanden ist|
|[CA0505](ca0505.md)|Die Eigenschaft ist veraltet. Verwenden Sie die ersetzende Eigenschaft|
|[FxCopCmd-Fehler](fxcopcmd-errors.md)|Analysefehler bei verwaltetem Code.|

## <a name="related-sections"></a>Verwandte Abschnitte

- [Richtlinien zum Schreiben von sicherem Code](http://msdn.microsoft.com/9892fd19-45cd-44b6-9fa8-10f1b5cb6ea4)
- [Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
- [Ressourcen für das Beheben von Fehlern in Application Lifecycle Management-Tools](http://msdn.microsoft.com/library/76ca8f76-1e2d-4b55-89e2-bd59e4abe74c)