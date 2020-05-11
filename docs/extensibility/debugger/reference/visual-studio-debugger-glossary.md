---
title: Glossar des Visual Studio-Debuggers | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 954532311fe6b63fc288877a6d41722e6ea47581
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713346"
---
# <a name="visual-studio-debugger-glossary"></a>Glossar zum Visual Studio-Debugger
Im Folgenden finden Sie [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Begriffe, die im Debugging SDK verwendet werden.

## <a name="terms"></a>Begriffe
 gebundener Haltepunkt Eine Abstraktion für einen im Code festgelegten Haltepunkt. Es besteht eine 1:1-Beziehung zwischen einem gebundenen Haltepunkt und einer Haltepunktanweisung im Codestream. Beim Entladen des Codes können gebundene Haltepunkte die Bindung auflösen.

 Causality Bietet die Möglichkeit, einen logischen Ausführungsthread über mehrere physische Threads, Prozesse und Computer hinweg nachzuverfolgen und die Aufrufliste dieses logischen Threads an einem bestimmten Punkt in der Lebensdauer dieses Threads zu rekonstruieren.

 Codekontext Stellt eine Abstraktion einer Position im Code bereit, die dem Debugmodul bekannt ist. Bei den meisten Laufzeitarchitekturen ist ein Codekontext eine Adresse im Anweisungsstream eines Programms. Bei nicht traditionellen Sprachen, in denen Code möglicherweise nicht durch Anweisungen dargestellt wird, kann ein Codekontext auf andere Weise dargestellt werden.

 Codepfad Stellt einen Ausführungspunkt im Code dar, an dem eine Verzweigung oder ein Funktionsaufruf ausgeführt wird. Eine Stapelablaufverfolgung ist im Wesentlichen eine Liste von Funktionsaufrufcodepfaden.

 Debug-Engine (DE) Eine Komponente, die das Debuggen einer Laufzeitarchitektur ermöglicht. Ein Debugmodul arbeitet mit dem Interpreter oder Betriebssystem zusammen und stellt Debugdienstdienste wie Ausführungssteuerung, Haltepunkte und Ausdrucksauswertung bereit.

 Dokumentkontext Stellt eine Abstraktion einer Position in einem Quelldateidokument bereit, das dem Debugmodul bekannt ist. Für die meisten Sprachen ist ein Dokumentkontext eine Position in einer Quelldatei. Bei nicht traditionellen Sprachen, bei denen die Quelldatei möglicherweise kein Text ist, kann ein Dokumentkontext auf andere Weise dargestellt werden. Siehe auch *Dokumentposition*.

 Dokumentposition Stellt eine Abstraktion einer Position in einer Quelldatei bereit, die der IDE bekannt ist. Für die meisten Sprachen ist eine Dokumentposition eine Position in einer Quelldatei. Bei nicht traditionellen Sprachen kann eine Dokumentposition auf andere Weise dargestellt werden. Siehe auch *Dokumentkontext*.

 Fehlerhaltepunkt Eine Abstraktion zum Beschreiben eines Fehlers in einem ausstehenden Haltepunkt. Ein Fehlerhaltepunkt kann einen Fehler an der Position des ausstehenden Haltepunkts, den Ausdruck, der dem ausstehenden Haltepunkt zugeordnet ist, oder andere Informationen beschreiben, die verhindern, dass der ausstehende Haltepunkt an einen Codespeicherort gebunden wird.

 Evaluierungskontext Bietet eine Abstraktion eines Programmierkontexts für die Ausdrucksauswertung. In der Regel ist ein Evaluierungskontext ein Bereich. Bei der Ausdrucksauswertung in einem Ausdruckskontext stellt der Ausdruckskontext Bereichsregeln bereit, die dem Erstellungspunkt entsprechen. Beispielsweise stellt ein in einem Stapelrahmen erstellter Ausdruckskontext den Kontext zum Auswerten lokaler Variablen, Methodenparameter, Klassenmember (falls zutreffend) und globaler Variablen bereit.

 abgefangene Ausnahme Eine Ausnahme, die von einem Debugmodul abgefangen wird, auch wenn im aktuellen Stapelrahmen kein Ausnahmebehandlungsmechanismus vorhanden ist.

 JustMyCode Das Konzept, nur den Code zu debuggen, der einem Benutzer gehört, und den gesamten Zwischencode wie Systemcode zu ignorieren – auch wenn Quellcode für diesen Systemcode verfügbar ist.

 Ausstehender Haltepunkt Stellt eine Abstraktion für Haltepunkte vor, während und nach dem Laden von Code und eine Möglichkeit zum Virtualisieren von Haltepunkten bereit. Ein ausstehender Haltepunkt:

- Enthält alle Informationen, die zum Binden eines Haltepunkts an Code in einem oder mehreren Programmen erforderlich sind.

- Kann an mehrere Codespeicherorte in einem oder mehreren Programmen gebunden werden.

- Bindet sich niemals an Code.

  Jedes Mal, wenn Code geladen wird, werden alle ausstehenden Haltepunkte in einem Programm überprüft, um festzustellen, ob sie binden können. Ein ausstehender Haltepunkt enthält angeblich alle gebundenen Haltepunkte, die er bindet.

  prozess Ein physischer Win32-Prozess. Ein Prozess kann mehrere Programme enthalten. Siehe auch *Programm*.

  programm Ein einzelner Namespace, der in einer bestimmten Laufzeitarchitektur ausgeführt wird. Siehe auch *Prozess*.

  Sitzungsdebug-Manager (SDM) Verwaltet eine beliebige Anzahl von Debugmodulen, die eine beliebige Anzahl von Programmen in mehreren Prozessen auf einer beliebigen Anzahl von Computern debuggen. Auf der Basisebene ist das SDM ein Multiplexer von Debug-Engines. Darüber hinaus bietet das SDM eine einheitliche Ansicht der Debugsitzung für die IDE.

  stack frame Stellt den Berechnungszustand für einen bestimmten Frame und eine bestimmte Ebene geschachtelter Funktionsaufrufe dar.

  thread Der allgemeine Begriff der stapelbasierten Anweisungsausführung, der in mindestens einem Programm ausgeführt wird.

  Warnhaltepunkt Eine Abstraktion zum Beschreiben einer Warnung in einem ausstehenden Haltepunkt. Ein Warnhaltepunkt beschreibt einen Grund, warum der ausstehende Haltepunkt noch nicht an einen Codespeicherort gebunden ist. Dies kann sein, dass der Code für den vom ausstehenden Haltepunkt beschriebenen Speicherort oder aus einem anderen Grund noch nicht geladen wurde.

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio Debugger-Erweiterbarkeit](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
