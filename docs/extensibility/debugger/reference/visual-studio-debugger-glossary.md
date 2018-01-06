---
title: "Glossar für Visual Studio-Debugger | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9cc1e668f1d78bc6a1db66b6fd4dfebf77b0f6ff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-debugger-glossary"></a>Glossar für Visual Studio-Debugger
Im folgenden werden die Begriffe, die in der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugging-SDK.  
  
## <a name="terms"></a>Begriffe  
 gebundenen Haltepunkt  
 Eine Abstraktion für einen Haltepunkt im Code festgelegt. Es ist eine direkte Beziehung zwischen einen gebundenen Haltepunkt und eine Anweisung Haltepunkt im Code-Datenstrom. Wenn code entladen wird, gebundenen Haltepunkte möglicherweise Aufheben der Bindung.  
  
 Verfolgen der Kausalität  
 Bietet die Möglichkeit, einen logischen Thread der Ausführung auf mehrere physische Threads und Prozesse Computer nachzuverfolgen und die Aufrufliste dieses logischen Threads zu einem bestimmten Zeitpunkt in der Lebensdauer des Threads zu rekonstruieren.  
  
 Codekontext  
 Stellt eine Abstraktion einer Position im Code bekannt, dass die Debugging-Modul. Für die meisten Laufzeit-Architekturen ist ein Codekontext einer Adresse in den Anweisungsstream ein Programm. Für traditionelle Sprachen, in denen Code Anweisungen nicht dargestellt werden kann, kann ein Codekontext auf andere Weise dargestellt werden.  
  
 Codepfad  
 Stellt einen Zeitpunkt der Ausführung im Code, in dem eine Abzweigung verwendet wird oder erfolgt ein Funktionsaufruf dar. Eine stapelüberwachung ist im Prinzip eine Liste der Funktion Aufruf Codepfade an.  
  
 Debugging-Modul (DE)  
 Eine Komponente, die ermöglicht das Debuggen von einer Laufzeit-Architektur. Ein Debugmodul funktioniert in Verbindung mit dem Betriebssystem oder Interpreter und stellt z. B. Ausführung-Steuerelement, Haltepunkte und Ausdruck Auswertung Debugdienste bereit.  
  
 Dokumentkontext  
 Stellt eine Abstraktion einer Position in einer Datei-Quelldokument bekannt, dass die Debugging-Modul bereit. Die meisten Sprachen ist ein Dokumentenkontext einer Position in einer Quelldatei. Für traditionelle Sprachen, für die die Quelldatei Text möglicherweise nicht möglicherweise ein Dokumentenkontext durch auch auf andere Weise dargestellt werden. Siehe auch *dokumentieren Position*.  
  
 Dokumentposition  
 Stellt eine Abstraktion einer Position in einer Quelldatei, die bekanntermaßen von der IDE bereit. Für die meisten Sprachen ist eine Dokumentposition Position in einer Quelldatei. Für traditionelle Sprachen wird möglicherweise eine Dokumentposition auf andere Weise dargestellt werden. Siehe auch *Dokumentenkontext*.  
  
 Fehler-Haltepunkt  
 Eine Abstraktion für einen Fehler in ein ausstehender Haltepunkt beschreiben. Ein Haltepunkt auf Fehler unter Umständen einen Fehler in den Speicherort des ausstehenden Haltepunkts, den Ausdruck mit der ausstehenden Haltepunkts oder andere Informationen, die Bindung an einen Speicherort Code ausstehenden Haltepunkt hindert beschreiben.  
  
 Evaluierungskontext  
 Stellt eine Abstraktion einer Programmierung Kontext für die Auswertung von Ausdrücken bereit. Üblicherweise handelt es sich bei ein Evaluierungskontext um einen Bereich. Bei der Auswertung von Ausdrücken im Ausdruckskontext eines, bietet der Ausdruckskontext Bereichsregeln, die der Zeitpunkt der Erstellung entsprechen. Beispielsweise wird ein Ausdruckskontext erstellt in einem Stapelrahmen der Kontext bereitstellt, zum Auswerten, lokale Variablen, Methodenparameter und Klassenmember (falls zutreffend), globale Variablen.  
  
 abgefangene Ausnahme  
 Eine Ausnahme, die von einem Debugging-Modul abgefangen wird, auch wenn keine Ausnahmebehandlungsmechanismus direkt in den aktuellen Stapelrahmen ist.  
  
 JustMyCode  
 Das Konzept des Debuggen von Code, der ein Benutzer angehört, und wird ignoriert, alle temporären Code z. B. Systemcode – selbst wenn der Quellcode für diesen Systemcode verfügbar ist.  
  
 ausstehender Haltepunkt  
 Stellt eine Abstraktion für Haltepunkte vor, während und nach dem Code wird geladen, und es wird eine Möglichkeit zum Virtualisieren des Breakpoints. Ein ausstehender Haltepunkt:  
  
-   Enthält alle Informationen, die erforderlich sind, um einen Haltepunkt für Code in einem oder mehreren Programmen zu binden.  
  
-   Kann an mehreren Standorten von Code in einem oder mehreren Programmen binden.  
  
-   Bindet niemals selbst Code.  
  
 Jedes Mal Code lädt, alle ausstehenden Haltepunkte in einem Programm werden überprüft, um festzustellen, ob sie gebunden werden können. Ein ausstehender Haltepunkt gibt alle gebundenen Breakpoints enthalten, die er gebunden.  
  
 process  
 Ein physisches Win32-Prozess. Ein Prozess kann mehrere Programme enthalten. Siehe auch *Programm*.  
  
 Programm  
 Ein einzelner Namespace innerhalb einer bestimmten-Laufzeit-Architektur ausgeführt wird. Siehe auch *Prozess*.  
  
 Sitzungs-Debug-Manager (SDM)  
 Verwaltet eine beliebige Anzahl von Debugmodule Debuggen eine beliebige Anzahl von Programmen in mehreren Prozessen in einer beliebigen Anzahl von Computern an. Auf der grundlegenden Ebene wird die SDM Vereinheitlichung der Debugmodule. Darüber hinaus bietet das SDM einen schnellen Überblick über die Debugsitzung der IDE an.  
  
 Stapelrahmen  
 Stellt den Status der Berechnung auf einen bestimmten Rahmen und Maß verschachtelten Funktionsaufrufe dar.  
  
 Thread  
 Das generalisierte Konzept der Anweisung stapelbasierten Ausführung in mindestens ein Programm ausgeführt wird.  
  
 Warnung-Haltepunkt  
 Eine Abstraktion zum Beschreiben der in ein ausstehender Haltepunkt einer Warnung. Ein Haltepunkt für die Warnung beschreibt einen Grund, warum ausstehende Haltepunkt noch nicht an einen Speicherort gebunden wurde. Dies kann sein, dass der Code für den Speicherort von ausstehenden Haltepunkts beschrieben wird, oder einem anderen Grund nicht noch geladen wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio Debugger-Erweiterbarkeit](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)