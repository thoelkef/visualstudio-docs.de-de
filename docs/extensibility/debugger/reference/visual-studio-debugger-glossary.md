---
title: Visual Studio-Debugger-Glossar | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36c6ea7d4559d63f8d230d73e0df5f14fc21a0b5
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458035"
---
# <a name="visual-studio-debugger-glossary"></a>Glossar zum Visual Studio-Debugger
Im folgenden sind die Begriffe in der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugging-SDK.

## <a name="terms"></a>Begriffe
 gebundene Haltepunkt eine Abstraktion für einen Haltepunkt im Code festlegen. Es ist eine direkte Beziehung zwischen einen gebundenen Haltepunkt und eine Anweisung Haltepunkt im Code-Datenstrom. Wenn der code entladen, gebundener Haltepunkte möglicherweise Aufheben der Bindung.

 Kausalität bietet die Möglichkeit, einen logischen Thread der Ausführung auf mehrere physische Threads, Prozesse und Computer nachzuverfolgen und um die Aufrufliste dieses logischen Threads zu einem bestimmten Zeitpunkt in der Lebensdauer des Threads zu rekonstruieren.

 Codekontext stellt eine Abstraktion einer Position im Code bekannt, dass die Debug-Engine bereit. Für die meisten Laufzeitfehler-Architekturen ist ein Codekontext eine Adresse im Anweisungsstream eines Programms. Für nicht traditionelle Sprachen, in denen Code Anweisungen nicht dargestellt werden kann, kann ein Codekontext mithilfe anderer Methoden dargestellt werden.

 Codepfad stellt einen Zeitpunkt der Ausführung im Code, in denen eine Abzweigung verwendet wird, oder erfolgt ein Funktionsaufruf dar. Eine stapelüberwachung ist praktisch eine Liste von Funktion Aufruf Codepfade.

 Debug-Engine (DE) eine Komponente, die ermöglicht das Debuggen von einer Runtime-Architektur. Eine Debug-Engine funktioniert in Verbindung mit dem Betriebssystem oder -Interpreter und Debuggen von Diensten wie z. B. Ausführung-Steuerelement, Haltepunkte und Ausdruck Auswertung enthält.

 Dokumentkontext stellt eine Abstraktion einer Position in einer Datei-Quelldokument bekannt, dass die Debug-Engine bereit. Für die meisten Sprachen ist ein Dokumentkontext eine Position in einer Quelldatei. Für nicht traditionelle Sprachen, für die die Quelldatei Text möglicherweise nicht möglicherweise ein Dokumentenkontext andere Weise dargestellt werden. Siehe auch *dokumentieren Position*.

 Dokumentposition stellt eine Abstraktion einer Position in einer Quelldatei bekannt, dass die IDE bereit. Für die meisten Sprachen wird eine Dokumentposition einer Position in einer Quelldatei. Für nicht traditionelle Sprachen wird möglicherweise eine Dokumentposition auf andere Weise dargestellt werden. Siehe auch *Dokumentkontext*.

 Fehler beim Haltepunkt eine Abstraktion für einen Fehler in ein ausstehender Haltepunkt beschreiben. Ein Haltepunkt auf Fehler unter Umständen einen Fehler in den Speicherort der ausstehenden Haltepunkt, den Ausdruck, der mit den ausstehenden Haltepunkt oder andere Informationen, die Bindung den ausstehenden Haltepunkt an einem codespeicherort verhindert beschreiben.

 Evaluierungskontext stellt eine Abstraktion der ein Programmierungskontext für die Auswertung von Ausdrücken bereit. In der Regel mit ein Evaluierungskontext ein Bereich ist. Bei der Auswertung des Ausdrucks in einem Ausdruckskontext bietet der Ausdruckskontext Bereichsregeln, die der Zeitpunkt der Erstellung zu entsprechen. Beispielsweise wird ein Ausdruckskontext erstellt, die in einem Stapelrahmen der Kontext bereitgestellt, für Ihre Evaluierung von lokalen Variablen, Methodenparameter, Klasse, Elemente (falls zutreffend) und globale Variablen.

 abgefangen Ausnahme eine Ausnahme, die von einer Debug-Engine abgefangen wird, auch wenn kein Mechanismus zur Ausnahmebehandlung direkt in den aktuellen Stapelrahmen ist.

 JustMyCode das Konzept der nur den Code Debuggen, der zu einem Benutzer gehört, und wird ignoriert, alle temporären Code wie z. B. Systemcode – selbst wenn der Quellcode für diesen Systemcode verfügbar ist.

 ausstehender Haltepunkt ist stellt eine Abstraktion für Haltepunkte vor, während und nach Code geladen, und es wird eine Möglichkeit, Haltepunkte zu virtualisieren. Ein ausstehender Haltepunkt:

- Enthält alle Informationen, die erforderlich sind, einen Haltepunkt für Code in einem oder mehreren Programmen zu binden.

- Können eine Bindung an mehreren Standorten von Code in einem oder mehreren Programmen.

- Bindet niemals selbst Code.

  Jedes Mal Code lädt, alle ausstehenden Haltepunkte in einem Programm werden überprüft, um festzustellen, ob sie binden können. Ein ausstehender Haltepunkt ist dann alle gebundenen Breakpoints enthalten, die gebunden wird.

  verarbeitet einen physische Win32-Prozess. Ein Prozess kann mehrere Programme enthalten. Siehe auch *Programm*.

  Programmieren von einem einzigen Namespace, die in einer bestimmten Laufzeit-Architektur ausgeführt. Siehe auch *Prozess*.

  sitzungsbasierter Debug-Manager (SDM) verwaltet eine beliebige Anzahl von Debug-Engines, die eine beliebige Anzahl von Programmen in mehreren Prozessen auf eine beliebige Anzahl von Computern zu debuggen. Auf der Basisebene ist das SDM ein multiplexer der Debug-Engines. Darüber hinaus bietet das SDM eine einheitliche Ansicht der Debugsitzung der IDE.

  Stapelrahmen stellt den Status der Berechnung auf einem bestimmten Frame und Maß Aufrufe geschachtelter Funktionen dar.

  Thread das generalisierte Konzept der Anweisung stapelbasierten-Ausführung in mindestens ein Programm ausgeführt werden soll.

  Warnung Haltepunkt eine Abstraktion zum Beschreiben der in ein ausstehender Haltepunkt einer Warnung. Ein Haltepunkt für die Warnung beschreibt einen Grund, warum der ausstehenden Haltepunkt noch nicht an einen Speicherort gebunden wurde. Dies kann sein, dass der Code noch nicht für den Speicherort der ausstehenden Haltepunkt beschrieben oder einem anderen Grund geladen ist.

## <a name="see-also"></a>Siehe auch
- [Visual Studio Debugger-Erweiterbarkeit](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)